conNode.js® is a free, open-source, cross-platform JavaScript runtime environment that lets developers create servers, web apps, command line tools and scripts.

## Getting started
Every file in javascript is considered a module and one can export the  functions and variables from one file and use them in another file. This will be shown in the example below:
mind-grainer.js
```
const programmer = "Jupiter";
const cybersec = "Nebula";

modules export = {programmer, cybersec};
```
app.js file:
In app.js file we:
```
const userProfiles = require("./mind-grainer.js");
console.log(userProfiles); //this returns an object
console.log(userProfiles.programmer); // returns programmer assigned value
console.log(userProfiles.cybersec); //returns cybersec assigned value
```
## built-in-node modules
os module :
The operating system  (os) node module provides functions that can be used to get information on the operating system and the device.
To start:
```
const os = require("node:os");
// by just pressing the os. **it****** displays the list of functions available 
console.log(os.userinfo());
```