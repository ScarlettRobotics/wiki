# 3D Printer

!!!info 3d Printer Rules
1. All 3d print files must be in stl format and brought to a senior to be sliced and printed
2. Personal prints will cost 10&#162; per meter of filament used
3. Failure to comply with these rule will result in loss of 3d printer privileges
!!!
## Finding a file to print and slicing
Ensure the file is stl. Import the file into a slicer along with any other files you would like to print. The preferred slicer for the Monoprice printer is IIIP Cura a python based Cura version. If any other 3d printers have been obtained use Prusa3d slicer.

## Ensuring printer is prepared for printing
Please make sure the following settings are set in the IIIP Cura software:

==- Basic Settings
### Quality
* **Layer Height (mm):** 0.1
* **Shell Thickness (mm):** 1.2
* **Enable Retraction:** yes
### Fill
* **Bottom/Top thickness (mm):** 0.6
* **Fill Density (%):** 90
### Speed and Temperature
* **Print Speed (mm/s):** 50
* **Printing Temp (C):** 195
* **Bed Temp (C):** 50
### Support
* **Support Type:** Change as needed. 
    * *Touching* buildplate if no overhang above model. 
    * *Everywhere* if overhang above model
* **Platform Adhesion type:** 
    * *Brim* for less expansive prints. 
    * *Raft* for large and sensitive prints.
### Filament
* **Diameter (mm):** Change as Needed
* **Flow (%):** 100.0    
===
==- Advanced Settings
### Machine
* **Nozzle size (mm):** 0.4
### Retraction
* **Speed (mm/s):** 40.0
* **Distance (mm):** 7
### Quality
* **Initial Layer Thickness:** 0.3
* **Initial Layer Line Width (%):** 100.0
===
