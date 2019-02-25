# google-earth-webvr

*Set-up*

Clone the repository 
`git clone https://github.com/AustinDevs/google-earth-webvr.git`

Run `yarn init` and `yarn install` to install dependencies.

Add the earth-reverse-engineering repo by running `yarn add retroplasma/earth-reverse-engineering`


Navigate into the google-earth-webvr repo you cloned and run  `node ./node_modules/earth-reverse-engineering/lat_long_to_octant.js {lat} {long}` to obtain octants of the particular latitude and longitude you are examining.  For example to find the octants of (30.274701, -97.740341), run `node ./node_modules/earth-reverse-engineering/lat_long_to_octant.js 30.274701 -97.740341`.

Octants 1-18 should be returned as objects within the command line.  In addition for each octant there is a number returned with the same number of digits as the octant level.

Run `node dump_obj.js {number returned} {octant level}` 
For example, for octant 13, run `node dump_obj.js 2053525261515 13`.


*Troubleshooting*  
