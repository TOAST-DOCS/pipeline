## Dev Tools > Pipeline > Release Notes

### March 25, 2025
* **Pipeline Notifications** feature has been added.
    * You can receive Email and SMS notifications when a pipeline starts, completes, or fails.
    * See the Pipeline Notification Guide for usage instructions.
* **Pipeline Version** has been modified so that pipelines can no longer be edited in JSON format.

### November 26, 2024
* Improve **Build - Bake (Manifest)** stage
    * Added a feature to check results.
    * Improved the UI of the Override subconfiguration in the stage contents.
* Added messages to help you determine the cause when a deployment stage fails.
* Added the feature to see change differences when rolling back from **Deployment Target Management**.

### October 29, 2024
* Added the source repository URL type to the source repository settings.
    * Changed to allow the use of public type for source repositories as well as private type.

### September 10, 2024
* Changed the UI design of the **Pipeline Management** menu. See [Pipeline Management](/Dev%20Tools/Pipeline/en/pipeline-management/) for how to use.

### May 28, 2024
* Added new stages. You can learn how to use them in the [Pipeline Stage Guide](/Dev%20Tools/Pipeline/en/stage-guide/).
    * **Deployment - Disable**
    * **Deployment - Enable**
    * **Features - Precondition (Stage Status Condition)**
* Added the feature to dynamically select resource selection.
    * Applied Stages
        * **Deployment - Delete**
        * **Deployment - Disable**
        * **Deployment - Enable**
        * **Deployment - Patch**
        * **Deployment - Scale**
* Added the **stage failure feature** to all stages. You can see how to use it in the [Pipeline Stage Guide](/Dev%20Tools/Pipeline/en/stage-guide/).
* You can use a blue/green deployment. You can learn how to use them in the [Deployment Strategy Guide](/Dev%20Tools/Pipeline/en/deploy-strategy-guide/).

### April 23, 2024
* Added the chart repository URL type to Chart Repository Settings.
    * Made modifications so that the public type is available for chart repository, in addition to the private type.

### March 26, 2024
* Added **Deployment - NHN Container Service**, a new deployment stage. See [Pipeline Stage Guide](/Dev%20Tools/Pipeline/zh/stage-guide/).

### February 27, 2024
* Added a new build stage, NHN Cloud Build Tool v2.
    * Improved performance and changed tag formats.
        * AS-IS: _{BUILD_NUMBER}
        * TO-BE: {BUILD_DATE_TIME}
    * Existing build tools will be faded out no longer be created.

### January 23, 2024.
* Added the feature to set email recipient address in Organization/Project Dashboard > Manage Notifications.
* Added the Confirm Scenario button when selecting a scenario in the NHN Cloud Deploy Service stage.
    * Click **Confirm Scenario**to view task information for that scenario.
* Added the **Deployment History Management** page, where you can view the history of pipeline runs and deployment target tasks. You can see how to use it in the [Deployment History Management Guide](/Dev%20Tools/Pipeline/en/deploy-history-management).

### December 19, 2023
* The **Feature - NHN Cloud Deploy Service** stage has been added to run deployment scenarios of NHN Cloud Deploy. For how to use it, see [Pipeline Stage Guide](/Dev%20Tools/Pipeline/en/stage-guide/).
* Added **Artifact** to the GitHub Autorun settings. Set a specific file as an artifact to run a pipeline when a Git push event occurs, based on the inclusion or exclusion of that file.

### October 31, 2023
* Added the **Feature - Approval Management** stage that prevents subsequent stages from running without approval. For more information, see [Pipeline Stage Guide](/Dev%20Tools/Pipeline/en/stage-guide/).
* Added sample scenarios in the Pipeline Template Guide. You can download how-to and template files from [Pipeline Template Guide](/Dev%20Tools/Pipeline/en/pipeline-management/#_2).

### September 26, 2023
* Added the pipeline template feature. For how to use the feature, see [Pipeline User Guide](/Dev%20Tools/Pipeline/en/pipeline-management/#_1).
    * Create a pipeline by uploading template files(JSON format).
    * Download pipeline template files from **View JSON** > **Download Pipeline Template**.
* You can use tags in **Branch or Tag** from Github Autorun Settings. Use tags to perform builds on autorun with tags.

### August 29, 2023
* Added the **Feature - Run the Pipeline** stage to run entire other pipelines. See [Pipeline User Guide](/Dev%20Tools/Pipeline/en/stage-guide/#_4).
* The development environment feature provided by the Pipeline service is no longer provided. The development environment feature is available as a notebook of AI EasyMaker service. More details can be found in the [AI EasyMaker User Guide](/Machine%20Learning/AI%20EasyMaker/en/console-guide/#_2).
* Renamed **Deployment Target Monitoring** to **Deployment Target Management**.
* Added the feature to manage workloads deployed to clusters via Pipeline and check the workload history to the **Deployment Target Management**.

### June 27, 2023
* Deployment - Added the Deploy Target Management feature that allows you to check the output deployed to the Deploy stage. For more information, see [Pipeline User Guide](/Dev%20Tools/Pipeline/en/deploy-target-monitoring).
    * Kubernetes workloads and services can be found in Deploy Target Management.
* Added the [Feature - Judgement (Run Management)] and [Feature - Precondition (Run Condition)] stages that allow for pipeline branch processing. For more information, see [Pipeline Stage Guide](/Dev%20Tools/Pipeline/en/stage-guide/#feature-judgement-run-management) and [Pipeline User Guide](/Dev%20Tools/Pipeline/en/pipeline-management/#run-history-and-work).

### March 28, 2023
* Added the Build - Bake (Manifest) stage that can create results for deployment using Helm charts. For more details, see [Pipeline User Guide](/Dev%20Tools/Pipeline/en/stage-guide/#build-bake-manifest).
* Added the chart repository settings available in the Build - Bake (Manifest) stage. For more details, see [Pipeline User Guide](/Dev%20Tools/Pipeline/en/environment-config/#chart-repository).
* Added a feature to select Manifest as artifacts in the Deployment - Deploy stage.

### February 28, 2023
* Added an artifact feature that allows you to use external repository resources as start or end condtions for pipeline stages. You can find how to use in [Pipeline User Guide](/Dev%20Tools/Pipeline/en/pipeline-management/#create-a-pipeline)

### January 31, 2023
* Added a feature to assign dynamically created tags by using the image tag format in the build stage.
* Added a feature to deploy with the most recent tag among tags dynamically created using the image tag format in the deployment stage.
* Changes to how image autorun is executed as follows.
    * Tag value is excluded from required values from autorun settings.
    * Changed to automatically run the entered tag and a matched tag with regular expression are pushed.
    * Changed to automatically run a tag when it is pushed with tags excluding latest as long as the tag is not entered.

### December 27, 2022
* Fixed an issue where, when creating a pipeline, you have to select a source repository in the Source Settings step to go to the previous stage.

### October 25, 2022
* Modified to display a guide message when the kubernetes integration test in deployment target times out.

### August 23, 2022
* Made modifications so that, when running a pipeline without stages through the [API](/Dev%20Tools/Pipeline/en/api-guide/#pipeline), a failure response is returned.

### July 26, 2022
* Added a webhook stage.
* Changed the API endpoint domain from api-pipeline.cloud.toast.com to kr1-pipeline.api.nhncloudservice.com.

### May 24, 2022
* Added the connection check feature for the source repository, image registry, build tool, and deployment target. You can see how to use it in the [Pipeline User Guide](/Dev%20Tools/Pipeline/en/environment-config). 
* Added details to CloudTrail.
    * Added details for deletion of settings
    * Added details about pipeline execution

### February 22, 2022
* Added GitLab to the source repository. You can find how to use it in the [Pipeline User Guide](/Dev%20Tools/Pipeline/en/environment-config/#source-repository).

### January 25, 2022
* Added an API to run Pipeline. You can find how to use it in the [Pipeline API Guide](/Dev%20Tools/Pipeline/en/api-guide/#pipeline).
* Known issues (to be improved after analyzing the cause)
    * When creating a development environment, if you specify a value for the development environment constraints, the development environment creation fails.

### May 25, 2021
* Added integration with CloudTrail. You can check the events that occurred in Pipeline in CloudTrail.

### April 27, 2021

#### Release of a New Service
* A continuous deployment (CD) service that lets you manage the application deployment flow, such as building source code, creating container images, and deploying container images.
