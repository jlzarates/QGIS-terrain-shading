# QShader: a QGIS plugin for modelling natural illumination over digital terrain models. 

**Current version: 0.1**

**Supported QGIS version: 3.x**

**Repository and download: [github.com/zoran-cuckovic/QGIS-raster-shading](https://github.com/zoran-cuckovic/QGIS-raster-shading)**

## Installation

The algorithm is available in the official QGIS plugin repository and can be installed as usual (In QGIS go to Plugins -> Manage and install … ). Be sure to enable experimental plugins. 

If the standard installation does not work, the plugin can be downloaded for the repository (above) and installed manually: 
First you need to locate your QGIS plugins folder. On Windows it would be ‘C:\users\username\AppData\Roaming\QGIS\QGIS3\profiles\default\python\plugins’ (do a file search for ‘QGIS3’ …)

Plugin code can then be extracted in a new folder inside the plugins folder (you should name the folder QShader). Take care that the code is not inside a subfolder - the folder structure should be like this:

    QGIS3\profiles\default\python\plugins\
        [some QGIS plugin folders…]
        QShader
            dem_shading.py
            metadata.txt
            [other files and folders…]


Finally, there is a version made as QGIS script, which can be downloaded [here](_____) and installed as a QGIS script. 

## Manual

*Data input* for the plugin should be a digital elevation model (DEM) in raster format. Note that it has to be **projected in a metric coordinate system**. 

*Sun direction* marks the horizontal position of the Sun where 0° is on the North, 90° on the East and 270° on the West.

*Sun angle* marks the vertical position of the Sun. 

Two *analysis types* are available. The *shadow depth* will calculate the vertical difference between shadow surface and underlying terrain, while the *shadow length* will calculate the horizontal reach of the shadow. The reach is expressed as horizontal distance and not as slope length from the occlusion point to shadow tip.    

*Data output* is in the same raster format as the input dataset. Illuminated areas, i.e. thous without shadows, are assigned "NoData" value for shadow depth model. 


## Remarks 

For cartographic uses, the best result is achieved when varying levels of transparency according to shadow depth or length. You can download and apply a QGIS style definition files from [Style library on GitHub repository](https://github.com/zoran-cuckovic/QGIS-raster-shading/tree/styles).
REPO / FILE  ?raw=true

The algorithm output may contain some sharp transitions or visible artefacts, especially when made for rugged terrain, over noisy elevation models, such as Lidar data, or over small scale models of urban architecture. A simple 3x3 average (smoothing) filter should be applied in these cases.  


## More information

You can signal an issue [on GitHub](https://github.com/zoran-cuckovic/QGIS-raster-shading/issues).

For further information see also: [LandscapeArcaheology.org/2019/qgis-shadows](https://LandscapeArchaeology.org/2019/qgis-shadows/).