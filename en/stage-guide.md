<!-- machine_translated: true -->

<!-- pre-align:aligned sig=093d50d32d45 -->

<a id="dev-tools-pipeline-stage-guide"></a>
## Dev Tools > Pipeline > Stage Guide { #dev-tools-pipeline-stage-guide }

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

<a id="source"></a>
## Source { #source }

This is a stage that gets the source code to build.

<a id="source---github"></a>
### Source - GitHub { #source---github }

You can select [a source repository](/Dev%20Tools/Pipeline/en/environment-config/#_2) that you added in **Source Repository Settings** of **Environment Settings**. 

![stage-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-02_new.png)

<a id="source---gitlab"></a>
### Source - GitLab { #source---gitlab }

You can select [a source repository](/Dev%20Tools/Pipeline/en/environment-config/#_2) that you added in **Source Repository Settings** of **Environment Settings**.

![stage-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-03_new.png)

<a id="build"></a>
## Build { #build }

This is a stage to build

<a id="build---jenkins"></a>
### Build - Jenkins { #build---jenkins }

You can build using Jenkins with your own configuration. You can select [Build Tool](./environment-config/#build-tool) you added in the **Build Tool Settings** in **Preferences**. You can select a **build job**.
You can set the **start condition** and **end condition****for the artifact**. You can set the **start condition** to determine whether the stage starts. You can set an **end condition** to set the stage's output as an artifact.

![stage-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-04_new.png)

<a id="build---bake-manifest"></a>
### Build - Bake (Manifest) { #build---bake-manifest }

You can build using a Helm package file or [Chart Repository](./environment-config/#chart-repository)that users configured themselves.

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

<a id="build---nhn-cloud-build-tool-v2"></a>
### Build - NHN Cloud Build Tool v2 { #build---nhn-cloud-build-tool-v2 }

You can use the build tools provided by NHN Cloud.

- Build Environment Settings
    - You can set the performance and timeout of the build tools.
- Source Build Settings
    - You can select the [image registry](./environment-config/#image-registry) you added in the **Image Registry Settings** in **Environment Settings**.
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

<a id="deployment"></a>
## Deployment { #deployment }

This is a stage to deploy to the Kubernetes environment.

<a id="deployment---deploy"></a>
### Deployment - Deploy { #deployment---deploy }

- You can select the [deployment target](./environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**. Enter **Stage Name**, **Deployment Target**, and **Manifest** to use for deployment. If the tag format is used in the build stage, entering the Docker image tag part of **Manifest** as `_{BUILD_NUMBER}` allows you to deploy to the image with the most recent number among the images built in the tag format. For more information on how to write a **Manifest**, see the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/controllers/deployment ).
- You can select **Manifest Source** as artifacts. The selected artifact must be created in Manifest format.
    - You can select an artifact created in the pipeline.
    - You can select a specific file from a repository as an artifact.
- You can set the **start condition** and **end condition** of the **Artifact**. You can set the **start condition** to determine whether the stage starts. You can set an **end condition** to set the stage's output as an artifact.
- You can configure **Use Resource Versioning**. This is the default behavior of the Pipeline service, and we recommend that you enable it. For more information, see **Resource Versioning** below.

![stage-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-09-15/pipeline-stage-guide/deploy-stage-normal.png)

<a id="deployment---deploy-resource-versioning"></a>
#### Resource Versioning

When deploying ConfigMap and Secret resources, the Pipeline service provides a resource versioning feature that creates new resources with a version suffix (-v000, -v001, ...) appended to the name and automatically updates the parts of workloads in the same deployment that reference those resources (`volume`, `env`, `envFrom`, etc.) to use the versioned name.
This feature preserves the configuration change history by version and allows you to revert to a previous configuration along with the workload during a rollback.

If you disable **Use Resource Versioning** in the **Deployment - Deploy** stage, the resources deployed by that stage are deployed with their original names as defined in the manifest, and the resource versioning feature of the Pipeline service becomes unavailable.
We recommend disabling it only when operators, controllers, or other components outside the deployment manifest need to look up resources directly by their original names.

![stage-guide-07-1](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2026-09-15/pipeline-stage-guide/deploy-stage-version.png)

The resource versioning option applies to all resources deployed by that stage.
To configure specific resources differently, you can add the `strategy.spinnaker.io/versioned` annotation with a value of "`true`" or "`false`" to `metadata.annotations` in the manifest to configure versioning on a per-resource basis.
Resource versioning is determined by the following order of precedence:

1. The `strategy.spinnaker.io/versioned` annotation on the resource
2. The **Use Resource Versioning** setting in the Deploy stage

**Constraints**
* Resources with versioning disabled do not retain version history, so the rollback feature of the **Deployment - Rollout undo** stage and the **Deployment Target Management** workload cannot be used. Even if you perform a rollback, the previous ConfigMap and Secret configurations are not restored.
* Resources that were already deployed with a versioned name (-vNNN) are not automatically cleaned up and must be deleted manually.

<a id="deployment---patch"></a>
### Deployment - Patch { #deployment---patch }

- You can select the [deployment target](./environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
- Enter **Namespace**, **Resource Type**, **Selection Method**, **Resource Name**, and **Manifest** to use for deployment. You can modify the information of an existing resource with Patch.
- See the [Kubernetes documentation](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources) for how to write **Manifest**.
- If you set **Selection Method** to **Dynamic selection**, enter the **Cluster** and **Selection Strategy**.
- Cluster
    - For replicaSets, Pipeline internally versions and deploys them, and when you select **Dynamic selection**, it selects targets based on a selection strategy rather than selecting a specific version.
- Selection Strategy
    - Newest: Select the most recently deployed resource when the stage started.
    - Second Newest: Select the second most recently deployed resource when the stage started.
    - Oldest: Select the oldest resource when the stage started.
    - Largest: Select the resource with the largest number of Pods in the cluster when that stage started.
    - Smallest: Select the resource with the smallest number of Pods in the cluster when that stage is started.

![stage-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-08_new.png)

<a id="deployment---scale"></a>
### Deployment - Scale { #deployment---scale }

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

<a id="deployment---rollout-undo"></a>
### Deployment - Rollout Undo { #deployment---rollout-undo }

You can select the [deployment target](./environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**. Enter **Namespace**, **Resource Type**, **Resource Name**, **Revision Back**. You can roll back to the specified Revision.

![stage-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-10_new.png)

<a id="deployment---delete"></a>
### Deployment - Delete { #deployment---delete }

- You can select the [deployment target](./environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
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

<a id="deployment---nhn-container-service-ncs"></a>
### Deployment - NHN Container Service (NCS) { #deployment---nhn-container-service-ncs }

The stage where you can replace the template of an NCS workload.  
Entering the **NCS app key** retrieves a list of **NCS roles**, templates, and workloads.  
You can select the template you want to change from the list.  
You can select a workload from the list for which you want to change the template.

![stage-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-12_new.png)


<a id="deployment---enable"></a>
### Deployment - Enable { #deployment---enable }

- You can select the [deployment target](./environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
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

<a id="deployment---disable"></a>
### Deployment - Disable { #deployment---disable }

- You can select the [deployment target](./environment-config/#deployment-target) you added in **Deployment Target Settings** in **Environment Settings**.
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

<a id="feature"></a>
## Feature { #feature }

This is a stage to provide additional features.

<a id="features---approval-management"></a>
### Features - Approval Management { #features---approval-management }

**Feature - Approval Management** Allows approvers to manage **execution management (run, stop)** for stages after the stage.

You can write about requests in the stage, and the ability to manage the **execution** (run, stop) of an approval management stage can only be done by a user with the **Pipeline APPROVAL** ADMIN role for that **project**.

![stage-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-15_new.png)

The **Pipeline APPROVAL ADMIN** role can be granted from Manage members, Manage role groups in a project.

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-18.png)

<a id="feature---judgement-run-management"></a>
### Feature - Judgement (Run Management) { #feature---judgement-run-management }

You can fill in **Description** and **Run Settings** for the Judgement stage when necessary.

You can **Manage Run** (run, stop running) for the next stage with or without the **Run Settings**.
If you add **Run Settings** and select run for the next stage, you can pass the settings to Precondition(Run Condition), the stage to be described, for branching processing.

![stage-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-16_new.png)

<a id="features---precondition-stage-status-condition"></a>
### Features - Precondition (Stage Status Condition) { #features---precondition-stage-status-condition }

You can set conditions by selecting the stage name and execution result of the previous stage.
The next stage runs only if all the conditions you specify are met.

![stage-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-17_new.png)

<a id="feature---precondition-run-condition"></a>
### Feature - Precondition (Run Condition) { #feature---precondition-run-condition }

Decide whether to run subsequent stages based on the **Run Condition** of the values passed from the Judgment stage set as the previous stage.
Decide whether run subsequent stages by selecting either **Condition Matched or Condition Unmatched** for values from **Run Condition** and setting values passed from the Judgement (Run Management).

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-18_new.png)

<a id="feature---webhook"></a>
### Feature - Webhook { #feature---webhook }

Enter the HTTP method and URL in **URL**. You can add **Request Header** and **Request Data** as needed. If the response value of the webhook is one of the values entered in **Fail Fast HTTP Status Code**, close the stage immediately.

![stage-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-19_new.png)

<a id="feature---run-other-pipelines"></a>
### Feature - Run Other Pipelines { #feature---run-other-pipelines }

You can run entire other pipelines on a stage.
Select the **pipeline name** you want to run.

If you uncheck the **execution condition**, the next stage runs without waiting for the selected pipeline's execution status.

![stage-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-20_new.png)

<a id="feature---run-nhn-cloud-deploy-service-deployment"></a>
### Feature - Run NHN Cloud Deploy Service Deployment { #feature---run-nhn-cloud-deploy-service-deployment }

You can run the deployment using the NHN Cloud Deploy service on the stage.
- If the **Command Type** of the artifact you want to run the deployment on is **SSH**, the **Run NHN Cloud Deploy Service Deployment** feature is not supported; it is supported only when the Command Type is **Cloud Agent**. For more information, see [Deploy User Guide](/Dev%20Tools/Deploy/en/console-guide/#_8).

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

<a id="features---providing-user-variables"></a>
### Features - Providing User Variables { #features---providing-user-variables }

Define variables to be reused in subsequent stages within the pipeline. Variables created in this stage are available to all subsequent stages connected to it, and up to five variables can be created.

**How to Use Variables**

- Referenced by pipeline expression.
- (example) If a variable name is myImage:

```
${myImage}
```
> In actual use, replace the variable name with the value specified in the stage. (example: `${buildTag}`, `${buildImage}`)

**Description and Examples by Variable Type**

| Variable Type                 | Description                                                                                                                         | Example                                                                                                                                                                                       |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorun image info          | When a pipeline is auto-run with the **Image Registry** type, image information is available.<br/>You can set default values ​​to use as fallback values ​​when the pipeline is not auto-run (with the image registry type). | Full image name: `dd530b18-kr1-registry.container.nhncloud.com/pipeline-test/image-name:tag`<br/>Image name: `dd530b18-kr1-registry.container.nhncloud.com/pipeline-test/image-name`<br/>Image tag: `tag` |
| Judgement (execution management) selection value | Create a variable based on the value selected in the connected **Features - Judgement (execution management)** stage.                                                                     | `Selection value` of Judgement (execution management)                                                                                                                                                                 | 
| Generated date string            | Create a date string based on the point in time executing **Features - Providing User Variable** stage.<br/>For date format, use `java.text.SimpleDateFormat` rule.                    | Format: `yyyyMMddHHmmss` -> Variable value: `20250903113846`<br/>Format: `yyyy-MM-dd HH:mm:ss Z` -> Variable value: `2025-09-04 16:58:44 +0900`                                                                            |
| Random UUID           | Generate a version 4 (UUID v4) with a standard string of 8-4-4-4-12 hyphenated characters (36 characters total).                                                                | `550e8400-e29b-41d4-a716-446655440000`                                                                                                                                                       |
| User input value              | You can use values ​​you enter directly as variables.                                                                                                  | `Input value`                                                                                                                                                                                       |

![stage-guide-22](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-22.png)

<a id="features---analyze-image-vulnerability"></a>
### Features - Analyze Image Vulnerability { #features---analyze-image-vulnerability }

A stage where vulnerability analysis is performed on images.

- Image registry
    - You can select the [Image Registry](./environment-config/#image-registry) you added in **Image Registry Settings** of **Preferences**.
- Specify the image you want to analyze by entering the **Image Name** and **Tags**.

![stage-guide-23](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-23.png)

The results of the image vulnerability analysis can be viewed in the stage execution results. If a vulnerability is found, details are displayed in the analysis results.

![stage-guide-24](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-24.png)

<a id="features---analyze-source-code-vulnerability"></a>
### Features - Analyze Source Code Vulnerability { #features---analyze-source-code-vulnerability }

A stage where vulnerability analysis is performed on the source code.

- Source repository
  - You can select the [Source Repository](./environment-config/#source-repository) you added in **Source Repository Settings** of **Preferences**.
- Select **Branch** to specify the source code to analyze.

![stage-guide-25](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-25.png)

The results of the source code vulnerability analysis can be viewed in the stage execution results. If a vulnerability is found, details are displayed in the analysis results.

![stage-guide-26](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-26.png)

<a id="stage-common-features"></a>
## Stage Common Features { #stage-common-features }

<a id="on-stage-failure"></a>
### On stage failure { #on-stage-failure }

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
