## Dev Tools > Pipeline > Console User Guide > Deploy Target Management

### Deploy Target Management

You can identify output created by deploying with Pipeline in the **Deploy Target Management** menu.

## Deployment Target

Go to **Deploy Target Management > Deployment Target** to identify workloads deployed to Kubernetes by using Pipeline.
![deploy-target-monitoring-guide-01.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-01.png)
You can find all workloads deployed, workload names, pod count, and status.
Enter a search term and click the search button, search for deployment targets with the entered string starts.
Click **Deployment Target Name** in the Deployment Target table to go to a page where you can see the workloads that belong to the selected deployment target.

![deploy-target-monitoring-guide-02.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-02.png)
Displays the namespaces of workloads deployed with Pipeline among the namespaces of the selected deployment target cluster.
Enter a search term and click the search button to search the namespace with the entered string.
Select a namespace to display a list of workloads that belong to the selected namespace.

![deploy-target-monitoring-guide-09.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-09.png)
Displays the number of pods in the workload and which pods are currently running in %. When you select a workload, a list of the pods in the selected workload appears, and their operational status is indicated by the color of the dot on the left.
You can find basic information about the selected workload and pods on the right.


Pod status in the left dot

| Color | Status   |
| --- |------|
| Green | Running |
| Red | Suspended   |



![deploy-target-monitoring-guide-10.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-10.png)
Select a pod to view the console log and the information of the connected service.
For the pod associated with the service, the load balancer icon appears on the right. Select the load balancer icon to go to the **Network** tab.

To see the workloads associated with the service in **Deploy Target Management**, you need to add the 'traffic.spinnaker.io/load-balancers' annotation to the manifest rather than specifying a selector.

![deploy-target-monitoring-guide-08.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-08.png)

Click the **Workload Management** to show a list of possible management tasks based on the selected workload. All tasks are actually applied to the cluster where the workload is running.
![](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-11.png)deploy-target-monitoring-guide-11.png![](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-11.png)

Check the executed tasks in the **Management History** tab.
The **management history** is saved by namespace and workload name, and only the most recent 10 cases are displayed. If you delete a task, the workload is also deleted so you cannot check the deleted history.


 ![deploy-target-monitoring-guide-12.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-12.png)

Management Task Types

| Management Task    | Description                      | Available Workload |
|----------|-------------------------| --- |
| Modify       | Modify and apply the manifest of workload | All workloads |
| Delete       | Delete workload from cluster         | All workloads |
| Activate Service   | Connect workload and service           | Replica set|
| Deactivate Service  | Disconnect workload and service        | Replica set|
| Scale in/out | Adjust the number of pods in workload           | Deployment, replica set, stateful set|
| Rollback       | Roll back to a previous version of the workload        | Deployment|
| Restart Pod   | Restart pods in workload          | Deployment |
| Pause Deployment | Rollback, pause of pod restart    | Deployment |
| Restart Deployment   | Restart a paused deployment          | Deployment |

## Network

You can identify a service deployed to Kubernetes by using Pipeline in **Deploy Target Management > Network**.

![deploy-target-monitoring-guide-05.png]( http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-05.png)
You can see all the services you've deployed, along with the number and status of pods connected to them.
Enter a search term and click the Search button to search for a deployment target with the string you entered.
Click the **Deployment Target Name** in the Deployment Target table to go to the namespace selection page.

![deploy-target-monitoring-guide-06.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-06.png)

Displays the namespaces of services deployed with Pipeline among the namespaces of the selected deployment target cluster.
Enter a search term and click the search button to search the namespace with the entered string.
Select a namespace to display services that belong to the selected namespace.

![deploy-target-monitoring-guide-07.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-07.png)

Select a service to display workloads that belong to the service. When you select a workload, the information for the selected workload appears on the right in the **Deployment Target** tab. 
