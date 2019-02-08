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

Activity Lifecyle: 

![alt text](https://s3.ap-south-1.amazonaws.com/mindorks-server-uploads/android_activity_lifecycle_mindorks_image.png)

Fragment Lifecycle: 

![alt text](https://s3.ap-south-1.amazonaws.com/mindorks-server-uploads/android_fragments_lifecycle_mindorks_image.png)

Acitivity and Fragment LifeCycle in Comparison: 

![alt text](https://github.com/xxv/android-lifecycle/raw/master/complete_android_fragment_lifecycle.png)


## 4. Preferences

It is part of the android JetPack.
A Preference is the basic building block of the Preference Library. A settings screen contains a Preference hierarchy. You can define this hierarchy as an XML resource, or you can build a hierarchy in code.

The sections below describe how to build a simple settings screen using the AndroidX Preference Library.

    <androidx.preference.PreferenceScreen
        xmlns:app="http://schemas.android.com/apk/res-auto">

        <SwitchPreferenceCompat
            app:key="notifications"
            app:title="Enable message notifications"/>

        <Preference
            app:key="feedback"
            app:title="Send feedback"
            app:summary="Report technical issues or suggest new features"/>

    </androidx.preference.PreferenceScreen>

NOTE :::: The root tag must be a <PreferenceScreen>, and the XML resource must be placed in the res/xml/ directory.
    
  To inflate a hierarchy from an XML attribute, create a PreferenceFragmentCompat, override onCreatePreferences(), and provide the XML resource to inflate, as shown in the example below:
  
      public class MySettingsFragment extends PreferenceFragmentCompat {
        @Override
        public void onCreatePreferences(Bundle savedInstanceState, String rootKey) {
            setPreferencesFromResource(R.xml.preferences, rootKey);
        }
    }
    
    public class MySettingsActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        getSupportFragmentManager()
                .beginTransaction()
                .replace(R.id.settings_container, new MySettingsFragment())
                .commit();
    }
}


## 5. Stroing Data in SQLite

SQL databases:

        1. Store data in tables of rows and columns.
        2. The intersection of a row and column is called a field.
        3. Fields contain data, references to other fields, or references to other tables.
        4. Rows are identified by unique IDs.
        5. Columns are identified by names that are unique per table.
Think of it as a spreadsheet with rows, columns, and cells, where cells can contain data, references to other cells, and links to other sheets.

SQLite:

SQLite is a software library that implements SQL database engine that is:

        self-contained (requires no other components)
        serverless (requires no server backend)
        zero-configuration (does not need to be configured for your application)
        transactional (changes within a single transaction in SQLite either occur completely or not at all)
        SQLite is the most widely deployed database engine in the world. The source code for SQLite is in the public domain.
        For details of the SQLite database, see the SQLite website.


Transactions:

    A transaction is a sequence of operations performed as a single logical unit of work. A logical unit of work must exhibit four properties, called the atomicity, consistency, isolation, and durability (ACID) properties, to qualify as a transaction.
    All changes within a single transaction in SQLite either occur completely or not at all, even if the act of writing the change out to the disk is interrupted by a program crash, an operating system crash, or a power failure.

Examples of transactions:
Transferring money from a savings account to a checking account.
Entering a term and definition into dictionary.
Committing a changelist to the master branch.
ACID:

    1. Atomicity. Either all of its data modifications are performed, or none of them are performed.
    2. Consistency. When completed, a transaction must leave all data in a consistent state.
    3. Isolation. Modifications made by concurrent transactions must be isolated from the modifications made by any other concurrent transactions. A transaction either recognizes data in the state it was in before another concurrent transaction modified it, or it recognizes the data after the second transaction has completed, but it does not recognize an intermediate state.
    4. Durability. After a transaction has completed, its effects are permanently in place in the system. The modifications persist even in the event of a system failure.
More on transactions.



Cursors:

    Queries always return a Cursor object. A Cursor is an object interface that provides random read-write access to the result set returned by a database query. It points to the first element in the result of the query.
    A cursor is a pointer into a row of structured data. You can think of it as a pointer to table rows.
    The Cursor class provides methods for moving the cursor through that structure, and methods to get the data from the columns of each row.
    When a method returns a Cursor object, you iterate over the result, extract the data, do something with the data, and finally close the cursor to release the memory.



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
