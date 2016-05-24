# Google-Cloud-Messaging-Library
A library that makes Google Cloud Messaging simple.

### How to install:
1) Copy gcm package into your project and add [this config](https://developers.google.com/cloud-messaging/android/start) to the 'app' directory.

2) Permissions: (Notice where you should insert you package name)

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.GET_ACCOUNTS"/>
<uses-permission android:name="android.permission.WAKE_LOCK"/>
<permission android:name="<YOUR PACKAGE NAME>.permission.C2D_MESSAGE" android:protectionLevel="signature"/>
<uses-permission android:name="<YOUR PACKAGE NAME>.permission.C2D_MESSAGE"/>
<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE"/>
```


3) Registrations (in manifest file):

```xml
<service android:name=".gcm.GcmRegistrationService"/>
```
```xml
<service android:name=".gcm.GcmMessageListener" android:exported="false">
	<intent-filter>
		<action android:name="com.google.android.c2dm.intent.RECEIVE"/>
	</intent-filter>
</service>
```
```xml
<receiver android:name="com.google.android.gms.gcm.GcmReceiver" android:exported="true" android:permission="com.google.android.c2dm.permission.SEND">
  <intent-filter>
  	<action android:name="com.google.android.c2dm.intent.RECEIVE"/>
  
  	<category android:name="<YOUR PACKAGE NAME HERE>"/>
  </intent-filter>
</receiver>
```

And you should be good to go.

### How to use: