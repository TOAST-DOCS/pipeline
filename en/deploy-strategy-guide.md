## Dev Tools > Pipeline > Deployment Strategy Guide

The Deployment strategy guide explains how to combine the stages in Pipeline to perform different deployment strategies.

## Blue/Green Deployment

![deploy-strategy-guide-11.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-11.png)

A Blue/Green deployment is a deployment strategy that creates two identical environments. One environment (Blue) runs the current application version, and the other environment (Green) runs the new application version.
You can use a Blue/Green deployment strategy to reduce deployment risk by increasing application availability and simplifying the rollback process in the event of a deployment failure. When testing is complete in the Green environment, application traffic is moved to the Green environment, and the Blue environment is decommissioned.

### Use ReplicaSets

- Pipeline uses labels to manage traffic, and you need to modify the labels of running resources.
Since modifying the Deployment Object triggers the rollout, the only way to do a Blue/Green deployment without modifying the Service Object is to use **ReplicaSets**.
- When Pipeline deploys ReplicaSets, it deploys new ReplicaSets with the `-vNNN` suffix. You must also include `strategy.` `spinnaker`. `io/max-version-history`, `traffic.spinnaker.io/load-balancers`among the annotations in the ReplicaSets.
    - `strategy.spinnaker.io/max-version-history`: Specifies the maximum number of ReplicaSets that Pipeline maintains. You must give a value of 2 or higher to enable blue/green deployments.
    - `traffic.spinnaker.io/load-balancers`: Specify the Service Object. Pipeline will modify the Pod's label to match the Service's Selector, enabling traffic to be delivered to your application. The Service Object you specify must have been created through Pipeline.

### How to configure a Blue/Green Pipeline

Here's how to configure a pipeline that can do blue/green deployments.
You can configure a pipeline by referring to the[Pipeline template guide](/Dev%20Tools/Pipeline/en/template-guide/).

#### 1. Create a Service

Deploy **-**Add a **Deploy stage**and use the Pipeline to create the Service. Since you typically don't modify the Service when deploying an application, create a different pipeline than the application deployment pipeline to pre-create just the Service.

![deploy-strategy-guide-01.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-01.png)

- Deploy - Deploy stage
    - An example of a service manifest is shown below. You can modify the metadata, spec, etc. to suit your environment.

``` yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
  namespace: blue-green
spec:
  selector:
    frontedBy: my-service
  ports:
  - protocol: TCP
    port: 80
```

![deploy-strategy-guide-02.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-02.png)

#### 2. Configure the Application Deployment Pipeline

Organize your pipeline in the following order: **Deploy - Deploy stage** **> Deploy - Disable Stage**. Configure the **Deploy - Deploy Stage** to deploy a new version of the application and the **Deploy - Disable stage** to select an older version of the application.
![deploy-strategy-guide-03.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-03.png)

- Deploy - Deploy stage
    - An example ReplicaSet manifest is shown below, where `strategy.` `spinnaker`. `io/max-version-history`in the annotations must have a value of 2 or greater, and `traffic.spinnaker.io/load-balancers`specifies the name of the Service created above.

      Other metadata, specs, etc. can be modified to suit your environment.

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  annotations:
    strategy.spinnaker.io/max-version-history: "2"
    traffic.spinnaker.io/load-balancers: '["service my-service"]'
  labels:
    app: myapp
  name: myapp-frontend
  namespace: blue-green
spec:
  replicas: 4
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - image: nginx:stable-alpine3.17-slim
        name: frontend
```
    
![deploy-strategy-guide-04.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-04.png)

- Deployment - Disable Stage
    - Select an obsolete application after deployment. The Deploy **\- Disable stage** doesn't delete the resource, it just **disables** it so that traffic is no longer sent to it.
If you want to delete the resource, utilize the Deploy **\- Delete stage**.
    - Selection Strategy
        - Newest: Select the most recently deployed resource when the stage started.
        - Second Newest: Select the second most recently deployed resource when the stage started.
        - Oldest: Select the oldest resource when this stage started.
        - Largest: Select the resource with the largest number of Pods in the cluster when that stage started.
        - Smallest: Select the resource with the smallest number of Pods in the cluster when that stage is started.
      
![deploy-strategy-guide-05.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-05.png)

