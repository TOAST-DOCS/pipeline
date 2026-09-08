<!-- machine_translated: true -->

<!-- pre-align:aligned sig=27f20a0f6e45 -->

<a id="dev-tools-pipeline-release-notes"></a>
## Dev Tools > Pipeline > Release Notes { #dev-tools-pipeline-release-notes }

<a id="september-15-2026"></a>
## September 15, 2026 { #september-15-2026 }

* Added the **Use Resource Version Management** option to the **Deploy - Deploy** stage.
  * If you disable the option, resources are deployed with the original names defined in the manifest.
  * For more information, see [Pipeline Stage Guide](/Dev%20Tools/Pipeline/en/stage-guide/).


<a id="april-14-2026"></a>
## April 14, 2026 { #april-14-2026 }

* Added the API v1.1 guide for using User Access Key tokens.
  * For more information, see the [API v1.1 Guide](./api-guide-v1-1/).

<a id="september-23-2025"></a>
## September 23, 2025 { #september-23-2025 }

* Added new stages. For more information, see the [Pipeline Stage Guide](./stage-guide/).
  * **Feature - Provide User Variables**
  * **Feature - Image Vulnerability Analysis**
  * **Feature - Source Code Vulnerability Analysis**
* Improved the UI for pipeline execution wait status.
  * When a pipeline is in the execution wait status, it is displayed with an execution wait badge.
  * When the **Feature - Approval Management** stage is running, it is displayed with an approval wait badge.
  * When the **Feature - Judgement (Execution Management)** stage is running, it is displayed with a selection wait badge.
  
<a id="june-24-2025"></a>
## June 24, 2025 { #june-24-2025 }

* **Build - NHN Cloud Build Tool** stage is being faded out.

<a id="april-15-2025"></a>
## April 15, 2025 { #april-15-2025 }

* Added **Run History** feature to Pipeline Studio
  * You can see the 10 most recent runs.
  * See the Pipeline Run History Guide for how to use.
* Changed to allow additional registration of image repositories required for image builds in NHN Cloud Build Tool v2.

<a id="march-25-2025"></a>
## March 25, 2025 { #march-25-2025 }

* **Pipeline Notifications** feature has been added.
  * You can receive Email and SMS notifications when a pipeline starts, completes, or fails.
  * You can find how to use from [Pipeline Notification Guide](./pipeline-management/#manage-a-pipeline).
* **Pipeline Version** has been modified so that pipelines can no longer be edited in JSON format.
* **Build - NHN Cloud Build Tool** stage fades out.

<a id="november-26-2024"></a>
## November 26, 2024 { #november-26-2024 }

* Improve **Build - Bake (Manifest)** stage
  * Added a feature to check results.
  * Improved the UI of the Override subconfiguration in the stage contents.
* Added messages to help you determine the cause when a deployment stage fails.
* Added the feature to see change differences when rolling back from **Deployment Target Management**.

<a id="october-29-2024"></a>
## October 29, 2024 { #october-29-2024 }

* Added the source repository URL type to the source repository settings.
  * Changed to allow the use of public type for source repositories as well as private type.

<a id="september-10-2024"></a>
## September 10, 2024 { #september-10-2024 }

* Changed the UI design of the **Pipeline Management** menu. See [Pipeline Management](./pipeline-management/) for how to use.

<a id="may-28-2024"></a>
## May 28, 2024 { #may-28-2024 }

* Added new stages. You can learn how to use them in the [Pipeline Stage Guide](./stage-guide/).
  * **Deployment - Disable**
  * **Deployment - Enable**
  * **Feature - Precondition (Stage Status Condition)**
* Added the feature to dynamically select resource selection.
  * Applied Stages
    * **Deployment - Delete**
    * **Deployment - Disable**
    * **Deployment - Enable**
    * **Deployment - Patch**
    * **Deployment - Scale**
* Added the **stage failure feature** to all stages. You can see how to use it in the [Pipeline Stage Guide](./stage-guide/).
* You can use a blue/green deployment. You can learn how to use them in the [Deployment Strategy Guide](./deploy-strategy-guide/).

<a id="april-23-2024"></a>
## April 23, 2024 { #april-23-2024 }

* Added the chart repository URL type to Chart Repository Settings.
    * Made modifications so that the public type is available for chart repository, in addition to the private type.

<a id="march-26-2024"></a>
## March 26, 2024 { #march-26-2024 }

* Added **Deployment - NHN Container Service**, a new deployment stage. See [Pipeline Stage Guide](./stage-guide/).

<a id="february-27-2024"></a>
## February 27, 2024 { #february-27-2024 }

* Added a new build stage, NHN Cloud Build Tool v2.
  * Improved performance and changed tag formats.
    * AS-IS: _{BUILD_NUMBER}
    * TO-BE: {BUILD_DATE_TIME}
  * Existing build tools will be faded out no longer be created.

<a id="january-23-2024"></a>
## January 23, 2024 { #january-23-2024 }

* Added the feature to set email recipient address in Organization/Project Dashboard > Manage Notifications.
* Added the Confirm Scenario button when selecting a scenario in the NHN Cloud Deploy Service stage.
  * Click **Confirm Scenario**to view task information for that scenario.
* Added the **Deployment History Management** page, where you can view the history of pipeline runs and deployment target tasks. You can see how to use it in the [Deployment History Management Guide](./deploy-history-management/).

<a id="december-19-2023"></a>
## December 19, 2023 { #december-19-2023 }

* The **Feature - NHN Cloud Deploy Service** stage has been added to run deployment scenarios of NHN Cloud Deploy. For how to use it, see [Pipeline Stage Guide](./stage-guide/).
* Added **Artifact** to the GitHub Autorun settings. Set a specific file as an artifact to run a pipeline when a Git push event occurs, based on the inclusion or exclusion of that file.

<a id="october-31-2023"></a>
## October 31, 2023 { #october-31-2023 }

* Added the **Feature - Approval Management** stage that prevents subsequent stages from running without approval. For more information, see [Pipeline Stage Guide](./stage-guide/).
* Added sample scenarios in the Pipeline Template Guide. You can download how-to and template files from [Pipeline Template Guide](/Dev%20Tools/Pipeline/en/pipeline-management/#_2).

<a id="september-26-2023"></a>
## September 26, 2023 { #september-26-2023 }

* Added the pipeline template feature. For how to use the feature, see [Pipeline User Guide](/Dev%20Tools/Pipeline/en/pipeline-management/#_1).
  * Create a pipeline by uploading template files(JSON format).
  * Download pipeline template files from **View JSON** > **Download Pipeline Template**.
* You can use tags in **Branch or Tag** from Github Autorun Settings. Use tags to perform builds on autorun with tags.

<a id="august-29-2023"></a>
## August 29, 2023 { #august-29-2023 }

* Added the **Feature - Run the Pipeline** stage to run entire other pipelines. See [Pipeline User Guide](/Dev%20Tools/Pipeline/en/stage-guide/#_4).
* The development environment feature provided by the Pipeline service is no longer provided. The development environment feature is available as a notebook of AI EasyMaker service. More details can be found in the [AI EasyMaker User Guide](/Machine%20Learning/AI%20EasyMaker/en/console-guide/#_2).
* Renamed **Deployment Target Monitoring** to **Deployment Target Management**.
* Added the feature to manage workloads deployed to clusters via Pipeline and check the workload history to the **Deployment Target Management**.

<a id="june-27-2023"></a>
## June 27, 2023 { #june-27-2023 }

* Deployment - Added the Deploy Target Management feature that allows you to check the output deployed to the Deploy stage. For more information, see [Pipeline User Guide](./deploy-target-monitoring/).
  * Kubernetes workloads and services can be found in Deploy Target Management.
* Added the [Feature - Judgement (Run Management)] and [Feature - Precondition (Run Condition)] stages that allow for pipeline branch processing. For more information, see [Pipeline Stage Guide](/Dev%20Tools/Pipeline/en/stage-guide/#feature-judgement-run-management) and [Pipeline User Guide](/Dev%20Tools/Pipeline/en/pipeline-management/#run-history-and-work).

<a id="march-28-2023"></a>
## March 28, 2023 { #march-28-2023 }

* Added the Build - Bake (Manifest) stage that can create results for deployment using Helm charts. For more details, see [Pipeline User Guide](/Dev%20Tools/Pipeline/en/stage-guide/#build-bake-manifest).
* Added the chart repository settings available in the Build - Bake (Manifest) stage. For more details, see [Pipeline User Guide](./environment-config/#chart-repository).
* Added a feature to select Manifest as artifacts in the Deployment - Deploy stage.

<a id="february-28-2023"></a>
## February 28, 2023 { #february-28-2023 }

* Added an artifact feature that allows you to use external repository resources as start or end condtions for pipeline stages. You can find how to use in [Pipeline User Guide](./pipeline-management/#create-a-pipeline)

<a id="january-31-2023"></a>
## January 31, 2023 { #january-31-2023 }

* Added a feature to assign dynamically created tags by using the image tag format in the build stage.
* Added a feature to deploy with the most recent tag among tags dynamically created using the image tag format in the deployment stage.
* Changes to how image autorun is executed as follows.
  * Tag value is excluded from required values from autorun settings.
  * Changed to automatically run the entered tag and a matched tag with regular expression are pushed.
  * Changed to automatically run a tag when it is pushed with tags excluding latest as long as the tag is not entered.

<a id="december-27-2022"></a>
## December 27, 2022 { #december-27-2022 }

* Fixed an issue where, when creating a pipeline, you have to select a source repository in the Source Settings step to go to the previous stage.

<a id="october-25-2022"></a>
## October 25, 2022 { #october-25-2022 }

* Modified to display a guide message when the kubernetes integration test in deployment target times out.

<a id="august-23-2022"></a>
## August 23, 2022 { #august-23-2022 }

* Made modifications so that, when running a pipeline without stages through the [API](./api-guide-v1-0/#pipeline-manual-run), a failure response is returned.

<a id="july-26-2022"></a>
## July 26, 2022 { #july-26-2022 }

* Added a webhook stage.
* Changed the API endpoint domain from api-pipeline.cloud.toast.com to kr1-pipeline.api.nhncloudservice.com.

<a id="may-24-2022"></a>
## May 24, 2022 { #may-24-2022 }

* Added the connection check feature for the source repository, image registry, build tool, and deployment target. You can see how to use it in the [Pipeline User Guide](./environment-config/). 
* Added details to CloudTrail.
  * Added details for deletion of settings
  * Added details about pipeline execution

<a id="february-22-2022"></a>
## February 22, 2022 { #february-22-2022 }

* Added GitLab to the source repository. You can find how to use it in the [Pipeline User Guide](./environment-config/#source-repository).

<a id="january-25-2022"></a>
## January 25, 2022 { #january-25-2022 }

* Added an API to run Pipeline. You can find how to use it in the [Pipeline API Guide](./api-guide-v1-0/).
* Known issues (to be improved after analyzing the cause)
  * When creating a development environment, if you specify a value for the development environment constraints, the development environment creation fails.

<a id="may-25-2021"></a>
## May 25, 2021 { #may-25-2021 }

* Added integration with CloudTrail. You can check the events that occurred in Pipeline in CloudTrail.

<a id="april-27-2021"></a>
## April 27, 2021 { #april-27-2021 }

<a id="april-27-2021-release-of-a-new-service"></a>
#### Release of a New Service

* A continuous deployment (CD) service that lets you manage the application deployment flow, such as building source code, creating container images, and deploying container images.
