## Dev Tools > Pipeline > Stage Guide

This guide describes the basics of stages in Pipeline. 
Click **Pipeline Management** > **+Create Pipeline** to create a pipeline. After selecting the pipeline you created, you can add a stage by clicking **+Add Stage** in the **Stage** tab at the bottom.

![stage-guide-01](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-01.png)

Stages are divided into the following groups.
- **Source**
- **Build**
- **Deployment**
- **Feature**

### Source
This is a stage that gets the source code to build.

#### Source - GitHub
You can select the [source repository](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) that you added in **Source Repository Settings** of **Environment Settings**.

![stage-guide-02](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-02.png)

#### Source - GitLab
You can select the [source repository](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) that you added in **Source Repository Settings** of **Environment Settings**.

![stage-guide-03](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-03.png)

### Build
This is a stage to build

#### Build - Jenkins
You can build using Jenkins that you configured yourself. You can select the [build tool](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) you added in **Build Tool Settings** of **Environment Settings**. You can select **Build Job** and enter **Build Job Parameters**.

![stage-guide-04](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-04.png)

#### Build - NHN Cloud Build Tool
You can use the build tools provided by NHN Cloud.
- Build Environment Settings
  - You can select the [image registry](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) you added in the **Image Registry Settings** in **Environment Settings**.
  - Select the **Image Name** of the environment to build, set the **Build Tool Performance**, **Build Time Limit (minutes),** and **Build Command**.
  
- Build Result Settings
  - Set the **Dockerfile Path** of the build result, and the **Dockerfile Execution Path**.
  - Select a **Image Registry** and decide on **Image Name**, and the build result is pushed to the selected repository.
  - If **Use Tag Format** is selected, the tag format is fixed, and the image is created with dynamically generated tags in the form of `_{BUILD_NUMBER}`.

![stage-guide-05](http://static.toastoven.net/prod_pipeline/2023-01-13/stage-guide-01.png)

### Deployment
This is a stage to deploy to the Kubernetes environment.

#### Deployment - Deploy
You can select the [deployment target](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) you added in **Deployment Target Settings** in **Environment Settings**. 
Enter **Stage Name**, **Deployment Target**, and **Manifest** to use for deployment. 
If the tag format is used in the build stage, when the docker image tag of **Manifest** is entered as `_{BUILD_NUMBER}`, you can deploy as the image with the most recent number among the images built in the tag format.
See the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/controllers/deployment ) for how to write **Manifest**.

![stage-guide-06](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-06.png)

#### Deployment - Patch
You can select the [deployment target](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) you added in **Deployment Target Settings** in **Environment Settings**.
Enter **Namespace**, **Resource Type**, **Resource Name**, and **Manifest** to use for deployment.You can modify the information of an existing resource with Patch. 
See the [Kubernetes documentation](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources) for how to write **Manifest**.

![stage-guide-07](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-07.png)

#### Deployment - Scale
You can select the [deployment target](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) you added in **Deployment Target Settings** in **Environment Settings**. 
Enter **Namespace**, **Resource Type**, **Resource Name**, and **Replicas**. Replicas can be modified with Scale.

![stage-guide-08](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-08.png)

#### Deployment - Rollout Undo
You can select the [deployment target](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) you added in **Deployment Target Settings** in **Environment Settings**. 
Enter **Namespace**, **Resource Type**, **Resource Name**, **Revision Back**. You can roll back to the specified Revision.

![stage-guide-09](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-09.png)

#### Deployment - Delete
You can select the [deployment target](https://docs.nhncloud.com/en/Dev%20Tools/Pipeline/en/console-guide/#_1) you added in **Deployment Target Settings** in **Environment Settings**. 
Enter **Namespace**, **Resource Type**, and **Resource Name**. You can delete the resource.

![stage-guide-10](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-10.png)

### Feature
This is a stage to provide additional features.

#### Feature - Webhook
Enter the HTTP method and URL in **URL**. You can add **Request Header** and **Request Data** as needed. 
If the response value of the webhook is one of the values entered in **Fail Fast HTTP Status Code**, close the stage immediately.

![stage-guide-11](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-11.png)
