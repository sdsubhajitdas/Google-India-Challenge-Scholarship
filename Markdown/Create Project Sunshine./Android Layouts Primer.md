# Android Layouts Primer

You've learned about a lot of new terms that have to do with the Android UI. Here is a quick reference of these important concepts and how they work together. If you have never worked with a language like XML or HTML before and feel confused, you should head over to the [Android Basics class on Android Layouts](https://www.udacity.com/course/android-development-for-beginners--ud837) class and take the first lesson.

## Activities and Layouts

An **activity** is a single focused thing that the user can do. Activities are responsible for creating the window that your application uses to draw and receive events from the system. Activities are written in Java, extending from the Activity class.

An activity creates **views** to show the user information, and to let the user interact with the activity. Views are a class in the Android UI framework. They occupy a rectangular area on the screen and are responsible for drawing and handling events. An activity determines what views to create (and where to put them), by reading an XML layout file. These XML files, as Dan mentioned, are stored in the **res folder** inside the folder labeled **layouts**.

![Project View](https://d17h27t6h515a5.cloudfront.net/topher/2016/November/5827ad17_image02/image02.png)

## Layout XML

So what does this XML look like? Here's an example:

    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
       xmlns:tools="http://schemas.android.com/tools"
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:orientation="vertical"
       android:padding="16dp"
       tools:context="com.example.android.exampleapp.MainActivity">

       <EditText
           android:id="@+id/edit_text_name_input"
           android:layout_width="match_parent"
           android:layout_height="wrap_content"
           android:background="@color/colorAccent"
           android:hint="Enter your name"
           android:padding="4dp"
           android:textSize="24sp" />

       <TextView
           android:id="@+id/text_view_name_display"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:layout_gravity="center"
           android:layout_marginTop="8dp"
           android:text="Your name appears here"
           android:textSize="30sp" />
    </LinearLayout>

This looks like the following on a phone screen:

![Screenshot](https://d17h27t6h515a5.cloudfront.net/topher/2016/November/5827afdd_image03/image03.png)

## Type of View : UI Components

There are two major categories of views. The first type are UI components that are often interactive. Here are a few examples:

| Class Name    | Description   |
| ------------- |:-------------:| 
| [TextView](https://developer.android.com/reference/android/widget/TextView.html)        | Creates text on the screen; generally non interactive text. | 
| [EditText](https://developer.android.com/reference/android/widget/EditText.html)        | Creates a text input on the screen                          | 
| [ImageView](https://developer.android.com/reference/android/widget/ImageView.html)      | Creates an image on the screen                              |
| [Button](https://developer.android.com/reference/android/widget/Button.html)            | Creates a button on the screen                              |
| [Chronometer](https://developer.android.com/reference/android/widget/Chronometer.html)  | Create a simple timer on screen                             | 

The [android.widget](https://developer.android.com/reference/android/widget/package-summary.html) package contains a list of _most_ of the UI view classes available to you.

## Type of View : Container View

The second are views called "Layout" or "Container" views. They extend from a class called [ViewGroup](https://developer.android.com/reference/android/view/ViewGroup.html). They are primarily responsible for containing a group of views and determining where they are on screen. What do I mean by "containing a group of views?". I mean that a view will be nested inside the tag of another view, like below:

    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
       xmlns:tools="http://schemas.android.com/tools"
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:orientation="vertical"
       tools:context="com.example.android.exampleapp.MainActivity">
       <TextView
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:layout_gravity="center"
           android:text="A"
           android:textSize="30sp" />
       <TextView
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:layout_gravity="center"
           android:text="B"
           android:textSize="30sp" />
       <TextView
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:layout_gravity="center"
           android:text="C"
           android:textSize="30sp" />
    </LinearLayout>

This will look like:

![Screenshot](https://d17h27t6h515a5.cloudfront.net/topher/2016/November/5827aceb_image00/image00.png)

A few examples of common container views are:

| Class Name    | Description   |
| ------------- |:-------------:| 
| [LinearLayout](https://developer.android.com/reference/android/widget/LinearLayout.html)        | Displays views in a single column or row. | 
| [RelativeLayout](https://developer.android.com/reference/android/widget/RelativeLayout.html)        | Displays views positioned relative to each other and this view.                          | 
| [FrameLayout](https://developer.android.com/reference/android/widget/FrameLayout.html)      | A ViewGroup meant to contain a single child view.                              |
| [ScrollView](https://developer.android.com/reference/android/widget/ScrollView.html)            | A FrameLayout that is designed to let the user scroll through the content in the view.                              |
| [ConstraintLayout](https://developer.android.com/reference/android/support/constraint/ConstraintLayout.html)  | This is a newer viewgroup; it positions views in a flexible way. We’ll be exploring constraint layout later in the lesson.                             | 

Note that layout views can be nested in one another, so you can nest a LinearLayout inside of a LinearLayout if you so choose.

## XML Attributes

Views have attributes in XML which control the **properties** of the view. Here’s an example from before:

    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
       xmlns:tools="http://schemas.android.com/tools"
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:orientation="vertical"
       android:padding="16dp"
       tools:context="com.example.android.exampleapp.MainActivity">

       <EditText
           android:id="@+id/edit_text_name_input"
           android:layout_width="match_parent"
           android:layout_height="wrap_content"
           android:background="@color/colorAccent"
           android:hint="Enter your name"
           android:padding="4dp"
           android:textSize="24sp" />

       <TextView
           android:id="@+id/text_view_name_display"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:layout_gravity="center"
           android:layout_marginTop="8dp"
           android:text="Your name appears here"
           android:textSize="30sp" />
    </LinearLayout>

The properties are things like **textSize** and **padding**. Every view has a handful of properties associated with them, which can be found on their documentation pages. These properties can be set to different values. Properties determine the specifics of how a view looks and interacts. Let's look at a few examples of properties you’ll be using shortly.

### Text

The `android:text` attribute is an example of a very simple property that can be modified with the xml. In the code above, the portion that says

`android:text="Your name appears here"`

makes the TextView show the words:

![Screenshot](https://d17h27t6h515a5.cloudfront.net/topher/2016/November/5827ad06_image01/image01.png)

### Width and Height

Some of the most important properties are the width property and height property - those must be defined for every view. Remember that all views occupy a rectangular area on the screen - the width and height are the width and height of that area. You can define this in pixels, or better yet dp (stands for density-independent pixels, we’ll talk a lot more about this in later lessons):

    android:layout_width="200dp"
    android:layout_height="300dp"

For the sake of having a layout be responsive and adjust to different devices, two common values are not numbers at all, but `wrap_content` and `match_parent` used as shown here:

    android:layout_width="wrap_content"
    android:layout_height="match_parent"

**wrap_content** will shrink the view to wrap whatever is displayed inside the view. For example, if the view is filled with the text “Hello world” then `wrap_content` for the width will set the width of the view to be the exact width that the text “Hello world” takes up on the screen.

**match_parent** will expand the size of the view to be as large as the parent view which it is nested inside of.

### Padding and Margin

`padding` and `layout_margin` are two very similar attributes. Both determine the space around a View. The difference is that `padding` determines space within the boundaries of the view, and `layout_margin` determines the space outside the boundaries of the view. For a thorough example, check out this video about [Padding and Margin](https://classroom.udacity.com/courses/ud837/lessons/4330701752/concepts/42402386170923#)

## How do the XML Layouts relate to the Java Activites?

After you create your XML Layout you need to associate it with your activity. This is done in the `onCreate` method of the `Activity` using the method `setContentView`. You pass a reference to the layout file as `R.layout.name_of_layout`. For example, if your layout were named **activity_main.xml** this would look like:

    public class MainActivity extends AppCompatActivity {
        @Override
        protected void onCreate(Bundle savedInstanceState) {
           super.onCreate(savedInstanceState);
           setContentView(R.layout.activity_main);
           // other code to setup the activity
        }
        // other code
    }

At this point, you might have two questions, first, what is this R.layout business and second, what is setContentView actually doing?

### The R Class

When your application is compiled the [R](https://developer.android.com/reference/android/R.html) class is generated. It creates constants that allow you to dynamically identify the various contents of the `res` folder, including layouts. To learn more, check out the documentation about [resources](https://developer.android.com/guide/topics/resources/accessing-resources.html).

### setContentView

So what is the `setContentView` method doing? It **inflates the layout**. Essentially what happens is that Android reads your XML file and generates Java objects for each of the tags in your layout file. You can then edit these objects in the Java code by calling methods on the Java objects. We’ll go over what these methods look like and how to access view in your layout files later in the course.

## Additional resources

This was a very quick introduction to the basics of Android layouts. You’ll be learning more about leveraging resources and responsive design in the course. If you’d like a more in-depth introduction to creating XML layouts in Android, check out the first lesson in [Android for Beginners](https://www.udacity.com/course/android-development-for-beginners--ud837).
