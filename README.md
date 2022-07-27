Organize
=========


### About Organize

The *Organize* mobile app is for community organizations.

### Documentation

#### Setup project 

1. Download and setup [NVM](https://github.com/nvm-sh/nvm) 

2. For the project we will be using node version 14.15.0
		
		nvm install 14,15.0  
	    nvm use 14.15.0
	    
 3. Install Node Modules

    	npm install 
	    
3. Generate icons

	    npm i -g cordova-res
	    cordova-res
	    
4. Add Firebase plugin 

	    cordova plugin add cordova-plugin-firebasex

#### Building the app for Android

  1. Add the android platform to the project

		  cordova platform add android 

  2. For Firebase notification integration, update `google-services.json` and `build.gradle` (both app level and project level) with those provided by Firebase (when you add an app). 
	  

	      rm ~/Organize-Mobile-App/platforms/android/app/ && mv /path/to/new/google/services/json/ ~/Organize-Mobile-App/platforms/android/app/src
		Add the following in `Organize-Mobile-App/platforms/android/build.gradle` (project level build.gradle)

		  buildscript {
		  repositories {
		  ...
		  dependencies { 
		  ...
		  // Add this line
		  classpath 'com.google.gms:google-services:4.3.13'
		  }
		  }
	
		Add the following in `Organize-Mobile-App/platforms/android/app/build.gradle` (app level build.gradle)
		
		 apply plugin:  'com.android.application'
		 // Add this line  
		 apply plugin:  'com.google.gms.google-services'
		 ...
		 android {
	     dependencies {
	     //Add the following dependencies 
		 implementation platform('com.google.firebase:firebase-bom:30.3.1')
		 implementation ("androidx.browser:browser:1.3.0"){
         force = true
         } 
	     }
   
3. Now run `ionic cordova run android` from the root folder while an android device is attached to the laptop with MTP enabled. 





