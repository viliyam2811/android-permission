Prompt for Permission in Android app
Create one project in Android Studio.
give name Getperm
give package name com.exapmle.getperm

Add permission in AndroidManifest.xml file
<code>
  
  <?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.getperm">

    <uses-sdk
        android:minSdkVersion="12"
        android:targetSdkVersion="27" />

    <uses-permission android:name="android.permission.READ_CONTACTS"/>

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
  
<code>
  
2. Add code in MainActivity.java
<code>
package com.example.getperm;

import android.Manifest;
  
import android.content.DialogInterface;
  
import android.content.pm.PackageManager;
  
import android.support.annotation.NonNull;
  
import android.support.v4.app.ActivityCompat;
  
import android.support.v4.content.ContextCompat;
  
//import android.support.v7.app.AlertDialog;
  
import android.support.v7.app.AppCompatActivity;
  
import android.os.Bundle;
  
import android.view.View;
  
import android.widget.Toast;

public class MainActivity extends Activity {
  
    private int CONTACTS_PERMISSION_CODE = 1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        if (ContextCompat.checkSelfPermission(MainActivity.this, Manifest.permission.READ_CONTACTS) == PackageManager.PERMISSION_GRANTED) { 
            Toast.makeText(MainActivity.this, "You have already granted this permission!", Toast.LENGTH_SHORT).show(); 
        } else { 
            ActivityCompat.requestPermissions(this, new String[] {Manifest.permission.READ_CONTACTS}, CONTACTS_PERMISSION_CODE); 
        }
    }
}
</code>
