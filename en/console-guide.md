## Dev Tools > Pipeline > Console User Guide

This guide explains the basics of using Pipeline.
- **Set up an environment**
- **Create a pipeline**
- **Run a pipeline**
- **Manage a pipeline**
- **Set up a development environment**

### Set Up an Environment

Pipeline uses various external systems to configure the application deployment flow. You can add external systems used by Pipeline in environment settings.

External systems that can be added to Pipeline include:
- Source repository
- Image registry
- Build tool
- Deployment target

#### Source Repository

After adding the source repository, you can build the source code using the NHN Cloud build tool. You can add repositories that can be accessed using the git commands, such as GitHub, GitLab, or GitHub Enterprise.

![console-guide-01](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-01.png)

Click **Source Repository Settings** in **Environment Settings** to go to the screen to manage source repositories. You can add a source repository by clicking **Add Source Repository**. 

![console-guide-02](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-01.png)

Enter the source repository information, and click **Check** in **Source Repository Connection Check**. To obtain a token for a GitLab source repository, `read_user`, `api`, and `read_api` permissions are required. After checking the connection, click **Confirm**.

![console-guide-03](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-03.png)

#### Image Registry

If you add an image registry, you can use the information to access an image registry that requires credentials. You can use the image registry when creating a container to build source code in the NHN Cloud build tool, or when uploading a newly created container image. You can also use it to set the container image that executes autorun in your pipeline autorun settings. For image registry, you can add NHN Cloud Container Registry, Docker Hub, or private Docker registry.

![console-guide-04](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-04.png)

Click **Image Registry Settings** in **Environment Settings** to go to the screen to manage image repositories. You can add a source repository by clicking **Add Image Registry**.

![console-guide-05](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-02.png)

Enter the image registry information, and click **Check** in **Image Registry Connection Check**. After checking the connection, click **Confirm**. If you don't enter the image registry URL, it works as Docker Hub.

![console-guide-06](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-06.png)

#### Build Tool

By adding a build tool, your pipeline can use the various actions you define in the build tool. For the build tool, you can add Jenkins.

![console-guide-07](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-07.png)

Click **Build Tool Settings** in **Environment Settings** to go to the screen to manage the build tool. You can add a build tool by clicking **Add Build Tool**.

![console-guide-08](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-03.png)

Enter the build tool information, click **Check** in **Build Tool Connection Check**. After checking the connection, click **Confirm**.

![console-guide-09](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-09.png)

#### Deployment Target

Adding a deployment target allows you to manage the deployment target in your pipeline. You can deploy container images to deployment targets or change the running containers. For deployment targets, you can add NHN Cloud Container and Kubernetes.

![console-guide-10](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-10.png)

Click **Deployment Target Settings** in **Environment Settings** to go to the screen to manage deployment targets. You can add deployment targets by clicking **Add Deployment Target**.

![console-guide-11](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-04.png)

Enter the deployment target name and deployment target description, select the Kubeconfig file, and click **Check** in **Deployment Target Connection Check**. After checking the connection, click **Confirm**.

![console-guide-12](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-12.png)


#### Pipeline IP
If the system integrated with Pipeline does not work properly, check the ACL. The IP address used by Pipeline is **211.56.1.0/27**.

| Service | CIDR |
|---|---|
| Pipeline | 211.56.1.0/27 |

### Create a Pipeline

Pipeline stores the application deployment flow as a pipeline consisting of one or more stages. In Create Pipeline, you can create a basic pipeline that works in the following order: **Build Source Code** > **Create Container Image** > **Upload Container Image** > **Deploy Container Image**.

![console-guide-13](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-13.png)

Click **Create Pipeline** in **Pipeline Management**. Pipeline creation is performed in the following steps.
- Entering pipeline information
- Source settings
- Build Settings
- Deployment settings
- Final review and pipeline creation

#### Entering Pipeline Information

Enter basic information of the pipeline.

![console-guide-14](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-14.png)

Enter the pipeline name and pipeline description, and click **Next**.

#### Source Settings

Set the source repository used when building the source code in the NHN Cloud build tool. If you do not use the NHN Cloud build tool or do not build the source code in the NHN Cloud build tool, you can skip this step.

![console-guide-15](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-15.png)

Enter the stage name, the source repository registered in the environment settings, and the branch to build the source code from, and click **Next**.

#### Build Settings

In the build settings, you can use the NHN Cloud build tool or the build tool registered in the environment settings. Enter a stage name and select the build tool to use under **Build Tool**.

![console-guide-16](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-16.png)

The NHN Cloud build tool allows you to build the application source code stored in the source repository without installing additional software, create a container image with the built application, and upload the created container image to the image registry.
In **Build Environment Settings**, enter the method of building the application using the source code set in **Source Settings**. You can enter the container image to use for building the source code, the performance of the build machine, and the command to use for the build.
In **Build Result Settings**, enter how to create a container image with the built application. You can enter the Dockerfile to use when creating the container image, the image registry to upload the created container image to, and the name and tag of the container image to upload.

![console-guide-17](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-17.png)

The build tool added in the environment settings allows you to run the build tool's build job. If you select a build job to run, you can enter additional parameters for the build job.

After completing the build settings, click **Next**.

#### Deployment Settings

In deployment settings, you can set how the container image is deployed to the deployment target added in the environment settings.

![console-guide-18](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-18.png)

Enter the stage name, deployment target, and Manifest to use for deployment, and click **Next**. See the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/controllers/deployment) for how to write a Manifest.

#### Final Review and Pipeline Creation

In the final review, you can check the full configuration you’ve entered for your pipeline.

![console-guide-19](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-19.png)

After confirming the entered configuration, click **Create**.

![console-guide-20](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-20.png)

### Run a Pipeline

There are two ways to run a pipeline: manual run and automatic run.

#### Manual Run

Manual run allows you to run your pipeline when you want.

![console-guide-21](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-21.png)

In **Pipeline Management**, click ▶︎ (Manual Run). when the dialog box appears, click **OK**.

#### Autorun

Autorun lets you configure your pipeline to run automatically when an event occurs in your GitHub repository or when a container image in your image registry is updated.

![console-guide-22](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-22.png)

Click **Autorun Settings** and click **Add** in the **Autorun Settings** dialog box.

![console-guide-23](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-23.png)

Using a GitHub webhook, you can configure your pipeline to run automatically when an event occurs in a repository on GitHub or GitHub Enterprise. Set the autorun type to GitHub, enter the repository's organization or user name, project name, branch, and secret, and click **OK**.

![console-guide-24](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-24.png)

Set up a webhook in your repository on GitHub or GitHub Enterprise.

| Item | Setting value |
|---|---|
| Payload URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | The value entered in the secret of the pipeline autorun settings |

![console-guide-35](http://static.toastoven.net/prod_pipeline/2022-02-15/console-guide-02.png)

Using a GitLab webhook, you can configure your pipeline to run automatically when an event occurs in the GitLab repository. Set the autorun type to GitLab, enter the repository's organization or user name, project name, and branch, and click **OK**. GitLab secret setting will be supported in the future.

![console-guide-36](http://static.toastoven.net/prod_pipeline/2022-02-15/console-guide-03.png)
Set up a webhook in the GitLab repository.

| Item | Setting value |
|---|---|
| URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Select Push events |
| Secret | Do not set |
| SSL verification | Select Enable SSL verification |


![console-guide-25](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-25.png)

If you want the pipeline to run automatically when the container image is updated, set the autorun type to image registry. After selecting the image registry registered in the environment settings, select the container image to use for autorun from the list of container images. Finally, enter a tag and click **OK**. The image registry autorun configuration only supports NHN Cloud Container Registry and private Docker registry. Docker Hub will be supported in the future.

![console-guide-26](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-26.png)

When a new pipeline is created, **Prevent Autorun** is set to **Enable**. If you want the pipeline to run automatically, you must change **Prevent Autorun** to **Disable**. After selecting the pipeline, click **Change** under Prevent Autorun at the bottom of Basic Information. In the Set Autorun Prevention dialog box, select **Disable** and click **OK**.

![console-guide-27](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-27.png)

To check the detailed information about the running pipeline, select a running pipeline and click **Details** under Recent Run Status in Basic Information at the bottom.

### Manage a Pipeline

You can add, change, or delete stages that make up the pipeline.

![console-guide-28](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-28.png)

After selecting a pipeline, click **Stage** at the bottom to display the screen to manage stages. Click **Add Stage**, and the **Add Stage** dialog box appears.

![console-guide-29](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-29.png)

After setting the stage name, stage type, input values for each stage type, and previous stage, click **Add Stage** to add a stage to the pipeline. Pipeline provides a number of different stage types that you can use when configuring your application deployment flow.

![console-guide-30](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-30.png)

Stages can run in parallel depending on how the previous stage is selected. If one of the stages in the parallel configuration fails, execution of the remaining stages is canceled and the pipeline execution fails.

### Set up a Development Environment

The development environment settings allows users who do not know how to use Kubernetes to deploy container images on Kubernetes.

![console-guide-31](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-31.png)

Under **Development Environment Settings**, click **Create Development Environment**. 

![console-guide-32](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-32.png)

Enter a development environment name and development environment description, and select the container image to deploy from the basic images. Set the information required to access the container image in the image registry. For the deployment target, select the Kubernetes to deploy the container image to. For the service port, enter the port of the service provided by the container. If you enter a service port, a service IP that can access the container service is automatically assigned (if Kubernetes provides a service of the LoadBalancer type). Finally, after entering the development environment constraints, click **Create** to create the development environment.

![console-guide-33](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-33.png)

While the development environment is being created, the **Development Environment Status** is displayed as **Creating**.

![console-guide-34](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-34.png)

When the development environment creation is complete, the **Development Environment Status** is changed to **Running**. You can access the container service using the service IP and service port.
