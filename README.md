# Ex.No:3a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.


## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
1.Start the application. MainActivity launches and activity_main.xml is loaded using setContentView().

2.Initialize the views: get the text field (etUrl) and the two buttons (btnImplicit, btnGmail) using findViewById().

3.Set the click listeners on both buttons using setOnClickListener(), so the app waits for the user to tap.

4.Read the input: when the user taps Implicit Intent, read the website address from the text field (default www.gmail.com). Check that it is not empty, and add https:// if it is missing.

5.Create the implicit intent: build new Intent(Intent.ACTION_VIEW, Uri.parse(url)). Only the action (VIEW) and the data (URL) are given, with no target class named.

6.Start the activity: call startActivity(intent). Android searches for an app whose intent filter matches (usually a browser) and opens it. If none is found, ActivityNotFoundException is caught and a Toast is shown.

7.Display the result and stop: the browser opens the Gmail page, and the user can press Back to return to the app.


## PROGRAM:
```
/*
Program to print the text “Implicitintent”.
Developed by: MAHALINGA JEYANTH V
Registeration Number : 212224220057
*/
```
ACTIVITY MAIN.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/background"
    android:fillViewport="true">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">

        <!-- Header -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="@drawable/bg_header"
            android:gravity="center"
            android:orientation="vertical"
            android:paddingTop="48dp"
            android:paddingBottom="56dp">

            <ImageView
                android:layout_width="72dp"
                android:layout_height="72dp"
                android:contentDescription="@string/web_icon"
                android:src="@drawable/ic_web" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginTop="12dp"
                android:text="@string/implicit_intent"
                android:textColor="@color/white"
                android:textSize="26sp"
                android:textStyle="bold" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginTop="4dp"
                android:text="@string/open_a_website_using_an_implicit_intent"
                android:textColor="@color/text_light"
                android:textSize="14sp" />
        </LinearLayout>

        <!-- Card -->
        <com.google.android.material.card.MaterialCardView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginStart="20dp"
            android:layout_marginTop="-32dp"
            android:layout_marginEnd="20dp"
            app:cardBackgroundColor="@color/white"
            app:cardCornerRadius="20dp"
            app:cardElevation="8dp">

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                android:padding="20dp">

                <com.google.android.material.textfield.TextInputLayout
                    android:id="@+id/tilUrl"
                    style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:hint="@string/website_address"
                    app:boxCornerRadiusBottomEnd="12dp"
                    app:boxCornerRadiusBottomStart="12dp"
                    app:boxCornerRadiusTopEnd="12dp"
                    app:boxCornerRadiusTopStart="12dp"
                    app:endIconMode="clear_text"
                    app:startIconDrawable="@android:drawable/ic_menu_search">

                    <com.google.android.material.textfield.TextInputEditText
                        android:id="@+id/etUrl"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:imeOptions="actionGo"
                        android:inputType="textUri"
                        android:maxLines="1"
                        android:text="@string/default_url" />
                </com.google.android.material.textfield.TextInputLayout>

                <com.google.android.material.button.MaterialButton
                    android:id="@+id/btnImplicit"
                    android:layout_width="match_parent"
                    android:layout_height="58dp"
                    android:layout_marginTop="24dp"
                    android:text="@string/implicit_intent"
                    android:textAllCaps="false"
                    android:textSize="17sp"
                    app:backgroundTint="@color/primary"
                    app:cornerRadius="14dp"
                    app:icon="@android:drawable/ic_menu_send"
                    app:iconGravity="textStart" />

                <com.google.android.material.button.MaterialButton
                    android:id="@+id/btnGmail"
                    style="@style/Widget.MaterialComponents.Button.OutlinedButton"
                    android:layout_width="match_parent"
                    android:layout_height="58dp"
                    android:layout_marginTop="12dp"
                    android:text="@string/open_gmail"
                    android:textAllCaps="false"
                    android:textColor="@color/gmail_red"
                    android:textSize="17sp"
                    app:cornerRadius="14dp"
                    app:strokeColor="@color/gmail_red"
                    app:strokeWidth="2dp" />
            </LinearLayout>
        </com.google.android.material.card.MaterialCardView>

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="24dp"
            android:gravity="center"
            android:text="@string/picker_hint"
            android:textColor="@color/text_grey"
            android:textSize="13sp" />
    </LinearLayout>
</ScrollView>
```
ACTIVITY MAIN.JAVA:
```
package com.example.implicitintent1;

import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.text.Editable;
import android.util.Patterns;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;


import com.google.android.material.button.MaterialButton;
import com.google.android.material.textfield.TextInputEditText;
import com.google.android.material.textfield.TextInputLayout;

public class MainActivity extends AppCompatActivity {

    private TextInputLayout tilUrl;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        tilUrl = findViewById(R.id.tilUrl);
        TextInputEditText etUrl = findViewById(R.id.etUrl);
        MaterialButton btnImplicit = findViewById(R.id.btnImplicit);
        MaterialButton btnGmail = findViewById(R.id.btnGmail);

        // Opens whatever is typed in the text field (default: www.gmail.com)
        btnImplicit.setOnClickListener(v -> {
            Editable text = etUrl.getText();
            String url = text != null ? text.toString().trim() : "";
            openWebsite(url);
        });

        // Always opens www.gmail.com
        btnGmail.setOnClickListener(v -> openWebsite("www.gmail.com"));
    }

    private void openWebsite(String url) {
        tilUrl.setError(null);

        if (url.isEmpty()) {
            tilUrl.setError("Enter a website address");
            return;
        }

        String formattedUrl = (url.startsWith("http://") || url.startsWith("https://")) ? url : "https://" + url;

        if (!Patterns.WEB_URL.matcher(formattedUrl).matches()) {
            tilUrl.setError("Enter a valid website address");
            return;
        }

        try {
            // Implicit intent: we only say WHAT to do (VIEW) and WHICH data (URL).
            Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(formattedUrl));
            startActivity(intent);
        } catch (ActivityNotFoundException e) {
            Toast.makeText(this, "No app found to open this link", Toast.LENGTH_LONG).show();
        }
    }
}
```
ANDROID MANIFEST.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.ImplicitIntent1">
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:windowSoftInputMode="adjustResize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## OUTPUT
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/f8083c3b-77a7-461c-9ca3-c8e2066a0384" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/087adc24-3a8c-4b14-9089-2809451d6a24" />



## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


