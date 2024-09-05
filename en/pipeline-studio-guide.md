## Dev Tools > Pipeline > Console User Guide > Pipeline Studio

### Pipeline Studio

Pipeline Studio is the page where users can manage basic information about their pipelines, or add, change, or delete the stages that make up a pipeline.

#### Manage a pipeline
![pipeline-studio-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-01.png)

At the top of Pipeline Studio, you'll see basic information about the pipeline: its name, description, last modified date, and creator.

In the Pipeline Studio panel, you can see the stages that make up that pipeline.

![pipeline-studio-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-02.png)

You can edit the name and description of a pipeline by clicking the edit icon next to the pipeline name.

After you edit the information, you can click **OK** to finalize your edits.

![pipeline-studio-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-03.png)

You can click **▶ Manual Run** to run the pipeline, or **■ Stop Running** to stop a pipeline that is running.

![pipeline-studio-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-04.png)

To view basic information about the pipeline's most recent run and the status of the run for each stage, click **Recent Run Details**. 

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-05.png)

You can view the pipeline in JSON format by clicking **Pipeline Version**.

You can view by modification date by clicking the drop-down button in the top left that shows the pipeline modification date.

You can save it as a JSON file by clicking **Download Pipeline Template**in the top right corner.

You can click **Edit** to modify the JSON file directly on the screen.

![pipeline-studio-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-06.png)

You can delete the pipeline by clicking **Delete Pipeline**.

### Check a stage
![pipeline-studio-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-07.png)

Click a stage to view stage information in the **Stage Settings** panel on the right side of the screen.

![pipeline-studio-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-18.png)

Click the buttons in the lower left to adjust the view of the stages that make up the pipeline. The buttons are described in the following order, from top to bottom

- Autosort
- Expand
- Collapse
- Auto scaling
- Lock

### Edit mode
![pipeline-studio-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-08.png)

You can enter edit mode by clicking the edit mode toggle in the top right corner. In the edit mode, you can add, change, delete, and reposition stages.

### Add a stage
![pipeline-studio-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-09.png)

When you enable **Edit Mode**, the left side exposes the **Source**, **Build**, **Deploy**, and **Feature** groups, which are organized into different stages that you can use to organize your application deployment flow.

You can select the stages you want to add from the four groups and drag and drop them onto the screen.

![pipeline-studio-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-10.png)

When a stage is added, select it to enter the required information.

![pipeline-studio-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-11.png)

Set the order of execution by concatenating the stages to run before and the stages to add.

Stages can run in parallel depending on how the previous stage is connected. If one of the stages in the parallel configuration fails, execution of the remaining stages is canceled and the pipeline execution fails.

![pipeline-studio-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-12.png)

You can click **Save Pipeline**in the top right corner to finish adding stages.

### Editing Stages
![pipeline-studio-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-13.png)

You can edit a stage by enabling **Edit Mode**and then clicking the stage you want to edit.

![pipeline-studio-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-14.png)

After you've finished editing, you can click **Save Pipeline** in the top right corner to finalize your stage edits.

### Delete a stage
![pipeline-studio-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-15.png)

![pipeline-studio-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-16.png)

You can delete a stage by activating **Edit Mode**and clicking **X** at the top right on the stage you want to delete.

![pipeline-studio-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-17.png)

After deleting, you can click **Save Pipeline** in the upper right corner to finalize the stage deletion.
