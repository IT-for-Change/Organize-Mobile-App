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


#### Common errors and things to look out for: 

1. Cordova - Current working directory is not a Cordova-based project 

	$\to$ Make sure you have www folder in root directory. 

2.  [ERROR] Could not parse build output file: `platforms/android/app/build/outputs/apk/debug/output.json`

	$\to$ Downgrade Ionic CLI to 5.4.16 
			
3. FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed - JavaScript heap out of memory
	$\to$ `export NODE_OPTIONS="--max-old-space-size=8192"`
	This command simply increases the maximum allowed memory for Node. Add it to ~/.bashrc so that you dont have to execute it on every build. 
4.  Error : ```Cannot find symbol import com.google.firebase.iid.FirebaseInstanceIdService
						app:compileDebugJavaWithJavac FAILED```
						$\to$ Install the Firebase plugin with  `cordova plugin add cordova-plugin-firebasex`
5. Task :app:checkDebugAarMetadata FAILED 
$\to$ Add ```implementation ("androidx.browser:browser:1.3.0"){
         force = true
         } ``` under android dependencies in app-level build.gradle. 
7.  In general,  if you get a generic error during building, try running `./gradlew --debug` or `./gradlew --info` for more verbose error. 
8. After plugin updates, try removing and adding the android platform using `cordova platform rm android` and `cordova platform add android` (Don't forget to make the changes in `build.gradle` and `google-services.json` after reinstalling the platform)

