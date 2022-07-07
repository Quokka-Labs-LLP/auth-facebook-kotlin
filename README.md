# Facebook login module

Features:
Facebook Login and Get User Details

To import this module, First download it.
Now open your project in which you want to use this module.

Goto File -> New -> Import Module
Select the source directory of the Module you want to import and click Finish.
Open Project Structure Dialog (You can open the PSD by selecting File > Project Structure) and from the left panel click on Dependencies.
Open the Dependencies tab.
Click on <All Module> now in right side you will see add dependencies tab.
Click the (+) icon from Dependencies section and click Module Dependency.
Add Module Dependency dialog will open, Now select app module and click Ok.
Then you will see another Add Module Dependency dialog and it will show you facebooklogin module. Click on CheckBox then click ok.
Open your build.gradle file and check that the module is now listed under dependencies as shown below. 
implementation project(path: ':facebooklogin')

After Successfully importing facebooklogin module, Now let's implement it.

Create app in https://developers.facebook.com and add product Facebook Login (setup app).
Goto  Settings -> Basic and copy App ID and App Secret.

Goto res -> values folder and open string.xml file.
Paste these lines and replace APP_ID and APP_SECRET.
<string name="facebook_app_id">APP_ID</string>
<string name="facebook_client_token">APP_SECRET</string>
Close string.xml file.

Now open AndroidManifest.xml file 
Paste these permission outside the application tag.

<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET"/>

Paste these lines outside the activity tag.
<meta-data android:name="com.facebook.sdk.ApplicationId" android:value="@string/facebook_app_id"/>
<meta-data android:name="com.facebook.sdk.ClientToken" android:value="@string/facebook_client_token"/>
Close AndroidManifest.xml file.

Open the Activity in which you want to implement Facebook Login.

implement FacebookLoginListener interface and import all function.

Inside onCreate function.
FacebookLogin.doFacebookLogin(this,this,this)
Respond to a login result, we need to register a callback.
//here we are initializing, adding LoginManager callback and setting up FacebookLoginListener.

Add performLogin function when we click on login with facebook button 
loginWithFacebook.setOnClickListener{
FacebookLogin.performLogin(this)
}

You will get user data inside onGetProfileSuccess(userData: JSONObject?). You can parse it as you like.
To see user data you can print userData.





