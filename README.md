# android-essentials


# Topics to cover:

# Part 1
## 1. Recycler View
A flexible view for providing a limited window into a large data set.

A RecyclerView is a new ViewGroup used to render any adapter-based view in horizontal or vertical or grid or staggered grid manner.



Adapter: A subclass of RecyclerView.Adapter responsible for providing views that represent items in a data set.

Position: The position of a data item within an Adapter.

Index: The index of an attached child view as used in a call to getChildAt(int). Contrast with Position.

Binding: The process of preparing a child view to display data corresponding to a position within the adapter.

Recycle (view): A view previously used to display data for a specific adapter position may be placed in a cache for later reuse to display the same type of data again later. This can drastically improve performance by skipping initial layout inflation or construction.

Scrap (view): A child view that has entered into a temporarily detached state during layout. Scrap views may be reused without becoming fully detached from the parent RecyclerView, either unmodified if no rebinding is required or modified by the adapter if the view was considered dirty.

Dirty (view): A child view that must be rebound by the adapter before being displayed.

COmponents of Recycler View: 
1. RecyclerView.LayoutManager. - responsible for fetching the view from Adapter and displaying it on UI. 
2. RecyclerView.ViewHolder. - helps in creating viewobjects to hold the data fetched from Adapter. 
3. RecyclerView.Adapter : Takes out the data from the data source and provides it to Layout Manager to present it on UI.
4. RecyclerView.ItemAnimator : 






## 2. Intents
Intents are message objects that make a request to the Android runtime to start an activity or other app component in your app or in some other app. You don't start those activities yourself;

When your app is first started from the device home screen, the Android runtime sends an intent to your app to start your app's main activity (the one defined with the MAIN action and the LAUNCHER category in the Android Manifest). To start other activities in your app, or request that actions be performed by some other activity available on the device, you build your own intents with the Intent class and call the startActivity() method to send that intent.

In addition to starting activities, intents are also used to pass data between activities. When you create an intent to start a new activity, you can include information about the data you want that new activity to operate on. So, for example, an email activity that displays a list of messages can send an intent to the activity that displays that message. The display activity needs data about the message to display, and you can include that data in the intent.

There are two types of intents in Android:

    Explicit intents specify the receiving activity (or other component) by that activity's fully-qualified class name. Use an explicit intent to start a component in your own app (for example, to move between screens in the user interface), because you already know the package and class name of that component.

    Implicit intents do not specify a specific activity or other component to receive the intent. Instead you declare a general action to perform in the intent. The Android system matches your request to an activity or other component that can handle your requested action. You'll learn more about implicit intents in a later chapter.

An Intent object is an instance of the Intent class. For explicit intents, the key fields of an intent include the following:

    1. The activity class (for explicit intents). This is the class name of the activity or other component that should receive the intent, for example, com.example.SampleActivity.class. Use the intent constructor or the intent's setComponent(), setComponentName() or setClassName() methods to specify the class.
    2. The intent data. The intent data field contains a reference to the data you want the receiving activity to operate on, as a Uri object.
    3. Intent extras. These are key-value pairs that carry information the receiving activity requires to accomplish the requested action.
    4. Intent flags. These are additional bits of metadata, defined by the Intent class. The flags may instruct the Android system how to launch an activity or how to treat it after it's launched.
  
  Explicit Intent:
  
      Intent messageIntent = new Intent(this, ShowMessageActivity.class);
    startActivity(messageIntent);

Implicit Intent:

    Intent sendIntent = new Intent();
    sendIntent.setAction(Intent.ACTION_SEND);
    sendIntent.putExtra(Intent.EXTRA_TEXT, textMessage);
    sendIntent.setType("text/plain");

    // Verify that the intent will resolve to an activity
    if (sendIntent.resolveActivity(getPackageManager()) != null) {
        startActivity(sendIntent);

NOTE:

    To verify that an activity will receive the intent, call resolveActivity() on your Intent object. If the result is non-null, there is at least one app that can handle the intent and it's safe to call startActivity(). If the result is null, do not use the intent and, if possible, you should disable the feature that issues the intent. The following example shows how to verify that the intent resolves to an activity. 
    
## Activity Navigation :

Android system supports two different forms of navigation strategies for your app.

    1. Temporal or Back navigation, provided by the device back button, and the back stack.
    2. Ancestral, or Up navigation, provided by you as an option in the app's action bar.
    
## 3. Lifecycle

Activity Lifecyle
![alt text](https://s3.ap-south-1.amazonaws.com/mindorks-server-uploads/android_activity_lifecycle_mindorks_image.png)

Fragment Lifecycle:
![alt text] (https://s3.ap-south-1.amazonaws.com/mindorks-server-uploads/android_fragments_lifecycle_mindorks_image.png)

Acitivity and Fragment LifeCycle in Comparison:

![alt text] (https://github.com/xxv/android-lifecycle/raw/master/complete_android_fragment_lifecycle.png)


## 4. Preferences
## 4. Preferences
## 5. Stroing Data in SQLite
## 6. Content Providers
## 7. Android Architecture Components
## 8. Background Tasks
## 9. UI - Constraint Layout
## 10. UI - Accessibility & Internalization



# Part 2
## 1. Fragments
## 2. Libraries
## 3. FCM
## 4. Places
## 5. Media Playback
## 6. Widgets
## 7. Espresso
