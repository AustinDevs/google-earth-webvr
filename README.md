# google-earth-webvr


https://github.com/retroplasma/earth-reverse-engineering


### Set-up

* Clone the repository 
`git clone https://github.com/AustinDevs/google-earth-webvr.git`

* Run `yarn init` and `yarn install` to install dependencies.

* Add the earth-reverse-engineering repo by running `yarn add retroplasma/earth-reverse-engineering`


* Navigate into the google-earth-webvr repo you cloned and run  `node ./node_modules/earth-reverse-engineering/lat_long_to_octant.js {lat} {long}` to obtain octants of the particular latitude and longitude you are examining.  
      * For example to find the octants of (30.274701, -97.740341), run `node ./node_modules/earth-reverse-engineering/lat_long_to_octant.js 30.274701 -97.740341`.

* Octants 1-18 should be returned as objects within the command line.  In addition, for each octant there is a number returned with the same number of digits as the octant level.

* Run `node ./node_modules/earth-reverse-engineering/dump_obj.js {number returned} {octant level}` 
For example, for octant 13, run `node ./node_modules/earth-reverse-engineering/dump_obj.js 2053525261515 13`. 
The command line should now indicate that 2053525261515 was found and downloaded.

* When you open the repo in your code editor, you should see it within downloaded_files.  

* We will be using A-Frame https://aframe.io/ which is a web framework based upon HTML for building virtual reality experiences.  More specifically, we will use the gtlf model primitive to display the 3D glTF model we downloaded: https://aframe.io/docs/0.9.0/primitives/a-gltf-model.html

* The object must be centered properly by running `node ./node_modules/earth-reverse-engineering/center_scale_obj.js downloaded_files/obj/22053525261515-13-823`

* Run  `node ./node_modules/earth-reverse-engineering/center_scale_obj.js downloaded_files/obj/22053525261515-13-826/model.obj downloaded_files/obj/22053525261515-13-823/model.2.obj`

* This will save the new centered object as model.2.obj.

* Open Blender (free and open source download: https://www.blender.org/)  We will use this software to make some edits to the file for improved VR viewing purposes.

Navigate to File -> Import -> Wavefront (obj). Import the downloaded file from above.  You'll likely see a very odd view.  Click on view in bottom left corner and change to see from bottom, top, etc.

* Click on Add -> Lamp -> Hemi.  Then click on the little ball icon to the right of Object Mode and click on "Rendered".  Now the image will show up properly.  You can save the rendered file by clicking File -> Export.  

* Now you will be  using the object-to-gltf model as mentioned above.  
Run  `yarn add obj2gltf`  
`npx obj2gltf -i downloaded-files/obj/22053525261515-13-823/{rendered file save in previous step}`
    * Example: `npx obj2gltf -i downloaded_files/obj/2053525261515-13-823/model.3.obj -o downloaded_files/obj/2053525261515-13-823/model.3.gltf`

* Add link into the source tag in index.html.  Yarn start to open in 3D VR environment.

### Troubleshooting
