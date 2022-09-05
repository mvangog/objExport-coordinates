# objExport-coordinates
mvba to prevent microstation obj-exporter from moving the origin of the model

when export a design to .obj in microstation, the default exporter decides on an originpoint for the obj-file.
when no objects are selected in the designmodel, the origin of the obj-file will be the center of the bounds of the model-contents.
when one or multiple objects are selected, the origin of the obj-file will be the center of the bounds of the selected objects. (the selected objects have to be in view to be included in this functionality)

<h2>what this tool does</h2>
when the export-obj dialog is opened, this tool will create a pointElement at position 0,0,0 and select it.
this way, the exporter will use 0,0,0 as originpoint for the obj-file.
next, it calls for a "Fit View" to make sure the pointElement will be used for determining the originpoint.

when the export-obj dialog is closed, the oint is removed and the viewarea is restored to the way it was before the export.

<h2>how to set it up</h2>
place the mvba in the vba-folder

option 1: using a keyin
  use the keyin: vba run [objRD_export]ForcedOrigin.ExportOBJ
option 2:
  add the mvba to the ConfigVariable MS_VBAAUTOLOADPROJECTS
  now this tool will run every time you use the export-obj function without needing to use a key-in.
