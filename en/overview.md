<!-- pre-align:aligned sig=188fdbf35804 -->

<a id="dev-tools-pipeline-overview"></a>
## Dev Tools > Pipeline > Overview { #dev-tools-pipeline-overview }
Pipeline is a continuous deployment service that allows you to manage the application deployment flow, such as building source code, creating container images, and deploying container images.

<a id="main-features"></a>
### Main Features { #main-features }
* NHN Cloud build tool
* Jenkins integration
* Kubernetes integration
* Application deployment flow management
* Application deployment automation
* Approval Feature

<a id="feature-description"></a>
### Feature Description { #feature-description }
Pipeline provides a number of features that you can use to deploy applications.

<a id="feature-description-nhn-cloud-build-tool"></a>
#### NHN Cloud Build Tool
Pipeline provides the NHN Cloud build tool that you can use to build source code and create container images. The NHN Cloud build tool allows you to build the application source code stored in the source repository without installing additional software, create a container image with the built application, and upload the created container image to the image registry.

<a id="feature-description-jenkins-integration"></a>
#### Jenkins Integration

By integrating Pipeline with Jenkins, you can add Jenkins jobs. Various user-defined Jenkins jobs can be used for application deployment.

<a id="feature-description-kubernetes-integration"></a>
#### Kubernetes Integration

By integrating Pipeline with Kubernetes, you can add Kubernetes jobs. It provides various features, such as deploying container images, changing the number of Pod replicas, and deleting Kubernetes objects.

<a id="feature-description-application-deployment-flow-management"></a>
#### Application Deployment Flow Management

You can define the different stages required for application deployment, such as building source code, creating a container image, uploading a container image, and deploying a container image, and save it as a pipeline. Saved pipelines can be rerun at any time.

<a id="feature-description-application-deployment-automation"></a>
#### Application Deployment Automation

You can configure autorun on the pipeline. When you change the source code in the source repository or update the container images in the image registry, the pipeline is run automatically.

<a id="feature-description-approval-feature"></a>
#### Approval Feature

By using approval management stages in a pipeline, ensure that subsequent stages don't run without approval from an approver.

<a id="feature-description-artifact"></a>
#### Artifact

Artifact is a concept used when handling external resources such as Docker container images and configuration files in pipeline configuration. You can designate external resources to be used in the pipeline as artifacts and use them as stage start/end conditions.

<a id="feature-description-artifact-type"></a>
#### Artifact Type
| Type        | Description               |
|-----------|-------------------|
| GitHub file | File in a GitHub repository |
| GitLab file | File in a GitLab repository |
| HTTP file   | File accessible with an URL  |
| Docker image | Image in an image repository |
|Kubernetes object| Object created in a Kubernetes cluster|

<a id="glossary"></a>
### Glossary { #glossary }
| Term | Description |
|---|---|
| Pipeline | NHN Cloud's continuous deployment service |
| pipeline | An object that stores the application deployment flow |
| stage | Each of the deployment stages that make up the pipeline |
| NHN Cloud build tool | Pipeline's built-in build tool |

