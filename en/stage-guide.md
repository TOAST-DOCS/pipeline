## Dev Tools > Pipeline > Stage Guide

This guide explains the basics of stages in Pipeline.

Stages can be added to the Pipeline Studio screen by clicking the **Edit Mode** toggle in the top right corner to enable edit mode, then clicking the
In the **Add Stage** panel on the left, click the tree menu to add exposed Stages by dragging and dropping them.

You can view or edit the details of a stage in the **Stage Settings** panel on the right.

![stage-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-01_new.png)

Stages are divided into the following groups.

- **Source**
- **Build**
- **Deployment**
- **Feature**

## Source
This is a stage that gets the source code to build.

### Source - GitHub
You can select [a source repository](/Dev%20Tools/Pipeline/en/environment-config/#_2) that you added in **Source Repository Settings** of **Environment Settings**. 

![stage-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-02_new.png)

### Source - GitLab
You can select [a source repository](/Dev%20Tools/Pipeline/en/environment-config/#_2) that you added in **Source Repository Settings** of **Environment Settings**.

![stage-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-03_new.png)

## Build
This is a stage to build

### Build - Jenkins
You can build using Jenkins with your own configuration. You can select [Build Tool](/Dev%20Tools/Pipeline/en/environment-config/#_4) you added in the **Build Tool Settings** in **Preferences**. You can select a **build job**.
You can set the **start condition** and **end condition****for the artifact**. You can set the **start condition** to determine whether the stage starts. You can set an **end condition** to set the stage's output as an artifact.

![stage-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-04_new.png)

### Build - Bake (Manifest)
You can build using a Helm package file or [Chart Repository](/Dev%20Tools/Pipeline/en/environment-config/#_6)that users configured themselves.

- Set the chart name as the name of the output configured with the Helm engine.
- Set the namespace as the namespace of the output configured with the Helm engine.
- Template
    - For repository type, select a repository that is added in [Source Repository Settings](/Dev%20Tools/Pipeline/en/environment-config/#_2) or [Chart Repository Settings](/Dev%20Tools/Pipeline/en/environment-config/#_6) of **Environment Settings**.
    - When you set a repository type as **GitHub file** or **GitLab file**.
        - Enter the Helm package file path for the path.
        - Enter the branch of GitHub or GitLab for the branch name.
    - When you specify **Helm Chart** for the repository type
        - For the chart repository name, you can select one of repositories set in [Chart Repository Settings](/Dev%20Tools/Pipeline/en/environment-config/#_6).
        - For the chart name, you can choose any chart name available in the chart repository's configuration.
        - For the chart version, you to select a chart version available in the chart repository's configuration.
- Override
    - Repository Information
        - You can select in the same way as for templates.
        - Create a build output using the template as default and replacing it with what you specify in the override.
    - Key / Value
        - Enter a value consisting of key and value, create a build result by replacing a specific value.
    - Replace Basic Type
        - If the option is checked, when adding the override value, --set is used instead of --set--string.
- Artifact
    - You can set the **Start Condition** and **End Condition** of ** Artifact**. You can set a start condition to determine whether to start stages. You can set **End Condition** to set stage products as artifacts.

![stage-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-10-29/stage-guide-05-1.png)

### Build - NHN Cloud Build Tool v2
You can use the build tools provided by NHN Cloud.

- Build Environment Settings
    - You can set the performance and timeout of the build tools.
- Source Build Settings
    - You can select the [image registry](/Dev%20Tools/Pipeline/en/environment-config/#_3) you added in the **Image Registry Settings** in **Environment Settings**.
      - Enter the **image name** and **tag**for the environment you want to build, and set the **build command**.

- Docker Image Build Settings
    - **For Dockerfile path**, enter the path where the dockefile exists.
    - **For Dockerfile execution path,** enter the path to use for building the Dockerfile.
    - Select a **Image Registry** and decide on **Image Name**, and the build result is pushed to the selected repository.
    - **In Tags**, enter tags for the image. If you include the tag format, the tag format area entered will be dynamically replaced.

- Artifact Settings
    - Set **Start Condition** to determine whether to start stages.
    - Set **End Condition** to set stage products as artifacts.


|Image tag format | Replaced format | Description                                 |
| ----------- | ---------- |------------------------------------|
|{BUILD_DATE_TIME}| yyyy-MM-dd_HH_mm_ss| This is replaced by the build execution time in the form of year-month-day-hour-minute-second. |

![stage-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-06_new.png)

## Deployment
This is a stage to deploy to the Kubernetes environment.

### Deployment - Deploy
- You can select the [deployment target](/Dev%20Tools/Pipeline/en/environment-config/#_5) you added in **Deployment Target Settings** in **Environment Settings**. 
Enter **Namespace**, **Resource Type**, **Resource Name**, and **Manifest** to use for deployment. 
If the tag format is used in the build stage, entering the Docker image tag part of **Manifest** as `_{BUILD_NUMBER}` allows you to deploy to the image with the most recent number among the images built in the tag format.
For more details on **Manifest**, see [Kubernetes documents](https://kubernetes.io/docs/concepts/workloads/controllers/deployment ).
- You can select **Manifest Source** as artifacts. The selected artifact must be created in Manifest format.
    - You can select an artifact created in the pipeline.
    - You can select a specific file from the repository as an artifact. 
- You can set the **Start Condition** and **End Condition** of ** Artifact**. You can set a start condition to determine whether to start stages. You can set **End Condition** to set stage products as artifacts.

![stage-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-07_new.png)

### Deployment - Patch
- You can select the [deployment target\](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
- Enter **Namespace**, **Resource Type**, **Resource Name**, and **Manifest** to use for deployment.You can modify the information of an existing resource with Patch.
- See the [Kubernetes documentation\](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources) for how to write **Manifest**.
- If you set the selection method to **Select by dynamic method**, enter a **cluster** and **selection strategy**.
- Cluster
    - For replicaSets, Pipeline internally versions and deploys them, and when you select a **Select by dynamic method**, it selects targets based on a selection strategy rather than selecting a specific version.
- Selection Strategy
    - Newest: Select the most recently deployed resource when the stage started.
    - Second Newest: Select the second most recently deployed resource when the stage started.
    - Oldest: Select the oldest resource when this stage started.
    - Largest: Select the resource with the largest number of Pods in the cluster when that stage started.
    - Smallest: Select the resource with the smallest number of Pods in the cluster when that stage is started.

![stage-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-08_new.png)

### Deployment - Scale
- You can select the [deployment target\](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
- Enter **Namespace**, **Resource Type**, Resource Name, and Replicas. Replicas can be modified with Scale.
- If you set the selection method to **Select by dynamic method**, enter a **cluster** and **selection strategy**.
- Cluster
    - For replicaSets, Pipeline internally versions and deploys them, and when you select a **Select by dynamic method**, it selects targets based on a selection strategy rather than selecting a specific version.
- Selection Strategy
    - Newest: Select the most recently deployed resource when the stage started.
    - Second Newest: Select the second most recently deployed resource when the stage started.
    - Oldest: Select the oldest resource when this stage started.
    - Largest: Select the resource with the largest number of Pods in the cluster when that stage started.
    - Smallest: Select the resource with the smallest number of Pods in the cluster when that stage is started.

![stage-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-09_new.png)

### Deployment - Rollout Undo
You can select the [deployment target](/Dev%20Tools/Pipeline/en/environment-config/#_5) you added in **Deployment Target Settings** in **Environment Settings**. Enter **Namespace**, **Resource Type**, **Resource Name**, **Revision Back**. You can roll back to the specified Revision.

![stage-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-10_new.png)

### Deployment - Delete
- You can select the [deployment target](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
- Enter the **Namespace**, **resource type**, **selection method**, and **resource name**. You can delete the resource.
- If you set the selection method to **Select by dynamic method**, enter a **cluster** and **selection strategy**.
- Cluster
    - For replicaSets, Pipeline internally versions and deploys them, and when you select a **Select by dynamic method**, it selects targets based on a selection strategy rather than selecting a specific version.
- Selection Strategy
    - Newest: Select the most recently deployed resource when the stage started.
    - Second Newest: Select the second most recently deployed resource when the stage started.
    - Oldest: Select the oldest resource when this stage started.
    - Largest: Select the resource with the largest number of Pods in the cluster when that stage started.
    - Smallest: Select the resource with the smallest number of Pods in the cluster when that stage is started.

![stage-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-11_new.png)

### Deployment - NHN Container Service
The stage where you can replace the template of an NCS workload.  
Entering the **NCS app key** retrieves a list of **NCS roles**, templates, and workloads.  
You can select the template you want to change from the list.  
You can select a workload from the list for which you want to change the template.

![stage-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-12_new.png)


### Deployment - Enable
- You can select the [deployment target](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
- Enter the **Namespace**, **resource type**, **selection method**, and **resource name**. You can enable the resource.
    - Enabled: The resource is managed by Pipeline and is enabled to send traffic to the resource.
- If you set the selection method to **Select by dynamic method**, enter a **cluster** and **selection strategy**.
    - Cluster
        - For replicaSets, Pipeline internally versions and deploys them, and when you select a **Select by dynamic method**, it selects targets based on a selection strategy rather than selecting a specific version.
    - Selection Strategy
        - Newest: Select the most recently deployed resource when the stage started.
        - Second Newest: Select the second most recently deployed resource when the stage started.
        - Oldest: Select the oldest resource when this stage started.
        - Largest: Select the resource with the largest number of Pods in the cluster when that stage started.
        - Smallest: Select the resource with the smallest number of Pods in the cluster when that stage is started.

![stage-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-13_new.png)

### Deployment - Disable
- You can select the [deployment target](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
- Enter the **Namespace**, **resource type**, **selection method**, and **resource name**. You can disable the resource.
    - Disable: Doesn't delete the resource, but no longer sends traffic to it.
- If you set the selection method to **Select by dynamic method**, enter a **cluster** and **selection strategy**.
    - Cluster
        - For replicaSets, Pipeline internally versions and deploys them, and when you select a **Select by dynamic method**, it selects targets based on a selection strategy rather than selecting a specific version.
    - Selection Strategy
        - Newest: Select the most recently deployed resource when the stage started.
        - Second Newest: Select the second most recently deployed resource when the stage started.
        - Oldest: Select the oldest resource when this stage started.
        - Largest: Select the resource with the largest number of Pods in the cluster when that stage started.
        - Smallest: Select the resource with the smallest number of Pods in the cluster when that stage is started.

![stage-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-14_new.png)

## Feature
This is a stage to provide additional features.

### Features - Approval Management
**Feature - Approval Management** Allows approvers to manage **execution management (run, stop)** for stages after the stage.

You can write about requests in the stage, and the ability to manage the **execution** (run, stop) of an approval management stage can only be done by a user with the **Pipeline APPROVAL** ADMIN role for that **project**.

![stage-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-15_new.png)

The **Pipeline APPROVAL ADMIN** role can be granted from Manage members, Manage role groups in a project.

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-18.png)

### Feature - Judgement (Run Management)
You can fill in **Description** and **Run Settings** for the Judgement stage when necessary.

You can **Manage Run** (run, stop running) for the next stage with or without the **Run Settings**.
If you add **Run Settings** and select run for the next stage, you can pass the settings to Precondition(Run Condition), the stage to be described, for branching processing.

![stage-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-16_new.png)

### Features - Precondition (Stage Status Condition)
You can set conditions by selecting the stage name and execution result of the previous stage.
The next stage runs only if all the conditions you specify are met.

![stage-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-17_new.png)

### Feature - Precondition (Run Condition)
Decide whether to run subsequent stages based on the **Run Condition** of the values passed from the Judgment stage set as the previous stage.
Decide whether run subsequent stages by selecting either **Condition Matched or Condition Unmatched** for values from **Run Condition** and setting values passed from the Judgement (Run Management).

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-18_new.png)

### Feature - Webhook
Enter the HTTP method and URL in **URL**. You can add **Request Header** and **Request Data** as needed. If the response value of the webhook is one of the values entered in **Fail Fast HTTP Status Code**, close the stage immediately.

![stage-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-19_new.png)

### Feature - Run Other Pipelines
You can run entire other pipelines on a stage.
Select the **pipeline name** you want to run.

If you uncheck the **execution condition**, the next stage runs without waiting for the selected pipeline's execution status.

![stage-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-20_new.png)

### Feature - Run NHN Cloud Deploy Service Deployment
You can run the deployment using the NHN Cloud Deploy service on the stage.
- If the **command type**of the artifact you want to run the deployment on is **SSH**, the **Run NHN Cloud Deploy Service Deployment** is not supported, only **Cloud Agenet** is supported. For more information, refer to the [Deploy User Guide](/Dev%20Tools/Deploy/en/console-guide/#_8).

In **Environment Settings** > **NHN Cloud Security Settings**, select the security settings you added, and in **AppKey**, enter the appkey that will use the NHN Cloud Deploy service.

After entering the information, click **Confirm** to get deployment-related information from NHN Cloud Deploy that matches your security settings and Appkey.

You can then select **artifacts**, **server groups**, and **scenarios**to deploy through the NHN Cloud Deploy service.


For **Deployment restriction time**, specify how long the stage will wait to complete execution (minimum 1 minute, maximum 600 minutes).

For **Deployment Settings Details**, you can add conditions for what you want to deploy to.

In **Select Server**, you can choose which server to deploy to. If you select **All Servers**, the deployment will target all servers, and if you click **Select Server**, you can choose which servers to deploy to.

In **Number of concurrent server executions**, you can select how many servers the NHN Cloud Deploy service will run at the same time. (Default 1, maximum number of servers)

In **Deployment Note**, you can enter deployment execution information.

For more information, see the [Deploy User Guide](/Dev%20Tools/Deploy/en/reference/#_1).

![stage-guide-21](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-21_new.png)

## Stage Common Features
### On stage failure

You can select settings related to pipeline execution when a stage fails.

- Terminate Entire Pipeline
    - If that stage fails, the entire pipeline terminates. 
- Terminate only that branch
    - Only the branch that the stage belongs to is terminated, and the pipeline on the other branches continues. 
- The branch is terminated, and other branches fail on termination
    - Only the branch that the stage belongs to is terminated, and pipelines on other branches continue. However, the result of that pipeline will remain a failure.
- Ignore the failure and proceed
    - If that stage fails, the next stage proceeds.

![stage-guide-27](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-05-28/stage-guide-27.png)
