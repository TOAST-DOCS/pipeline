## Dev Tools > Pipeline > Console User Guide > Dev Env Configuration

### Set up a Development Environment

The development environment settings allows users who do not know how to use Kubernetes to deploy container images on Kubernetes.

![dev-env-config-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-01.png)

Under **Development Environment Settings**, click **Create Development Environment**.

![dev-env-config-guide-02](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-02.png)

Enter a development environment name and development environment description, and select the container image to deploy from the basic images. Set the information required to access the container image in the image registry. For the deployment target, select the Kubernetes to deploy the container image to. For the service port, enter the port of the service provided by the container. If you enter a service port, a service IP that can access the container service is automatically assigned (if Kubernetes provides a service of the LoadBalancer type). Finally, after entering the development environment constraints, click **Create** to create the development environment.

![dev-env-config-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-03.png)

While the development environment is being created, the **Development Environment Status** is displayed as **Creating**.

![dev-env-config-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-04.png)

When the development environment creation is complete, the **Development Environment Status** is changed to **Running**. You can access the container service using the service IP and service port.
