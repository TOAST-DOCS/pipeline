## Dev Tools > Pipeline > Console User Guide > Pipeline Management

A pipeline defines an application deployment flow consisting of one or more stages.

### Configure a pipeline

#### Create a pipeline

You can create a pipeline by clicking **\+ Create Pipeline**, or you can create a pipeline by uploading a pipeline template file.
![pipeline-management-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-01.png)


In **Pipeline Management**, click **\+ Create Pipeline**.

![pipeline-management-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-02.png)

In the **Create Pipeline** modal window, enter **a pipeline name** and **pipeline description **, then click **Confirm**.

Alternatively, you can create a pipeline with a pipeline template file (pipeline templates use JSON files).

![pipeline-management-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-03.png)

After you upload the pipeline template file, click **Confirm**.

#### Pipeline Studio

Pipeline Studio is the page where users can manage basic information about their pipelines, or add, change, or delete the stages that make up a pipeline.

![pipeline-studio-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-1.png)

At the top of Pipeline Studio, you'll see basic information about the pipeline: its name, description, last modified date, and creator.

In the Pipeline Studio panel, you can see the stages that make up that pipeline.

#### Edit mode
![pipeline-studio-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-2.png)

You can enter edit mode by clicking the **edit mode** toggle in the top right corner. In the edit mode, you can add, change, delete, and reposition stages.

#### Add a stage
![pipeline-studio-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-3.png)

When you enable **Edit Mode**, the left side exposes the **Source**, **Build**, **Deploy**, and **Feature** groups, which are organized into different stages that you can use to organize your application deployment flow.

You can select the stages you want to add from the four groups and drag and drop them onto the screen.

![pipeline-studio-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-4.png)

When a stage is added, select it to enter the required information.

![pipeline-studio-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-5.png)

Set the order of execution by concatenating the stages to run before and the stages to add.

![pipeline-studio-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-6.png)

You can click **Save pipeline**in the top right corner to finish adding stages.

#### Editing Stages
![pipeline-studio-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-7.png)

You can edit a stage by enabling **edit mode**and then clicking the stage you want to edit.

![pipeline-studio-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-9.png)

After you've finished editing, you can click **Save Pipeline** in the top right corner to finalize your stage edits.

#### Delete a stage
![pipeline-studio-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-10.png)

![pipeline-studio-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-11.png)

You can delete a stage by activating **edit mode**and clicking **X** at the top right on the stage you want to delete.

![pipeline-studio-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-12.png)

After deleting, you can click **Save Pipeline** in the upper right corner to finalize the stage deletion.

### Run a pipeline

Pipelines can be run manually or automatically.

#### Manual run

Manual run allows you to run your pipeline when you want.

![pipeline-management-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-12.png)

In **Pipeline Management**, click **▶ Run︎**, and when the **Run Pipeline** modal window appears, check out the contents and click **Confirm**.

#### Autorun

Autorun lets you configure your pipeline to run automatically when an event occurs in your GitHub or GitLab repository or when a container image in your image registry is updated.

![management-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-04.png)
![management-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-05.png)

Click **Autorun Settings**, and then click **Add** in the **Autorun Settings** modal pane.


* Setting up GitHub autoruns
![management-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-06.png)



You can use the GitHub webhook to set up a pipeline to run automatically when an event occurs in a repository on GitHub or GitHub Enterprise. Set the **autorun type** to **GitHub**, enter the repository's **organization name or username**, **project name**, **branch or tag**, and **secret**, and click OK.

To set up an autorun with a tag, enter the tag name in the **branch or tag** entry, such as `refs/tags/tagname`. You can use a JAVA regular expression for the `tag name` part.

After setting up autorun with tags, builds are performed with the tags set when using the NHN Cloud build tool. To perform builds with tags in the Build - Jenkins stage, you need to set the following settings.

Set the parameters in Jenkins as follows.
![pipeline-guide-39.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-39.png)
![pipeline-guide-40.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-40.png)


In Pipeline's build tool settings, in the **Build Job Parameter**, enter the following

![management-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-10.png)

* GitHub Webhook Settinig Values

![pipeline-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-16.png)


| Item | Setting value |
|---|---|
| Payload URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | The value entered in the secret of the pipeline autorun settings |
| event | push event, create event(When using tags) |

You can set certain files to autorun only when they are pushed (up to 5).

![management-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-13.png)

**Source repository name**selects the source repository you registered with in Preferences.
**GitHub file path is** the path that contains the file in the selected source repository.

* GitLab Autorun Settings

![management-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-07.png)

You can use the GitLab webhook to set up a pipeline to run automatically when an event occurs in your GitLab repository. Set the **autorun type** to **GitLab**, enter the repository's **organization or username**, **project name**, **branch, or tag**, and click **Confirm**. Support for setting GitLab secrets is coming in the future.

* Set up a webhook in the GitLab repository.

![pipeline-guide-18](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-18.png)


| Item | Setting value |
|---|---|
| URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Select Push events |
| Secret | Do not set |
| SSL verification | Select Enable SSL verification |

* Precautions for GitLab Webhook settings

When setting autorun with GitLab's user name, make sure to set the user name to be the same as GitLab's user name. If the user name is set differently, autorun may not work.

![pipeline-guide-19](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-19.png)

* Image Repository Autorun Setting

![management-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-08.png)

If you want the pipeline to run automatically when the container image is updated, set **Image Registry** for **Autorun Type**.
After selecting **the image registry** registered in **the environment settings**, enter **Image Name**. Enter the image name in the form of `registry name/image name` for NHN Cloud container registry.
For Docker Hub, enter in the form of `docker hub account/image name`. **Tag** can use JAVA regular expression and is automatically executed when a tag matching the entered tag is pushed.
If you do not enter a tag, it will be automatically executed when a new tag except latest is pushed.
When finished, click **Confirm**.

![management-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-09.png)

When you create a new pipeline, the toggle switch for **autorun** is off. To run the pipeline automatically, you must click the **Auto-run** toggle switch to enable it. 

### Manage a pipeline

Users can modify basic information in the pipeline.
![pipeline-studio-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-13.png)

You can edit the name and description of a pipeline by clicking the edit icon next to the pipeline name.

After you edit the information, you can click **Confirm** to finalize your edits.

![pipeline-studio-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-14.png)

You can click **▶ Manual Run** to run the pipeline, or **■ Stop Running** to stop a pipeline that is running.


#### View recent execution information

To view basic information about the pipeline's most recent run and the status of the run for each stage, click **Recent Run Details**.

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-16.png)

#### Modify and Download Pipeline JSON
You can modify the JSON to change the pipeline. 

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-15.png)

You can view the pipeline in JSON format by clicking **Pipeline Version**.

You can view by modification date by clicking the drop-down button in the top left that shows the pipeline modification date.

You can save it as a JSON file by clicking **Download Pipeline Template**in the top right corner.

You can click **Edit** to modify the JSON file directly on the screen.
