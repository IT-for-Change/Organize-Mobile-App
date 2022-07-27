Organize
=========


### About Organize

The *Organize* mobile app is for community organizations.

### Documentation

#### Setup project 

1. Download and setup NVM : https://github.com/nvm-sh/nvm

2. For the project we will be using node 14.15.0

    nvm use 14.15.0
    npm install 
    npm i -g cordova-res
    cordova-res

    mkdir www
    cordova plugin add cordova-plugin-firebasex
    cordova platform add android
    
    Add google-services.json
    Change build.gradle (app and project level) 
    
   
For Firebase Notification integration : 

Add google-settings.json file from Firebase project console
Add 	classpath 'com.google.gms:google-services:4.3.13' in project level build.gradle 
Add   implementation platform('com.google.firebase:firebase-bom:30.2.0')
      implementation ("androidx.browser:browser:1.3.0"){
        force = true
      } 
    
      in app level build.gradle. (Make sure to add in Android dependencies section and not Buildscript dependencies) 
  
Add   apply plugin: 'com.google.gms.google-services' in app level build.gradle. (At the start) 


Common Errors : 

1. Cordova - Current working directory is not a Cordova-based project 

Make sure you have www folder in root directory. 

2. [ERROR] Could not parse build output file: platforms/android/app/build/outputs/apk/debug/output.json

Downgrade Ionic CLI to 5.4.16 

3. 




