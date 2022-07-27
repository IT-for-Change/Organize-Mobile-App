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

