## Steps for Updating Fiducials in Slicer IGT Fiducial Registration Wizard

### Prerequisites needed

- Slicer 3D
- Slicer IGT plugin (used for initial registration as well)
- "From" and "To" fiducial files - "{id}_t.fcsv and {id}_f.fcsv files"
- "From" and "To" images to be aligned

### Steps

#### Loading images
- Open slicer 3D
- Load nissl and slide-seq images into Slicer for initial nissl/slide-seq alignment by dragging and dropping the files into the main view area. Select "Any Data" option in the pop up dialog.
- Goto side by side view
- For `Red` view on left select slide-seq image, and for `Yellow` view on right select nissl image
- Select axial orientation for both `Red` and `Yellow` views
- Test panning and zooming - by holding down shift and control, respectively
- Adjust field of view in both red and yellow views

#### Loading fiducials
- Start IGT plugin's fiducial registration wizard
- Select fiducial files in finder window and drag over to the slicer window
- In the drop down menu of Slicer IGT fiducial registration wizard (seen on the left), select the "from" and "to" fiducials
- Make sure that "place fiducial option" (indicated by red upward arrow) is not selected for either of fiducials
- Adjust views so that images and fiducials are visible

#### Adjusting fiducials
- Select and move fiducials as needed
- Add or remove fiducials as needed

#### Creating transform to verify new fiducial positions
- Create new transform as `Anyname`
- Set result transform type to "Warping"
- Set point matching method to "Manual"
- Set Auto-update as checked
- Preview transform by selecting slide-seq image and clicking "Apply"
- On nissl image (Yellow view), add slide seq view and verify that images are aligned approximately

#### Saving fiducials
- Click save icon on top left of Slicer UI
- Keep checked the fiduial files
- Uncheck all other files 
- Adjust save location of fiducial files to a local folder as needed
- Click save
