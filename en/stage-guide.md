## Dev Tools > Pipeline > Stage Guide

This guide describes the basics of stages in Pipeline. 
Click **Pipeline Management** > **+Create Pipeline** to create a pipeline. After selecting the pipeline you created, you can add a stage by clicking **+Add Stage** in the **Stage** tab at the bottom.

![stage-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-01.png)

Stages are divided into the following groups.

- **Source**
- **Build**
- **Deployment**
- **Feature**

### Source
This is a stage that gets the source code to build.

#### Source - GitHub
You can select the [source repository](/Dev%20Tools/Pipeline/en/environment-config/#source-repository) that you added in **Source Repository Settings** of **Environment Settings**.

![stage-guide-02](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-02.png)

#### Source - GitLab
You can select the [source repository](/Dev%20Tools/Pipeline/en/environment-config/#source-repository) that you added in **Source Repository Settings** of **Environment Settings**.

![stage-guide-03](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-03.png)

### Build
This is a stage to build

#### Build - Jenkins
You can build using Jenkins that you configured yourself. You can select the [build tool](/Dev%20Tools/Pipeline/en/environment-config/#build-tool) you added in **Build Tool Settings** of **Environment Settings**. You can select **Build Job** and enter **Build Job Parameters**.
You can set **Start Condition** and **End Condition** of the **artifact**. You can decide whether or not to start a stage by setting the **Start Condition**. You can set an **End Condition** to set stage output as an artifact.

![stage-guide-04](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-01.png)
![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-04.png)

#### Build - NHN Cloud Build Tool
You can use the build tools provided by NHN Cloud.

- Build Environment Settings
    - You can select the [image registry](/Dev%20Tools/Pipeline/en/environment-config/#image-registry) you added in the **Image Registry Settings** in **Environment Settings**.
    - Select the **Image Name** of the environment to build, set the **Build Tool Performance**, **Build Time Limit (minutes),** and **Build Command**.
  
- Build Result Settings
    - Set the **Dockerfile Path** of the build result, and the **Dockerfile Execution Path**.
    - Select a **Image Registry** and decide on **Image Name**, and the build result is pushed to the selected repository.
    - If **Use Tag Format** is selected, the tag format is fixed, and the image is created with dynamically generated tags in the form of `_{BUILD_NUMBER}`.

- Artifact Settings
    - You can decide whether to start stages by setting **Start Condtion**.
    - You can set stage output as an artifact by setting **End Condition**.
  
![stage-guide-05](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-02.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-02.png)

#### Build - NHN Cloud Build Tool v2
You can use the build tools provided by NHN Cloud.

- Build Environment Settings
    - You can set the performance and timeout of the build tools.
- Source Build Settings
    - You can select the [image registry](/Dev%20Tools/Pipeline/en/environment-config/#_3) you added in the **Image Registry Settings** in **Environment Settings**.
    - Enter the **image name** and **tag**for the environment you want to build, and set the **build command**.

- Docker Image Build Settings
    - For **Dockerfile path**, enter the path where the dockefile exists.
    - For **Dockerfile execution path**, enter the path to use for building the Dockerfile.
    - Select a **Image Registry** and decide on **Image Name**, and the build result is pushed to the selected repository.
    - **In Tags**, enter tags for the image. If you include the tag format, the tag format area entered will be dynamically replaced.

- Artifact Settings
    - Set **Start Condition** to determine whether to start stages.
    - Set **End Condition** to set stage products as artifacts.


|Image tag format | Replaced format | Description                                 |
| ----------- | ---------- |------------------------------------|
|{BUILD_DATE_TIME}| yyyy-MM-dd_HH_mm_ss| This is replaced by the build execution time in the form of year-month-day-hour-minute-second. |

![stage-guide-21.png](http://static.toastoven.net/prod_pipeline/2024-02-27/stage-guide-21.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-02.png)

#### Build - Bake (Manifest)
You can build using a Helm package file or [Chart Repository](/Dev%20Tools/Pipeline/en/environment-config/#chart-repository)that users configured themselves.

- Set the chart name as the name of the output configured with the Helm engine.
- Set the namespace as the namespace of the output configured with the Helm engine.
- Template
    - For repository type, select a repository that is added in [Source Repository Settings](/Dev%20Tools/Pipeline/en/environment-config/#source-repository) or [Chart Repository Settings](/Dev%20Tools/Pipeline/en/environment-config/#chart-repository) of **Environment Settings**.
    - When you set a repository type as **GitHub file** or **GitLab file**.
        - Enter the Helm package file path for the path.
        - Enter the branch of GitHub or GitLab for the branch name.
    - When you specify **Helm Chart** for the repository type
        - For the chart repository name, you can select one of repositories set in[Chart Repository Settings](/Dev%20Tools/Pipeline/en/environment-config/#chart-repository).
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

![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-12.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-13.png)

### Deployment
This is a stage to deploy to the Kubernetes environment.

#### Deployment - Deploy

- You can select the [deployment target](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**. 
Enter **Stage Name**, **Deployment Target**, and **Manifest** to use for deployment. 
If the tag format is used in the build stage, when the docker image tag of **Manifest** is entered as `_{BUILD_NUMBER}`, you can deploy as the image with the most recent number among the images built in the tag format.
See the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/controllers/deployment ) for how to write **Manifest**.
- You can select **Manifest Source** as artifacts. The selected artifact must be created in Manifest format.
    - You can select an artifact created in the pipeline.
    - You can select a specific file from the repository as an artifact. 
- You can set the **Start Condition** and **End Condition** of ** Artifact**. You can set a start condition to determine whether to start stages. You can set **End Condition** to set stage products as artifacts.


![stage-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-06.png)
![stage-guide-15](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-15.png)
![stage-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-16.png)
![stage-guide-14](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-05.png)

#### Deployment - Patch
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

![stage-guide-07](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-07.png)
![stage-guide-07-2](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-07-2.png)

#### Deployment - Scale
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

![stage-guide-08](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-08.png)
![stage-guide-08-2](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-08-2.png)

#### Deployment - Rollout Undo
You can select the [deployment target](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**. 
Enter **Namespace**, **Resource Type**, **Resource Name**, **Revision Back**. You can roll back to the specified Revision.

![stage-guide-09](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-09.png)

#### Deployment - Delete
- You can select the [deployment target\](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
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

![stage-guide-10](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-10.png)
![stage-guide-10-2](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-10-2.png)

#### Deployment - Disable
- You can select the [deployment target\](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
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

![stage-guide-23.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-23.png)
![stage-guide-24.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-24.png)

#### Deployment - Enable
- You can select the [deployment target\](/Dev%20Tools/Pipeline/en/environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
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

![stage-guide-25.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-25.png)
![stage-guide-26.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-26.png)

#### Deployment - NHN Container Service
The stage where you can replace the template of an NCS workload.  
Entering the **NCS app key** retrieves a list of **NCS roles**, templates, and workloads.  
You can select the template you want to change from the list.  
You can select a workload from the list for which you want to change the template.

![stage-guide-22.png](http://static.toastoven.net/prod_pipeline/2024-03-26/stage-guide-22.png)

### Feature
This is a stage to provide additional features.

#### Feature - Webhook
Enter the HTTP method and URL in **URL**. You can add **Request Header** and **Request Data** as needed. 
If the response value of the webhook is one of the values entered in **Fail Fast HTTP Status Code**, close the stage immediately.

![stage-guide-11](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-11.png)

#### Feature - Judgement (Run Management)
You can fill in **Description** and **Run Settings** for the Judgement stage when necessary.

![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-12.png)

You can **Manage Run (run, stop running)** for the next stage with or without the **Run Settings**.
If you add **Run Settings** and select run for the next stage, you can pass the settings to Precondition(Run Condition), the stage to be described, for branching processing.

![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-13.png)

#### Feature - Precondition (Run Condition)
Decide whether to run subsequent stages based on the **Run Condition** of the values passed from the Judgement stage set as the previous stage.
Decide whether run subsequent stages by selecting either **Condition Matched or Condition Unmatched** for values from **Run Condition** and setting values passed from the Judgement (Run Management).

![stage-guide-14](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-14.png)

#### Features - Precondition (Stage Status Condition)
You can set conditions by selecting the stage name and execution result of the previous stage.
The next stage runs only if all the conditions you specify are met.

![stage-guide-28](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-28.png)

#### Feature - Run the Pipeline
Run entire other pipelines.
Select a **pipeline name** to run.

![stage-guide-28](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-28.png)

#### Feature - Run Other Pipelines
You can run entire other pipelines on a stage.
Select the **pipeline name** you want to run.
![stage-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/stage-guide-15.png)

If you uncheck **Run Condition**, the next stage runs without waiting for the execution status of the selected pipeline.

![stage-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/stage-guide-16.png)

#### Feature - Approval Management
Approvers can manage **Run Management (run, stop running)** for stages after **Feature - Approval Management**.

![stage-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-17.png)

You can write requests in stages, and only users with the **Pipeline APPROVAL ADMIN** role can perform the **Run Management (run, stop running)** feature from the approval management stage. 

The **Pipeline APPROVAL ADMIN** role can be granted from the project's Member Management, Role Group Management.

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-18.png)

#### Feature - Run NHN Cloud Deploy Service Deployment
You can run the deployment using the NHN Cloud Deploy service on the stage.

- If the **command type**of the artifact you want to run the deployment on is **SSH**, the **Run NHN Cloud Deploy Service Deployment** is not supported, only **Cloud Agent** is supported. For more information, refer to the [Deploy User Guide](/Dev%20Tools/Deploy/en/console-guide/#_8).

![stage-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/stage-guide-19.png)

In **Environment Settings** > **NHN Cloud Security Settings**, select the security settings you added, and in **AppKey**, enter the appkey that will use the NHN Cloud Deploy service.

After entering the information, click **Search**to get deployment-related information from NHN Cloud Deploy that matches your security settings and Appkey.

You can then select **artifacts**, **server groups**, and **scenarios**to deploy through the NHN Cloud Deploy service.


For **Deployment restriction time**, specify how long the stage will wait to complete execution (minimum 1 minute, maximum 600 minutes).

![stage-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/stage-guide-20.png)

For **Deployment Settings Details**, you can add conditions for what you want to deploy to.

In **Select Server**, you can choose which server to deploy to. If you select **All Servers**, the deployment will target all servers, and if you click **Select Server**, you can choose which servers to deploy to.

In **Number of concurrent server executions**, you can select how many servers the NHN Cloud Deploy service will run at the same time. (Default 1, maximum number of servers)

In **Deployment Note**, you can enter deployment execution information.

For more information, see the [Deploy User Guide](/Dev%20Tools/Deploy/en/reference/#_1).

### Stage Common Features
#### On stage failure

You can select settings related to pipeline execution when a stage fails.

![stage-guide-27](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-05-28/stage-guide-27.png)

- Terminate Entire Pipeline
    - If that stage fails, the entire pipeline terminates. 
- Terminate only that branch
    - Only the branch that the stage belongs to is terminated, and the pipeline on the other branches continues. 
- The branch is terminated, and other branches fail on termination
    - Only the branch that the stage belongs to is terminated, and pipelines on other branches continue. However, the result of that pipeline will remain a failure.
- Ignore the failure and proceed
    - If that stage fails, the next stage proceeds.