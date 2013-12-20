---
layout: post
title: "android notes"
description: ""
category:
tags: [android]
Time-stamp: "liuminzhao 12/20/2013 20:59:41"
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
