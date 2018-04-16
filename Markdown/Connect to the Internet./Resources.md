# Resources

## What is the res Directory?

The res directory is where you should put things such as images, strings, and layouts. It's included in every Android project, and you can see it in Android Studio here:


![Screenshot](https://d17h27t6h515a5.cloudfront.net/topher/2016/November/582f613d_screen-shot-2016-11-18-at-12.12.40-pm/screen-shot-2016-11-18-at-12.12.40-pm.png)


Inside of the res directory, are sub folder for the following types of resources. You may have a subset of these directories, depending on the types of resources you're using in your app. Here are some examples

### Different Resource Directories

This information can also be found [here](https://developer.android.com/guide/topics/resources/providing-resources.html).

#### Some Common Resource Types
| Name 	      | What's Stored Here          | 
| ------------- |:-------------:|
| values 	|XML files that contain simple values, such as string or integers | 
| drawable 	|A bunch of visual files, including Bitmap file types and shapes. More information is [here](https://developer.android.com/guide/topics/resources/drawable-resource.html)      | 
| layouts 	|XML layouts for your app   |


#### Other Resource Types
| Name 	      | What's Stored Here          | 
| ------------- |:-------------:|
| animator 	|XML files for property animations | 
| anim 		|XML files for tween animations      | 
| color 	|XML files that define state list colors   |
| mipmap 	|Drawable files for launcher icons  |
| menu 		|XML files that define application menus   |
| raw 		|Resource file for arbitrary files saved in their raw form. For example, you could put audio files here. (You might also be interested in the [assets folder](https://developer.android.com/reference/android/content/res/AssetManager.html), depending on how you use that audio)   |
| xml 		|Arbitrary XML; if you have XML configuration files, this is a good place to put them   |

## Why Resources

You should always keep things like images and layouts separate in the **res** folder. Keeping resource files and values independent helps you easily maintain them if you need to update, say, all your button images to match a new style. The Android Framework also easily allows for alternative resources that support specific device configurations such as different languages or screen sizes. Providing a customized experience for users from different locations or on different devices becomes increasingly important as more of the world comes online and more devices come on the market. We will see how to provide alternate resources for different configurations and locals later in this course.

## Using Resources in XML and Java

You've already seen resources in action. For example, in the `MainActivity`, you have already seen usage of resources. When we say `setContentView(R.layout.activity_main)`, we are referencing a resource (the `activity_main.xml`) file to use as the layout of `MainActivity`. That magical looking R.layout part of the expression above is actually a static class that is generated for us to reference resources in Java code. This is all described in the [Android Layouts Primer](https://classroom.udacity.com/courses/ud851/lessons/93affc67-3f0b-4f9b-b3a4-a7a26f241a86/concepts/cdbfd437-de24-4903-8f01-37c29427cb38).


### Working with strings.xml

In Java, you can get a String saved in **res** -> **values** -> **strings.xml** by calling the `getString` method. If you’re in an Activity, you can just call `getString`, and pass in the String resource ID. The String resource ID can be found in the **strings.xml** XML. For example, let's look at Sunshine's **strings.xml** file:

        <string name="today">Today</string>

        <!-- For labelling tomorrow's forecast [CHAR LIMIT=15] -->
        <string name="tomorrow">Tomorrow</string>

        <!-- Date format [CHAR LIMIT=NONE] -->
        <string name="format_full_friendly_date">
            <xliff:g id="month">%1$s</xliff:g>, <xliff:g id="day">%2$s</xliff:g>
        </string>

The id of the String with the value "Today" is `today` and the id of the String with the value `<xliff:g id="month">%1$s</xliff:g>, <xliff:g id="day">%2$s</xliff:g>` is `format_full_friendly_date`

If you wanted to reference the **Today** string, you would reference it in Java by doing something like this:

    String myString = getString(R.string.today);

In XML, you can access a String by using the @string accessor method. For the same String defined above, you could access it like this:

    <TextView text=”@string/today” />

For more information on String Resources check out the [documentation](https://developer.android.com/guide/topics/resources/string-resource.html).
