---
layout: post
title: "android notes"
description: ""
category:
tags: [android]
Time-stamp: "liuminzhao 02/02/2014 14:39:18"
---
{% include JB/setup %}

Android Course Notes
=====================

# Virtual Device

## Telnet

	telnet localhost 80
	sms send 111 hello
	power capacity 0
	help window
	window scale 0.5
	avd stop

New: 1507 Ram, 100 MB

# Resourse

Under `res/layout` , and `res/values`.

# Syntax

	&gt; = >
	&lt; = <
	&amp;

# Logcat #

	import android.util.Log
	Log.e('tag', 'msg')

Put them in main activity.xml

# ImageView

Put images in a new folder `media`, then copy needed to `res/drawable-mdpi`, then under `activity_main.xml`, grab `Palette/ImageView` to the main.

In xml file:

	<ImageView ...
	android:contentDescription = ""

Properties:

	scaleType = 'fitXY'
	adjustViewBounds = 'true'

# TextView

Properties:

	paddingLeft = '16dp'
	textSize = '16sp'
	paddingTop = '8dp'

# ID

	@+id/jkj: create
	@id/ : cite

# R.java

# Files

	activity_main.xml
	strings.xml

	MainActivity.java

# Layout-land (layout-landscape)

make new folder `layout-land` under `res`, and copy `activity_main.xml` in it.

# ScrollView

	layout_width = "match_parent"
	layout_height = "match_parent"
	layout_below = "@id/imageView1"

wrap TextView

## ScrollView + LinearLayout

	<ScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_below="@id/hearthstone"
        android:layout_margin="8dp"
        android:scrollbars="vertical" >

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="vertical" >

            <ImageView
                android:id="@+id/chicken"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_centerHorizontal="true"
                android:adjustViewBounds="true"
                android:layout_margin="8dp"
                android:src="@drawable/chicken" />

## HorizontalScroll + LinearLayout

	   <HorizontalScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_margin="8dp"
         >

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="horizontal" >

# Export

`manifest` -> `export wizard`.

Make new folder as `publish`

# Format

	cmd + a
	cmd + shift + f

# MediaPlayer

- Resources put in the folder `res/raw`

- Modify `Main...java`:

	onCreate:
	MediaPlayer mp = MediaPlayer.create(this, R.raw.ex...);
	mp.start();

## Life Cycle

	OnCreate()
	OnResume()
	OnPause()

Also need to define `MediaPlayer mp` under `MainActivity` before `OnPause`.

# Button

- add (drag)
- change property: on click (yourmethod)

		android:onClick="wiki"

- edit java file, under (yourmethod)

		public void wiki(View v){
		String url = "http://en.wikipedia.org/wiki/Jabberwocky";
		Intent i = new Intent(Intent.ACTION_VIEW);
		i.setData(Uri.parse(url));
		startActivity(i);
		}


# Debug

	Log.e("pickle", "onCreate")
	Import Log;

set `Breakpoint`. `Debug as`.

# Diagram

`onPause` -> `mp.stop();`, `mp.release()`

# Manifest

Under `Manifest`:

	config changes = "orientation|screenSize|uimode"

or

	android:screenOrientation = "portrait"

to avoid start background music again

# Style

under `values/styles.xml`.

	<style name = "mystyle" parent = "@android:style/TextAppearanceLarge"
	<item> ...

## Usage

	style = "@style/mystyle"

# Enable external android device to debug

`about phone` -> `build number` 7 times -> `usb debug enable`

# Webview

drag a `WebView` under `Composite`. Copy `html` file etc under `asset` folder

	android:id="@+id/webView1"
	android:layout_width="match_parent"
	android:layout_height="match_parent"/>

Modify your onCreate method to include the following two lines:

	WebView myWebView = (WebView) findViewById(R.id.webView1);
	myWebView.loadUrl("file:///android_asset/index.html");

Enable `zoom` controls

	myWebView.getSettings().setBuiltInZoomControls(true);
	myWebView.getSettings().setJavaScriptEnabled(true);
	mywebview.getSettings().setDomStorageEnabled(true);

Add new activity that is accessible from the Launcher, create a 3rd activity :

	Intent intent = new Intent();
	intent.setClass(this, YourFirstActivity.class);
	if (Math.random() > 0.5) {
	// Open the Java Book instead!
	intent.setClass(this, YourSecondActivity.class);
	}
	startActivity(intent);
	finish();

## Permission

`AndroidManifest.xml` -> `Permission` -> `uses internet`

# New activity

`file`, `new`, `others`, `android activity`.

Remember title and check laucher.

	 <activity
            android:name="com.vivigator.webviewapp.NasaActivity"
            android:label="@string/title_activity_nasa" >
                        <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

Can just delete the layout file and use previous one.

# Linear Layout

	<LinearLayout
		android:orientation = "vertical">

`vertical` or `horizontal`

# EditText

	<EditText
		android:hint = "full name">
		<requestFocus />
	</EditText>

request focus

	android:minLines = "3"


## `inputType`

	<EditText
		android:inputType = "textPersonName">
		textEmailAddress
		phone
		textMultiLine

# ImageButton

	<ImageButton
		android:onClick = "processForm" />

and add to `MainActivity.java`:

	public void processForm(View duck) {
		duck.setVisibility(View.INVISIBLE); // GONE ; make it disaapear
		Toast.makeText(this.getApplicationContext(), R.string.app_name, Toast.LENGTH_LONG).show;
		String email = mEmail.getText().toString();
			// .toLowerCase().contains("duck"); // contains gives T or F
		Toast.makeText(this.getApplicationContext(), email, Toast.LENGTH_LONG).show();
	}

`Toast` : print message

can set `android:layout_gravity = 'right'`;

and also

	android:layout_weight = "10"
	android:adjustViewBounds = "true" // to fill bounds

# view name

In java code:

	private EditText mName;

then in `onCreate`:

	mName = (EditText) findViewByID(R.id.name);
	mEmail = (EditText) findViewByID(R.id.email);

for general view

	private View mName;

then in `onCreate`:

	mName = findViewByID(R.id.name);

and it should be after `setContentView`

# Play with String

	int position email.indexOF("@");
	if (position == -1){
		Toast....
		mEmail.requestFocus();  // request focus
		return;
	}

	String username = email.substring(0, position);
	String thankyou = "Thankyou " + username;

	if ( ! email.contains("@")){
	}

	int len = comments.length();

	int value = Integer.parseInt(phone);

	name.equals("Fere")

# `try`

	int value = -1;
	boolean valueOK = false;
	try {
		value = ...;
		valueOK = true;
	} catch(Exception e){
		Log.d("fdsf", "fdjsfj");
	}

# animation

	Animation anim = AnimationUtils.makeOutAnimation(this, true)
	duck.startAnimation(anim);

# Share

## SEND

In `public void processForm` method:

	Intent i = new Intent(Intent.ACTION_SEND);
	i.setType("text/plain");
	i.putExtra(Intent.EXTRA_TEXT, "Whata");
	startActivity(i);

### SMS message

	Intent i = new Intent(Intent.ACTION_VIEW);
	i.setData(Uri.parse("sms:" + phone));
	i.putExtra("sms_body", coments);
	startActivity(i);

### Email

	Intent i = new Intent(Intent.ACTION_SENDTO, Uri.fromParts("mailto", "someone@somewhere", null));
	i.putExtra(Intent.EXTRA_SUBJECT, "important");
	i.putExtra(Intent.EXTRA_TEXT, message);
	startActivity(i);

	try{
	startActivity(i);
	} catch(Exception e) {
		Toast...
	}

	if (i.resolveActivity(getPackageManager()) = null) {
		Toast...
	} else {
	startActivity( Intent.createChooser(i, "choose email"));
	}

# ScrollView

Use `scrollview` to wrap linearlayout
