## Dev Tools > Pipeline > Console User Guide > Env Configuration

### Set Up an Environment

Pipeline uses various external systems to configure the application deployment flow. You can add external systems used by Pipeline in environment settings.

External systems that can be added to Pipeline include:
- Source repository
- Image registry
- Build tool
- Deployment target
- Chart repository

### Source Repository

After adding the source repository, you can build the source code using the NHN Cloud build tool. You can add repositories that can be accessed using the git commands, such as GitHub, GitLab, or GitHub Enterprise.

![env-config-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-01.png)

Click **Source Repository Settings** in **Environment Settings** to go to the screen to manage source repositories. You can add a new source repository by clicking **Add Source Repository**.

![env-config-guide-02](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-02.png)

Enter the source repository information. After checking the connection, click **Confirm**.
- When obtaining a token for a GitLab source repository, `repo` permissions are required.
- When obtaining a token for a GitLab source repository, `read_user`, `api`, `read_api` permissions are required.

![env-config-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-03.png)

### Image Registry

If you add an image registry, you can use the information to access an image registry that requires credentials. You can use the image registry when creating a container to build source code in the NHN Cloud build tool, or when uploading a newly created container image. You can also use it to set the container image that executes autorun in your pipeline autorun settings. For image registry, you can add NHN Cloud Container Registry, Docker Hub, or private image registries. When using Docker Hub, image repository URLs can be omiited.

![env-config-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-04.png)

Click **Image Registry Settings** in **Environment Settings** to go to the screen to manage image repositories. You can add a ne source repository by clicking **Add Image Registry**.

![env-config-guide-05](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-05.png)

Enter the image registry information, and click **Check** in **Image Registry Connection Check**. After checking the connection, click **Confirm**. If you don't enter the image registry URL, it works as Docker Hub.

![env-config-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-06.png)

### Build Tool

By adding a build tool, your pipeline can use the various actions you define in the build tool. For the build tool, you can add Jenkins. If you use `NHN Cloud Build Tools`, you can skip adding build tools.

![env-config-guide-07](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-07.png)

Click **Build Tool Settings** in **Environment Settings** to go to the screen to manage the build tool. You can add a new build tool by clicking **Add Build Tool**.

![env-config-guide-08](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-08.png)

Enter the build tool information, click **Check** in **Build Tool Connection Check**. After checking the connection, click **Confirm**.

![env-config-guide-09](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-09.png)

### Deployment Target

Adding a deployment target allows you to manage the deployment target in your pipeline. You can deploy container images to deployment targets or change the running containers. For deployment targets, you can add NHN Cloud Container and Kubernetes.

![env-config-guide-10](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-10.png)

Click **Deployment Target Settings** in **Environment Settings** to go to the screen to manage deployment targets. You can add new deployment targets by clicking **Add Deployment Target**.

![env-config-guide-11](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-11.png)

Enter the deployment target name and deployment target description, select the Kubeconfig file, and click **Check** in **Deployment Target Connection Check**. After checking the connection, click **Confirm**.

![env-config-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-12.png)

### Chart Repository

If you add a chart repository, you can build Helm chart by using the **Build - Bake (Manifest)** stage. You can find how to configure a chart repository in [Chart Repository Guide](https://helm.sh/docs/topics/chart_repository/).

![env-config-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-13.png)

Click **Chart Repository Settings** in **Environment Settings** to go to the screen to manage source repositories. You can add a source repository by clicking **Add Chart Repository**.

![env-config-guide-14](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-14.png)

Enter the chart repository information, click **Check** in **Chart Repository Connection Check**. After checking the connection, click **Confirm**.

![env-config-guide-15](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-15.png)


### Pipeline IP
If the system integrated with Pipeline does not work properly, check the ACL. The IP address used by Pipeline is **211.56.1.0/27**.

| Service | CIDR |
|---|---|
| Pipeline | 211.56.1.0/27 |
