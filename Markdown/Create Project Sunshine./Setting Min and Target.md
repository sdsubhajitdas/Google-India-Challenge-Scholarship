<div class="index--container--2OwOl">

<div class="index--atom--lmAIo layout--content--3Smmq">

<div class="ltr">

<div class="index--markdown--2I2Ir ureact-markdown ">

# Android Min and Target Versions

Android 1.0 launched in 2008, and in just the 8 years since - there have been **13** new major platform releases. By convention, each release is named off of a sugary treat, and the releases are named alphabetically.

On the [Android Developer site](https://developer.android.com/about/dashboards/index.html#Platform), we show the relative percentage of active Android devices running a given platform version, also presented in this cool pie chart. Because pie charts are awesome.

![Chart](https://chart.googleapis.com/chart?chs=500x250&cht=p&chco=c4df9b%2C6fad0c&chl=Froyo%7CGingerbread%7CIce%20Cream%20Sandwich%7CJelly%20Bean%7CKitKat%7CLollipop%7CMarshmallow%7CNougat&chf=bg%2Cs%2C00000000&chd=t%3A0.1%2C1.3%2C1.3%2C13.7%2C25.2%2C34.1%2C24.0%2C0.3)

For our purposes though, you're really better off looking at it as a histogram.

![Graph](https://d17h27t6h515a5.cloudfront.net/topher/2016/November/58253ead_screen-shot-2016-11-10-at-7.43.52-pm/screen-shot-2016-11-10-at-7.43.52-pm.png)

If you squint, you can almost see a vaguely bell shaped curve, with the oldest releases on the left, their popularity dropping off as devices are upgraded or replaced. The largest proportion of devices are in the middle, representing devices about 2 years old. The newest platforms, which gain in popularity as new phones are released or updates go out, are on the right.

## Setting minSDK

The minSDK is the lowest SDK level that your app can run on. You can choose what level of devices to support. Setting the minSDK acts as a filter -- Google Play won’t show your app on devices running an Android platform version lower than your minimum SDK version.

So why not just set the minSDK to 1 and support everyone? Generally, you’ll want to target as many users as you can, but there's a cost associated with supporting older versions - things like creating different execution paths around deprecated or updated APIs, or presenting a different UX to devices with different features. You need to balance the opportunity of expanding your audience, with the cost of supporting those users.

Also remember that each release introduced new APIs and hardware support, so it may not make sense to make your app available to devices that don’t support your minimum feature set. Here are some examples of hardware support and features, tied to releases.

*   Home screen widgets (Cupcake)
*   Multiple finger tracking (Froyo)
*   Tablet (Honeycomb)
*   Android Beam (Jellybean)
*   Android TV, Auto, Wear (Lollipop)
*   Pro Audio (Marshmallow)

## Setting targetSDK

By comparison, the targetSDK is NOT a high pass filter -- it’s used only to declare which platform version you've tested your app on. An app targeted to a certain API or Android version will continue to be forward compatible on future releases -- the platform uses the target SDK values in case a future release makes a significant change to expected behavior, ensuring your app doesn’t break when a user’s phone gets upgraded. `

Android Studio by-default targets the latest release. If you’re developing a new app, there’s really no reason to target anything but the latest Android version, and once your app has been released, make it a point to update your target SDK and test as soon as possible when new platform releases roll out, so your app can take advantage of every new platform optimization and improvement.
