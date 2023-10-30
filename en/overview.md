## Dev Tools > Pipeline > Overview
Pipeline is a continuous deployment service that allows you to manage the application deployment flow, such as building source code, creating container images, and deploying container images.

### Main Features
* NHN Cloud build tool
* Jenkins integration
* Kubernetes integration
* Application deployment flow management
* Application deployment automation
* Approval Feature

### Feature Description
Pipeline provides a number of features that you can use to deploy applications.

#### NHN Cloud Build Tool
Pipeline provides the NHN Cloud build tool that you can use to build source code and create container images. The NHN Cloud build tool allows you to build the application source code stored in the source repository without installing additional software, create a container image with the built application, and upload the created container image to the image registry.

#### Jenkins Integration

By integrating Pipeline with Jenkins, you can add Jenkins jobs. Various user-defined Jenkins jobs can be used for application deployment.

#### Kubernetes Integration

By integrating Pipeline with Kubernetes, you can add Kubernetes jobs. It provides various features, such as deploying container images, changing the number of Pod replicas, and deleting Kubernetes objects.

#### Application Deployment Flow Management

You can define the different stages required for application deployment, such as building source code, creating a container image, uploading a container image, and deploying a container image, and save it as a pipeline. Saved pipelines can be rerun at any time.

#### Application Deployment Automation

You can configure autorun on the pipeline. When you change the source code in the source repository or update the container images in the image registry, the pipeline is run automatically.

#### Approval Feature

By using approval management stages in a pipeline, ensure that subsequent stages don't run without approval from an approver.

#### Artifact

Artifact is a concept used when handling external resources such as Docker container images and configuration files in pipeline configuration. You can designate external resources to be used in the pipeline as artifacts and use them as stage start/end conditions.

#### Artifact Type
| Type        | Description               |
|-----------|-------------------|
| GitHub file | File in a GitHub repository |
| GitLab file | File in a GitLab repository |
| HTTP file   | File accessible with an URL  |
| Docker image | Image in an image repository |
|Kubernetes object| Object created in a Kubernetes cluster|

### Glossary
| Term | Description |
|---|---|
| Pipeline | NHN Cloud's continuous deployment service |
| pipeline | An object that stores the application deployment flow |
| stage | Each of the deployment stages that make up the pipeline |
| NHN Cloud build tool | Pipeline's built-in build tool |

