## Steps for Slide Seq image to Nissl image registration

### Sample data
- A pair of nissl and slide seq images : https://drive.google.com/drive/folders/1ggUoXABG-rOzSkb2LF0Y1FIUsbFvPhfI?usp=sharing

### Prerequisite tools and preparation before alignment and registration

- Install Slicer 3D from https://www.slicer.org/
- Install Slicer IGT plugin - use UI in slicer to select and install slicer IGT plugin
- Identify folder to store selected fiducials and computed transforms in Part A
- Identify folder to store selected fiducials in Part B

### Part A: Rigid Alignment and Scaling (captioned video of steps - https://drive.google.com/file/d/1NusdmuQydeaQ7dHsnvSeB-1DauQjhiL5/view?usp=sharing )

#### Setup
- Load nissl and slide-seq images into Slicer for initial nissl/slide-seq alignment by dragging and dropping the files into the main view area. Select "Any Data" option in the pop up dialog.
- Goto side by side view
- For `Red` view on left select slide-seq image, and for `Yellow` view on right select nissl image
- Select axial orientation for both `Red` and `Yellow` views
- Test panning and zooming - by holding down shift and control, respectively
- Adjust field of view in both red and yellow views
- Start IGT plugin's fiducial registration wizard

#### Identifying fiducial positions
- Rename fiducials to `{id}_ff` and `{idf}_tt`, indicating `from` and `to` fiducials, respectively
- Enable multiple fiducials by clicking on checkbox
- Mark 3 `from` fiducials on slide_seq image
- Mark 3 `to` fiducials on nissl image

#### Creating transform
- Create new transform as `{id}_t3a`
- Set result transform type to "Similarity"
- Set point matching method to "Manual"
- Set Auto-update as checked
- Preview transform by selecting slide-seq image and clicking "Apply"
- On nissl image (Yellow view), add slide seq view and verify that images are aligned approximately

#### Saving transform and fiducials
- Click save icon on top left of Slicer UI
- Keep checked fiduial files
- Keep checked transform file and change type to txt
- Uncheck all other files 
- Adjust save location of fiducial files to a local folder named `s3a_fiducials`
- Adjust save location of transform file a local folder named `s3b_fiducials`
- Click save

#### Upload all saved data to Google bucket folder
- Upload fiducials to `macosko_data/mraj/mouse_atlas_data/s3_registered_ss/{your_name}/s3a_fiducials`
- Upload transforms in `macosko_data/mraj/mouse_atlas_data/s3_registered_ss/{your_name}/s3a_transforms`

### Generating transformed images
- Generation of transformed images will be done by Mukund using transform files saved in in Part A
- Transformed images are needed for Part B

### Part B: Fiducial based Registration (captioned video of steps - https://drive.google.com/file/d/1PAIXPLhOy2_aisT25czthtl7FTyF3-SW/view?usp=sharing )

#### Setup
- Download transformed images from Google bucket folder `macosko_data/mraj/mouse_atlas_data/s3_registered_ss/s3a_ss_imgs`
- Load nissl (same image as used in part A) and transformed slide seq images (from downloaded folder) into Slicer for nissl/slide-seq registration by dragging and dropping the files into the main view area. Select "Any Data" option in the pop up dialog.
- Goto side by side view
- For `Red` view on left select slide-seq image, and for `Yellow` view on right select nissl image
- Select axial orientation for both `Red` and `Yellow` views
- Test panning and zooming - by holding down shift and control, respectively
- Adjust field of view in both red and yellow views
- Start IGT plugin's fiducial registration wizard

#### Identifying fiducial positions
- Rename fiducials to `{id}_f` and `{idf}_t`, indicating `from` and `to` fiducials, respectively (Note just sigle f as suffix as opposed to double f suffix in part A)
- Enable multiple fiducials by clicking on checkbox
- Mark `from` fiducials on slide_seq image, ideally 3 at a time.
- Mark `to` fiducials on nissl image, ideally 3 at a time.

#### Creating transform
- Create new transform as `{id}_t3b`
- Set result transform type to "Warping"
- Set point matching method to "Manual"
- Set Auto-update as checked
- Preview transform by selecting slide-seq image and clicking "Apply"
- On nissl image (Yellow view), add slide seq view and verify that images are aligned approximately
- Adjust `{id}_t` fiducials if needed (Remember to uncheck "new marker placement" before adjusting existing markers).
- Add new fiducials if needed.

#### Saving transform and fiducials
- Click save icon on top left of Slicer UI
- Keep checked fiduial files
- Keep checked transform file and change type to txt
- Uncheck all other files 
- Adjust save location of fiducial files to a local folder named `s3b_fiducials`
- Change type of fiducial files to fiducial csv
- Click save

