# Android Notes


In Android XML files, we often see two main namespaces:

1. **`xmlns:android="http://schemas.android.com/apk/res/android"`**
2. **`xmlns:app="http://schemas.android.com/apk/res-auto"`**

These namespaces serve different purposes, and I'll explain the differences clearly.

### **1. `xmlns:android` Namespace**
- **Definition**: This is the standard namespace for attributes provided by the Android framework.
- **Prefix**: The prefix is `android:`.
- **Usage**: Used for built-in attributes defined by the Android system (e.g., `layout_width`, `layout_height`, `text`, etc.).
- **URI**: The URI (`http://schemas.android.com/apk/res/android`) is a unique identifier for the Android schema. It tells the parser that the attributes prefixed with `android:` are part of the Android framework.

**Example:**
```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World!" />
```

- Here, `android:layout_width`, `android:layout_height`, and `android:text` are attributes defined by the Android framework.

### **2. `xmlns:app` Namespace**
- **Definition**: This namespace is used for custom attributes defined by app libraries or components (e.g., `appcompat`, `ConstraintLayout`, `Material Design`).
- **Prefix**: The prefix is `app:`.
- **Usage**: Used for attributes that are not part of the core Android framework but are provided by external libraries or custom components (e.g., `layout_constraintTop_toTopOf`, `fabSize`).
- **URI**: The URI (`http://schemas.android.com/apk/res-auto`) allows the Android build system to **automatically determine** which library or resource to use for these attributes.

**Example:**
```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Click Me"
    app:cornerRadius="16dp"
    app:layout_constraintTop_toTopOf="parent" />
```

- Here, `app:cornerRadius` and `app:layout_constraintTop_toTopOf` are custom attributes provided by libraries like `Material Components` and `ConstraintLayout`.

### **Key Differences**

| **Aspect**             | **`xmlns:android`**                    | **`xmlns:app`**                        |
|------------------------|----------------------------------------|----------------------------------------|
| **Purpose**            | Core Android framework attributes      | Custom attributes from external libraries |
| **Prefix**             | `android:`                             | `app:`                                 |
| **URI**                | `http://schemas.android.com/apk/res/android` | `http://schemas.android.com/apk/res-auto` |
| **Examples**           | `android:text`, `android:layout_width` | `app:layout_constraintTop_toTopOf`, `app:cornerRadius` |
| **Usage Scope**        | Standard attributes in Android SDK     | Custom attributes from app libraries   |

### **Why Use `xmlns:app`?**
- The `app` namespace (`xmlns:app`) allows you to use attributes that are not part of the standard Android framework.
- It lets the build system **auto-detect** which library provides the attribute, so you don't need to specify it manually.

### **Example with Both Namespaces**
```xml
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

**Explanation:**
- `android:layout_width` and `android:text` are standard Android attributes.
- `app:layout_constraintTop_toTopOf` and `app:layout_constraintStart_toStartOf` are custom attributes provided by the ConstraintLayout library.

### **Summary**
- Use **`xmlns:android`** for attributes from the core Android framework.
- Use **`xmlns:app`** for attributes from custom components or libraries.
- The **`xmlns:app`** namespace (`res-auto`) allows flexibility, letting the Android build system figure out which library to use for custom attributes.

This helps avoid conflicts and makes your XML code cleaner. Let me know if you need any more details!

---

# Common Android Attributes

### 📜 **Built-in Attributes (Core Android)**
| **Attribute**                 | **Description**                                                 |
|-------------------------------|-----------------------------------------------------------------|
| `android:id`                  | Unique identifier for the view.                                 |
| `android:layout_width`        | Specifies the width of the view (`match_parent`, `wrap_content`).|
| `android:layout_height`       | Specifies the height of the view (`match_parent`, `wrap_content`).|
| `android:text`                | Sets the text content of a `TextView`.                          |
| `android:textColor`           | Sets the color of the text.                                     |
| `android:textSize`            | Sets the size of the text.                                      |
| `android:background`          | Sets the background color or drawable.                          |
| `android:padding`             | Sets padding inside the view.                                   |
| `android:margin`              | Sets margin outside the view (via `layout_margin`).             |
| `android:gravity`             | Aligns content within the view (`center`, `left`, `right`).     |
| `android:orientation`         | Sets the orientation (`horizontal`, `vertical` for layouts).    |
| `android:visibility`          | Controls visibility (`visible`, `invisible`, `gone`).           |
| `android:clickable`           | Determines if the view is clickable (`true`, `false`).          |
| `android:src`                 | Sets the image source for `ImageView`.                          |
| `android:contentDescription`  | Describes the view for accessibility purposes.                  |
| `android:inputType`           | Specifies the type of data expected in an input field (e.g., `text`, `number`).|
| `android:hint`                | Placeholder text for input fields.                              |
| `android:maxLines`            | Sets the maximum number of lines in a `TextView`.               |
| `android:ellipsize`           | Adds ellipsis (`...`) if text is too long.                      |
| `android:scaleType`           | Controls how an image is scaled in an `ImageView`.              |
| `android:elevation`           | Sets the shadow effect (elevation) of the view.                 |

### 📦 **External Attributes (`xmlns:app` - Custom Libraries)**
| **Attribute**                        | **Description**                                                 |
|--------------------------------------|-----------------------------------------------------------------|
| `app:layout_constraintTop_toTopOf`   | Aligns the top of the view to the top of another view (ConstraintLayout).|
| `app:layout_constraintBottom_toBottomOf` | Aligns the bottom of the view to the bottom of another view (ConstraintLayout).|
| `app:cornerRadius`                   | Sets the corner radius for a `MaterialCardView`.                |
| `app:fabSize`                        | Sets the size of a Floating Action Button (FAB).                |
| `app:srcCompat`                      | Sets the image source for `ImageView` with compatibility support.|
| `app:layout_behavior`                | Defines behavior for `CoordinatorLayout` (e.g., scrolling).     |
| `app:showAsAction`                   | Controls how an item is displayed in the ActionBar.             |
| `app:chipIcon`                       | Sets the icon for a `Chip` component.                           |
| `app:tabIndicatorColor`              | Sets the color of the tab indicator in a `TabLayout`.           |
| `app:toolbarNavigationButtonStyle`   | Customizes the navigation button style in a `Toolbar`.          |
| `app:shimmer_color`                  | Sets the shimmer effect color in `ShimmerFrameLayout`.          |
| `app:badgeTextColor`                 | Sets the text color for a `Badge` in `BottomNavigationView`.    |
| `app:layoutManager`                  | Defines the layout manager for a `RecyclerView` (e.g., `LinearLayoutManager`).|
| `app:progressIndicatorStyle`         | Sets the style for a progress indicator (`CircularProgressIndicator`).|

### 🔍 **Popular Libraries and Their Attributes**
1. **ConstraintLayout (`app:layout_constraint*`)**: Provides advanced positioning attributes for UI elements.
2. **Material Components (`app:cornerRadius`, `app:strokeColor`)**: Offers attributes for styling Material Design components.
3. **Glide/Picasso (`app:placeholder`, `app:errorImage`)**: Image loading libraries with custom attributes for placeholder and error images.
4. **Navigation Component (`app:navGraph`, `app:startDestination`)**: Attributes for setting up navigation graphs.

### 📖 **Conclusion**
This is a **summary of commonly used attributes**. For a complete list:
- Refer to the official [Android Developer Documentation](https://developer.android.com/reference).
- Explore third-party library documentation (e.g., Material Components, ConstraintLayout) for their attributes.


<!-- ================================================================ -->

---
---

# 2nd InSem

## Assignment 3rd

`Section A`

### Q1. What is the importance of data storage in mobile applications?

**Importance of Data Storage:**
- **Persistence**: Ensures user data remains available even after the app is closed or the device is restarted.
- **User Experience**: Saves user preferences, settings, and progress to provide a consistent experience.
- **Offline Access**: Allows users to access data without an internet connection (e.g., cached data).

**Types of Data Storage in Android:**
1. **Internal Storage**: Private storage for app-specific files.
2. **External Storage**: Public storage for larger files like media.
3. **Shared Preferences**: For saving simple key-value pairs.
4. **SQLite Database / Room**: For complex data storage.
5. **Cloud Storage**: For storing data online (e.g., Firebase).

---

### Q2. Explain the purpose of Shared Preferences in Android.

**Purpose:**
- Shared Preferences provide a way to store small amounts of **key-value pairs** data persistently across app sessions.
- Used for storing **user preferences** like theme, login status, or user settings.

**Example:**

```java
// Saving data to SharedPreferences
SharedPreferences sharedPref = getSharedPreferences("MyApp", MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPref.edit();
editor.putString("username", "faze_flynn");
editor.putBoolean("isLoggedIn", true);
editor.apply();

// Retrieving data from SharedPreferences
String username = sharedPref.getString("username", "default");
boolean isLoggedIn = sharedPref.getBoolean("isLoggedIn", false);
```

---

### Q3. What is the Room Persistence Library, and why is it used?

**Room Persistence Library:**
- A part of **Android Jetpack**, Room is an abstraction layer over SQLite.
- Simplifies database operations by providing **compile-time checks**, reducing boilerplate code, and supporting **LiveData** and **Flow**.

**Why Use Room:**
1. **Ease of Use**: Simplifies the database code with annotations.
2. **Type Safety**: Detects SQL errors during compile-time.
3. **Integration**: Works well with LiveData for reactive programming.

**Example:**

```java
// Entity class
@Entity
public class User {
    @PrimaryKey
    public int uid;
    public String name;
}

// DAO interface
@Dao
public interface UserDao {
    @Insert
    void insert(User user);

    @Query("SELECT * FROM User WHERE uid = :userId")
    User getUserById(int userId);
}
```

---

### Q4. What is a Content URI in Android?

**Content URI:**
- A **Uniform Resource Identifier (URI)** that identifies a specific data set in a content provider.
- It is used to interact with data from another application (e.g., Contacts, Media).

**Structure of Content URI:**
- `content://authority/path/id`
- `authority`: Identifies the content provider.
- `path`: Specifies the type of data.
- `id`: Optional, specifies a particular record.

**Example:**

```java
// Querying contacts using a Content URI
Uri uri = ContactsContract.Contacts.CONTENT_URI;
Cursor cursor = getContentResolver().query(uri, null, null, null, null);
```

---

### Q5. What is Jetpack, and why is it important for modern Android development?

**Jetpack:**
- **Android Jetpack** is a collection of libraries, tools, and best practices to help developers build high-quality Android apps.
- It includes components like **LiveData**, **ViewModel**, **Room**, **Navigation**, and **DataBinding**.

**Importance:**
1. **Simplifies Development**: Reduces boilerplate code.
2. **Consistency**: Provides standardized solutions across all Android versions.
3. **Maintainability**: Encourages modern architecture patterns (MVVM, Clean Architecture).

**Example Components:**
- **Lifecycle**: Manages activity lifecycle changes.
- **Room**: Manages database operations.
- **Navigation**: Handles navigation between fragments.

**Code Example (ViewModel with LiveData):**

```java
public class MyViewModel extends ViewModel {
    private MutableLiveData<String> userName = new MutableLiveData<>();

    public LiveData<String> getUserName() {
        return userName;
    }

    public void setUserName(String name) {
        userName.setValue(name);
    }
}
```

`Section B`

### Q1. Describe the different data storage options in Android based on size, complexity, and persistence needs, such as Shared Preferences, SQLite, and others.

**Data Storage Options in Android:**

1. **Shared Preferences:**
   - **Purpose**: To store small amounts of simple data as key-value pairs (e.g., user settings, login status).
   - **Size**: Limited to small data (typically a few KB).
   - **Complexity**: Low (easy to implement).
   - **Persistence**: Persistent across app sessions until explicitly cleared.
   - **Use Case**: Saving user preferences like theme selection, notification settings.

   **Example:**

   ```java
   SharedPreferences sharedPref = getSharedPreferences("MyApp", MODE_PRIVATE);
   SharedPreferences.Editor editor = sharedPref.edit();
   editor.putString("username", "faze_flynn");
   editor.apply();

   // Retrieving data
   String username = sharedPref.getString("username", "default_user");
   ```

2. **Internal Storage:**
   - **Purpose**: To store private files for the app, which are not accessible by other apps.
   - **Size**: Depends on the device storage (suitable for small to medium-sized files).
   - **Complexity**: Moderate.
   - **Persistence**: Persistent until the app is uninstalled.
   - **Use Case**: Storing sensitive user data like user profiles, settings.

   **Example:**

   ```java
   FileOutputStream fos = openFileOutput("user_data.txt", Context.MODE_PRIVATE);
   fos.write("User data".getBytes());
   fos.close();
   ```

3. **External Storage:**
   - **Purpose**: To store larger files accessible by other apps and the user.
   - **Size**: Large (depends on external storage capacity).
   - **Complexity**: Moderate (requires permissions).
   - **Persistence**: Data remains until manually deleted.
   - **Use Case**: Storing media files (photos, videos).

   **Example:**

   ```java
   File file = new File(getExternalFilesDir(null), "myfile.txt");
   FileOutputStream fos = new FileOutputStream(file);
   fos.write("External data".getBytes());
   fos.close();
   ```

4. **SQLite Database:**
   - **Purpose**: To store complex structured data in a relational database format.
   - **Size**: Suitable for medium to large data (up to a few GB).
   - **Complexity**: High (requires SQL queries).
   - **Persistence**: Persistent across app sessions.
   - **Use Case**: Storing user data, logs, or any structured data requiring querying.

   **Example:**

   ```java
   SQLiteDatabase db = openOrCreateDatabase("MyDatabase", MODE_PRIVATE, null);
   db.execSQL("CREATE TABLE IF NOT EXISTS Users (id INTEGER PRIMARY KEY, name TEXT)");
   db.execSQL("INSERT INTO Users (name) VALUES ('Faze Flynn')");
   ```

5. **Room Database (Recommended for SQLite abstraction):**
   - **Purpose**: Provides an abstraction layer over SQLite to simplify database access.
   - **Size**: Suitable for complex and large data storage.
   - **Complexity**: Moderate (simpler than raw SQLite).
   - **Persistence**: Persistent across app sessions.
   - **Use Case**: Complex data storage with compile-time verification of SQL queries.

   **Example:**

   ```java
   @Entity
   public class User {
       @PrimaryKey
       public int uid;
       public String name;
   }
   ```

6. **Cloud Storage (e.g., Firebase, AWS S3):**
   - **Purpose**: To store data online, accessible from anywhere.
   - **Size**: Very large (depends on the cloud service plan).
   - **Complexity**: High (requires network operations).
   - **Persistence**: Data is stored in the cloud and remains available until deleted.
   - **Use Case**: Storing user-generated content (photos, videos), real-time databases.

   **Example (Firebase Firestore):**

   ```java
   FirebaseFirestore db = FirebaseFirestore.getInstance();
   Map<String, Object> user = new HashMap<>();
   user.put("name", "Faze Flynn");
   db.collection("users").add(user);
   ```

---

### Q2. Explain how Room DAOs are used for CRUD (Create, Read, Update, Delete) operations in a Room Database. Provide code examples.

**Room DAOs (Data Access Objects):**
- DAOs are interfaces in Room used to define database operations without writing raw SQL queries.
- They provide a clean API for database operations like **Create**, **Read**, **Update**, and **Delete** (CRUD).

**Example: Room Database with DAO:**

1. **Entity Class:**

   ```java
   @Entity
   public class User {
       @PrimaryKey(autoGenerate = true)
       public int id;
       public String name;
   }
   ```

2. **DAO Interface:**

   ```java
   @Dao
   public interface UserDao {
       // Create
       @Insert
       void insertUser(User user);

       // Read
       @Query("SELECT * FROM User WHERE id = :userId")
       User getUserById(int userId);

       // Update
       @Update
       void updateUser(User user);

       // Delete
       @Delete
       void deleteUser(User user);
   }
   ```

3. **Database Class:**

   ```java
   @Database(entities = {User.class}, version = 1)
   public abstract class AppDatabase extends RoomDatabase {
       public abstract UserDao userDao();
   }
   ```

4. **Usage:**

   ```java
   AppDatabase db = Room.databaseBuilder(context, AppDatabase.class, "user-db").build();
   UserDao userDao = db.userDao();

   // Insert
   User user = new User();
   user.name = "Faze Flynn";
   userDao.insertUser(user);

   // Read
   User retrievedUser = userDao.getUserById(1);

   // Update
   retrievedUser.name = "Faze Flynn Updated";
   userDao.updateUser(retrievedUser);

   // Delete
   userDao.deleteUser(retrievedUser);
   ```

---

### Q3. How do Loaders work in Android, and what are some of the modern alternatives to Loaders for loading data in the background?

**Loaders:**
- Loaders are components used to load data asynchronously in Android, particularly in earlier versions.
- They are used to perform long-running operations (e.g., querying a database) without blocking the UI thread.
- The **LoaderManager** handles the lifecycle of Loaders.

**Example:**

```java
// Using CursorLoader to load data from a ContentProvider
getLoaderManager().initLoader(0, null, new LoaderManager.LoaderCallbacks<Cursor>() {
    @Override
    public Loader<Cursor> onCreateLoader(int id, Bundle args) {
        return new CursorLoader(context, ContactsContract.Contacts.CONTENT_URI, null, null, null, null);
    }

    @Override
    public void onLoadFinished(Loader<Cursor> loader, Cursor data) {
        // Process the loaded data
    }

    @Override
    public void onLoaderReset(Loader<Cursor> loader) {
        // Reset the loader
    }
});
```

**Modern Alternatives to Loaders:**

1. **ViewModel and LiveData:**
   - Recommended for modern Android development as part of the Jetpack library.
   - Manages data in a lifecycle-aware way, preventing memory leaks.

   **Example:**

   ```java
   public class MyViewModel extends ViewModel {
       private MutableLiveData<List<User>> users = new MutableLiveData<>();

       public LiveData<List<User>> getUsers() {
           return users;
       }

       public void loadUsers() {
           // Load data in the background (e.g., using Room)
           users.setValue(database.userDao().getAllUsers());
       }
   }
   ```

2. **WorkManager:**
   - Used for deferrable background tasks like syncing data.

3. **Coroutines and Flow (Kotlin):**
   - Provides a more modern and concise approach for background operations.


`Section C`

### Q1. Explain the lifecycle of Fragments in Android and how to manage Fragment transactions. Provide examples to demonstrate common lifecycle events.

**Fragment Lifecycle:**
- A Fragment in Android has its own lifecycle, which is closely related to the lifecycle of the activity it is attached to. The main lifecycle methods of a Fragment are:

1. **`onAttach(Context context)`**:
   - Called when the Fragment is associated with its parent Activity.
   - Used to perform initialization that requires a Context.

2. **`onCreate(Bundle savedInstanceState)`**:
   - Called to initialize the Fragment.
   - Used for creating non-UI components like ViewModels.

3. **`onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)`**:
   - Called to create the Fragment's UI view.
   - Returns the root view of the Fragment's layout.

4. **`onViewCreated(View view, Bundle savedInstanceState)`**:
   - Called after the view is created.
   - Used to initialize UI components and set up event listeners.

5. **`onStart()`**:
   - Called when the Fragment becomes visible.

6. **`onResume()`**:
   - Called when the Fragment is active and interactive.

7. **`onPause()`**:
   - Called when the Fragment is no longer interactive.

8. **`onStop()`**:
   - Called when the Fragment is no longer visible.

9. **`onDestroyView()`**:
   - Called when the Fragment’s view hierarchy is being destroyed.

10. **`onDestroy()`**:
    - Called when the Fragment is being destroyed.

11. **`onDetach()`**:
    - Called when the Fragment is detached from its parent Activity.

**Fragment Lifecycle Example:**

```java
public class MyFragment extends Fragment {

    @Override
    public void onAttach(@NonNull Context context) {
        super.onAttach(context);
        Log.d("FragmentLifecycle", "onAttach called");
    }

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        Log.d("FragmentLifecycle", "onCreate called");
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        Log.d("FragmentLifecycle", "onCreateView called");
        return inflater.inflate(R.layout.fragment_my, container, false);
    }

    @Override
    public void onViewCreated(@NonNull View view, Bundle savedInstanceState) {
        super.onViewCreated(view, savedInstanceState);
        Log.d("FragmentLifecycle", "onViewCreated called");
    }

    @Override
    public void onDestroyView() {
        super.onDestroyView();
        Log.d("FragmentLifecycle", "onDestroyView called");
    }
}
```

**Fragment Transactions:**
- Fragment transactions are used to add, replace, or remove Fragments dynamically at runtime.

**Fragment Transaction Example:**

```java
FragmentManager fragmentManager = getSupportFragmentManager();
FragmentTransaction transaction = fragmentManager.beginTransaction();

// Replacing a Fragment
MyFragment newFragment = new MyFragment();
transaction.replace(R.id.fragment_container, newFragment);
transaction.addToBackStack(null);
transaction.commit();
```

**Common Lifecycle Events:**
- **`onCreateView`**: Inflate the Fragment’s UI.
- **`onViewCreated`**: Set up UI elements.
- **`onDestroyView`**: Cleanup UI resources.

---

### Q2. Discuss Jetpack Navigation and how it helps in creating a seamless navigation flow in an Android app. Provide code examples of navigating between different fragments or activities.

**Jetpack Navigation:**
- Jetpack Navigation is a library that simplifies navigation within an Android app. It handles the back stack, deep links, and navigation transitions between different screens (Fragments or Activities).

**Benefits of Jetpack Navigation:**
1. **Simplified Navigation**: No need to manually handle Fragment transactions.
2. **Back Stack Management**: Automatically manages the back stack.
3. **Deep Linking**: Supports deep links for navigating directly to a specific screen.

**Setting Up Jetpack Navigation:**
1. Add dependencies in `build.gradle`:

   ```gradle
   implementation "androidx.navigation:navigation-fragment-ktx:2.7.3"
   implementation "androidx.navigation:navigation-ui-ktx:2.7.3"
   ```

2. Define the navigation graph (`nav_graph.xml`):

   ```xml
   <navigation xmlns:android="http://schemas.android.com/apk/res/android"
       xmlns:app="http://schemas.android.com/apk/res-auto"
       app:startDestination="@id/firstFragment">

       <fragment
           android:id="@+id/firstFragment"
           android:name="com.example.FirstFragment">
           <action
               android:id="@+id/action_first_to_second"
               app:destination="@id/secondFragment" />
       </fragment>

       <fragment
           android:id="@+id/secondFragment"
           android:name="com.example.SecondFragment" />
   </navigation>
   ```

3. Navigate between Fragments using NavController:

   ```java
   NavController navController = Navigation.findNavController(view);
   navController.navigate(R.id.action_first_to_second);
   ```

---

### Q3. What is the MVVM architecture in Android? Explain the role of ViewModels as central data stores for UI data with a practical example.

**MVVM Architecture:**
- **MVVM** (Model-View-ViewModel) is a design pattern that helps separate the UI logic from business logic and data.
  - **Model**: Represents the data layer (e.g., database, API).
  - **View**: Represents the UI (e.g., Activities, Fragments).
  - **ViewModel**: Acts as a bridge between the Model and View, managing the UI-related data lifecycle-aware.

**Role of ViewModel:**
- ViewModel stores and manages UI-related data in a lifecycle-conscious way.
- It survives configuration changes (e.g., screen rotation) and helps avoid memory leaks.

**MVVM Example:**

1. **Model (User.java):**

   ```java
   public class User {
       private String name;
       private int age;

       public User(String name, int age) {
           this.name = name;
           this.age = age;
       }

       public String getName() { return name; }
       public int getAge() { return age; }
   }
   ```

2. **ViewModel (UserViewModel.java):**

   ```java
   public class UserViewModel extends ViewModel {
       private final MutableLiveData<User> user = new MutableLiveData<>();

       public LiveData<User> getUser() {
           return user;
       }

       public void setUser(User newUser) {
           user.setValue(newUser);
       }
   }
   ```

3. **View (MainActivity.java):**

   ```java
   public class MainActivity extends AppCompatActivity {
       private UserViewModel userViewModel;

       @Override
       protected void onCreate(Bundle savedInstanceState) {
           super.onCreate(savedInstanceState);
           setContentView(R.layout.activity_main);

           userViewModel = new ViewModelProvider(this).get(UserViewModel.class);

           // Observing changes in the User data
           userViewModel.getUser().observe(this, user -> {
               if (user != null) {
                   TextView nameTextView = findViewById(R.id.nameTextView);
                   nameTextView.setText(user.getName());
               }
           });

           // Updating User data
           User user = new User("Faze Flynn", 25);
           userViewModel.setUser(user);
       }
   }
   ```

**Benefits of MVVM:**
1. **Separation of Concerns**: Keeps UI logic and business logic separate.
2. **Lifecycle Awareness**: ViewModel is lifecycle-aware, reducing memory leaks.
3. **Data Binding Support**: Works well with Android's data binding library for seamless UI updates.


## Assignment 4th

`Section A`

### Q1. What is the difference between synchronous and asynchronous programming?

- **Synchronous Programming**:
  - Tasks are executed one after another.
  - The next task waits for the current task to finish.
  - **Example**: Reading a file and blocking the UI until the file is read.

- **Asynchronous Programming**:
  - Tasks are executed independently of the main thread.
  - The next task does not wait for the current task to complete.
  - **Example**: Fetching data from a server without blocking the UI thread.
Here's the Kotlin version of the synchronous and asynchronous code example using coroutines:

#### Synchronous Example (Kotlin)
In a synchronous approach, the tasks block each other.

```kotlin
fun main() {
    println("Start")
    fetchDataSynchronously()
    println("End")
}

fun fetchDataSynchronously() {
    Thread.sleep(2000) // Blocks the main thread for 2 seconds
    println("Fetching data...")
}
```

**Output:**
```
Start
Fetching data...
End
```

#### Asynchronous Example (Kotlin with Coroutines)
In an asynchronous approach, coroutines allow non-blocking execution.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    println("Start")
    launch {
        fetchDataAsynchronously()
    }
    println("End")
}

suspend fun fetchDataAsynchronously() {
    delay(2000) // Does not block the main thread
    println("Fetching data...")
}
```

**Output:**
```
Start
End
Fetching data...
```

#### Explanation:
- **Synchronous Code**: The `Thread.sleep()` method blocks the main thread, making the program wait before proceeding.
- **Asynchronous Code**: The `delay()` function in coroutines is non-blocking. It suspends the coroutine without blocking the main thread, allowing other tasks to run.

This shows how coroutines help in writing asynchronous code in Kotlin.

---

### Q2. Mention two benefits of using asynchronous programming in Android.

1. **Improved UI Responsiveness**:
   - Asynchronous tasks prevent the UI from freezing by handling time-consuming operations (e.g., network requests) on a separate thread.

2. **Efficient Resource Utilization**:
   - Asynchronous tasks can run in the background, allowing the app to perform multiple tasks concurrently without blocking the main thread.

---

### Q3. What are coroutines, and why are they useful in Android development?

- **Coroutines**:
  - Coroutines are lightweight, concurrency primitives in Kotlin that simplify asynchronous programming.
  - They allow you to write asynchronous code in a sequential and non-blocking manner using `suspend` functions.

- **Why Coroutines are Useful**:
  1. **Simplified Asynchronous Code**: Coroutines help avoid callback hell and make code more readable.
  2. **Efficient Thread Management**: Coroutines use fewer system resources, making them more efficient than traditional threading.

**Example** (Kotlin):
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("Coroutine!")
    }
    println("Hello")
}
// Output:
// Hello
// Coroutine!
```

---

### Q4. What is a GET request, and how is it used in API calls?

- **GET Request**:
  - A GET request is used to **retrieve data** from a server without modifying it.
  - It is one of the most common HTTP methods for fetching resources.

**Example** (Java with OkHttp Library):
```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
        .url("https://api.example.com/data")
        .build();

client.newCall(request).enqueue(new Callback() {
    @Override
    public void onResponse(Call call, Response response) throws IOException {
        String responseData = response.body().string();
        System.out.println(responseData);
    }

    @Override
    public void onFailure(Call call, IOException e) {
        e.printStackTrace();
    }
});
```

---

### Q5. What is the purpose of a Broadcast Receiver in Android?

- **Broadcast Receiver**:
  - A Broadcast Receiver is a component in Android used to listen for system-wide or app-wide broadcast messages (intents).
  - It helps react to events such as battery changes, network connectivity, or custom broadcasts within the app.

**Example**:
```java
public class MyReceiver extends BroadcastReceiver {
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent.getAction().equals(Intent.ACTION_BATTERY_LOW)) {
            Toast.makeText(context, "Battery is low!", Toast.LENGTH_SHORT).show();
        }
    }
}
```

In the manifest:
```xml
<receiver android:name=".MyReceiver">
    <intent-filter>
        <action android:name="android.intent.action.BATTERY_LOW" />
    </intent-filter>
</receiver>
```

`Section B`

### Q1. Explain how coroutines work in Kotlin for Android, including launching and managing coroutines with code examples. Discuss error handling and cancellation using `try-catch`.

#### **Overview of Coroutines in Kotlin**
- Coroutines are Kotlin’s solution for asynchronous programming, enabling developers to write non-blocking code in a sequential manner.
- Coroutines help manage tasks on different threads without blocking the main thread.
- The main building blocks are:
  - **CoroutineScope**: Defines the scope for coroutines.
  - **Launch**: Creates a coroutine that doesn’t return a result (used for fire-and-forget tasks).
  - **Async**: Creates a coroutine that returns a result (used for tasks that need a result).
  - **Dispatcher**: Specifies the thread on which the coroutine will run (e.g., `Dispatchers.Main`, `Dispatchers.IO`).

#### **Launching Coroutines**
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    println("Main program starts")

    // Launch a coroutine in the background
    launch(Dispatchers.IO) {
        delay(1000L) // Non-blocking delay
        println("Coroutine Task on IO thread")
    }

    // Launch a coroutine with async
    val result = async {
        computeSum(5, 10)
    }
    println("Sum: ${result.await()}")

    println("Main program ends")
}

suspend fun computeSum(a: Int, b: Int): Int {
    delay(500L)
    return a + b
}
```

**Output:**
```
Main program starts
Coroutine Task on IO thread
Sum: 15
Main program ends
```

#### **Error Handling and Cancellation**
- **Error Handling**: Use `try-catch` within coroutines for exception handling.
- **Cancellation**: Coroutines can be cancelled using the `cancel()` function. The `isActive` property can be used to check if the coroutine is still active.

**Example with Error Handling and Cancellation:**
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val job = launch {
        try {
            repeat(1000) { i ->
                if (isActive) {
                    println("Processing $i")
                    delay(100L)
                }
            }
        } catch (e: Exception) {
            println("Coroutine cancelled with exception: $e")
        } finally {
            println("Cleanup resources if needed")
        }
    }

    delay(500L)
    println("Cancelling the coroutine")
    job.cancelAndJoin() // Cancels and waits for the coroutine to complete
    println("Coroutine cancelled")
}
```

**Output:**
```
Processing 0
Processing 1
Processing 2
Processing 3
Processing 4
Cancelling the coroutine
Cleanup resources if needed
Coroutine cancelled
```

### Q2. Describe how to make API calls in Android using Retrofit or Volley. Provide an example of making a GET request and parsing the resulting JSON data using Gson or Moshi.

#### **Using Retrofit with Gson**
- Retrofit is a type-safe HTTP client for Android used to make API calls.
- Gson is a library used to parse JSON data into Kotlin/Java objects.

**Setup**:
- Add dependencies in `build.gradle`:
```gradle
implementation 'com.squareup.retrofit2:retrofit:2.9.0'
implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
```

#### **API Interface**:
```kotlin
import retrofit2.http.GET
import retrofit2.Call

interface ApiService {
    @GET("posts/1")
    fun getPost(): Call<Post>
}
```

#### **Data Model**:
```kotlin
data class Post(
    val userId: Int,
    val id: Int,
    val title: String,
    val body: String
)
```

#### **Retrofit Setup and API Call**:
```kotlin
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory
import retrofit2.Call
import retrofit2.Callback
import retrofit2.Response

fun main() {
    val retrofit = Retrofit.Builder()
        .baseUrl("https://jsonplaceholder.typicode.com/")
        .addConverterFactory(GsonConverterFactory.create())
        .build()

    val apiService = retrofit.create(ApiService::class.java)
    val call = apiService.getPost()

    call.enqueue(object : Callback<Post> {
        override fun onResponse(call: Call<Post>, response: Response<Post>) {
            if (response.isSuccessful) {
                val post = response.body()
                println("Title: ${post?.title}")
                println("Body: ${post?.body}")
            }
        }

        override fun onFailure(call: Call<Post>, t: Throwable) {
            println("Error: ${t.message}")
        }
    })
}
```

**Output:**
```
Title: sunt aut facere repellat provident occaecati
Body: quia et suscipit suscipit...
```

### Q3. Discuss the file I/O operations in Android. Explain how to read, write, and delete files using the `File` class and streams, with code examples.

#### **Overview**
- Android provides the `File` class for handling file I/O operations.
- Files can be stored in:
  - **Internal Storage**: Private to the app, not accessible by other apps.
  - **External Storage**: Can be accessed by the user and other apps with permission.

#### **Writing to a File**
```kotlin
import android.content.Context
import java.io.File
import java.io.FileOutputStream

fun writeToFile(context: Context, fileName: String, data: String) {
    val file = File(context.filesDir, fileName)
    FileOutputStream(file).use {
        it.write(data.toByteArray())
    }
    println("Data written to $fileName")
}
```

#### **Reading from a File**
```kotlin
import android.content.Context
import java.io.File

fun readFromFile(context: Context, fileName: String): String {
    val file = File(context.filesDir, fileName)
    return if (file.exists()) {
        file.readText()
    } else {
        "File not found"
    }
}
```

#### **Deleting a File**
```kotlin
import android.content.Context
import java.io.File

fun deleteFile(context: Context, fileName: String): Boolean {
    val file = File(context.filesDir, fileName)
    return file.delete().also {
        println(if (it) "File deleted" else "File not found")
    }
}
```

#### **Example Usage in Android Activity**
```kotlin
writeToFile(context, "example.txt", "Hello, Android!")
val data = readFromFile(context, "example.txt")
println("Read Data: $data")
deleteFile(context, "example.txt")
```

**Output:**
```
Data written to example.txt
Read Data: Hello, Android!
File deleted
```

---

`Section C`

### Q1. Explain the lifecycle of a service in Android, including key methods like `onCreate`, `onStartCommand`, and `onDestroy`. Discuss different types of service binding and how services can be used in an Android application.

#### **Overview of Android Services**
- An Android **Service** is a component that runs in the background to perform long-running operations without interacting with the user interface.
- Services are primarily used for tasks like playing music, handling network transactions, or performing background processing.

#### **Types of Services**
1. **Started Service**:
   - Initiated by calling `startService()` or `startForegroundService()`.
   - Runs in the background until stopped using `stopSelf()` or `stopService()`.

2. **Bound Service**:
   - Allows components (like activities) to bind to the service using `bindService()`.
   - Provides a client-server interface for communication between the service and the component.

3. **Foreground Service**:
   - Runs in the foreground with a persistent notification (e.g., music player).
   - Uses `startForeground()` to display the notification and avoid being killed by the system.

#### **Lifecycle of a Service**
1. **`onCreate()`**:
   - Called when the service is first created.
   - Initializes resources like threads or network connections.

2. **`onStartCommand()`**:
   - Called each time the service is started using `startService()`.
   - Specifies what to do when the service starts and returns an integer indicating the restart behavior.

3. **`onBind()` and `onUnbind()`**:
   - Used for bound services to return an `IBinder` for communication.
   - `onUnbind()` is called when the last client unbinds from the service.

4. **`onDestroy()`**:
   - Called when the service is stopped or destroyed.
   - Cleans up any resources to prevent memory leaks.

#### **Code Example for Started Service**
```kotlin
import android.app.Service
import android.content.Intent
import android.os.IBinder
import android.util.Log

class MyService : Service() {

    override fun onCreate() {
        super.onCreate()
        Log.d("MyService", "Service Created")
    }

    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {
        Log.d("MyService", "Service Started")
        // Perform a task in the background
        return START_STICKY
    }

    override fun onDestroy() {
        super.onDestroy()
        Log.d("MyService", "Service Destroyed")
    }

    override fun onBind(intent: Intent?): IBinder? {
        return null // Not a bound service
    }
}
```

#### **Using the Service in an Activity**
```kotlin
val intent = Intent(this, MyService::class.java)
startService(intent) // To start the service
stopService(intent)  // To stop the service
```

### **Service Binding Example**
For a **Bound Service**, use `onBind()` to return an `IBinder`.

```kotlin
class MyBoundService : Service() {
    private val binder = LocalBinder()

    inner class LocalBinder : Binder() {
        fun getService(): MyBoundService = this@MyBoundService
    }

    override fun onBind(intent: Intent?): IBinder {
        return binder
    }
}
```

In an Activity:
```kotlin
val serviceConnection = object : ServiceConnection {
    override fun onServiceConnected(name: ComponentName?, service: IBinder?) {
        val binder = service as MyBoundService.LocalBinder
        val myService = binder.getService()
    }

    override fun onServiceDisconnected(name: ComponentName?) {}
}

bindService(intent, serviceConnection, Context.BIND_AUTO_CREATE)
```

### Q2. Discuss the concept of dispatchers in coroutines, focusing on `Dispatchers.IO` and `Dispatchers.Main`. Provide examples of how to use them with suspend functions to manage background tasks efficiently.

#### **Coroutine Dispatchers**
- **Dispatchers** determine the thread where the coroutine will be executed.
- Commonly used dispatchers:
  - **`Dispatchers.Main`**: Runs tasks on the main (UI) thread, typically used for updating UI.
  - **`Dispatchers.IO`**: Optimized for I/O tasks like reading from a database or making network requests.
  - **`Dispatchers.Default`**: Used for CPU-intensive tasks (e.g., sorting large data sets).
  - **`Dispatchers.Unconfined`**: Starts the coroutine in the caller thread and continues in the thread where the coroutine is resumed.

#### **Example with `Dispatchers.IO` and `Dispatchers.Main`**
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    println("Main program starts")

    launch(Dispatchers.Main) {
        val result = fetchDataFromNetwork()
        println("Data: $result")
    }

    println("Main program ends")
}

suspend fun fetchDataFromNetwork(): String = withContext(Dispatchers.IO) {
    delay(1000L)
    "Data fetched from network"
}
```

**Output:**
```
Main program starts
Main program ends
Data: Data fetched from network
```

### **Error Handling in Coroutines**
```kotlin
launch {
    try {
        withContext(Dispatchers.IO) {
            throw Exception("Network Error")
        }
    } catch (e: Exception) {
        println("Caught Exception: ${e.message}")
    }
}
```

### Q3. Describe the techniques for parsing data formats other than JSON in Android. Explain how to parse XML and HTML data using libraries like XMLPullParser with code examples.

#### **Parsing XML using XMLPullParser**
- **XMLPullParser** is a lightweight API for parsing XML data in Android.
- It processes XML data in a streaming fashion, making it memory efficient.

#### **Example of XML Data**
```xml
<books>
    <book>
        <title>Android Development</title>
        <author>John Doe</author>
    </book>
    <book>
        <title>Kotlin Programming</title>
        <author>Jane Smith</author>
    </book>
</books>
```

#### **XML Parsing Code**
```kotlin
import android.util.Xml
import org.xmlpull.v1.XmlPullParser

fun parseXML(xmlData: String) {
    val parser = Xml.newPullParser()
    parser.setInput(xmlData.reader())
    var eventType = parser.eventType
    var title = ""
    var author = ""

    while (eventType != XmlPullParser.END_DOCUMENT) {
        val tagName = parser.name
        when (eventType) {
            XmlPullParser.START_TAG -> {
                if (tagName == "title") {
                    title = parser.nextText()
                } else if (tagName == "author") {
                    author = parser.nextText()
                }
            }
            XmlPullParser.END_TAG -> {
                if (tagName == "book") {
                    println("Title: $title, Author: $author")
                }
            }
        }
        eventType = parser.next()
    }
}
```

#### **Output:**
```
Title: Android Development, Author: John Doe
Title: Kotlin Programming, Author: Jane Smith
```

#### **Parsing HTML using Jsoup Library**
- Jsoup is a library for parsing HTML data in Android.

**Setup**:
```gradle
implementation 'org.jsoup:jsoup:1.15.4'
```

**HTML Parsing Code**:
```kotlin
import org.jsoup.Jsoup

fun parseHTML(htmlData: String) {
    val document = Jsoup.parse(htmlData)
    val titles = document.select("h1")
    for (title in titles) {
        println("Title: ${title.text()}")
    }
}
```

#### **Example HTML Input**:
```html
<h1>Welcome to Android Development</h1>
<h1>Kotlin for Android</h1>
```

#### **Output:**
```
Title: Welcome to Android Development
Title: Kotlin for Android
```

---

## Important Topics

### 1. **Activities and Fragments Lifecycle**

#### **Activity Lifecycle**
- An **Activity** represents a single screen with a user interface.
- Key lifecycle methods:
  1. **`onCreate()`**: Initialization of activity, called when the activity is first created.
  2. **`onStart()`**: The activity is becoming visible.
  3. **`onResume()`**: The activity is now interacting with the user.
  4. **`onPause()`**: Activity is partially visible; the user is navigating away.
  5. **`onStop()`**: Activity is no longer visible.
  6. **`onDestroy()`**: Final cleanup before the activity is destroyed.
  7. **`onRestart()`**: Called if the activity is being restarted after stopping.

**Real-life Scenario**: 
Think of an Activity like a page in a book. Opening the book (`onCreate`), flipping to the page (`onStart`), reading it (`onResume`), pausing reading (`onPause`), closing the book temporarily (`onStop`), and throwing away the book (`onDestroy`).

#### **Fragment Lifecycle**
- A **Fragment** represents a portion of the UI in an Activity.
- Key lifecycle methods:
  1. **`onAttach()`**: Fragment is attached to the activity.
  2. **`onCreateView()`**: Create the view hierarchy for the fragment.
  3. **`onViewCreated()`**: Called after `onCreateView()`, view components are initialized.
  4. **`onStart()`**, **`onResume()`**, **`onPause()`**, **`onStop()`**: Same as in Activity.
  5. **`onDestroyView()`**: Cleans up the fragment view.
  6. **`onDetach()`**: Fragment is detached from the activity.

**Code Example:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        Log.d("Lifecycle", "Activity Created")
    }

    override fun onResume() {
        super.onResume()
        Log.d("Lifecycle", "Activity Resumed")
    }

    override fun onDestroy() {
        super.onDestroy()
        Log.d("Lifecycle", "Activity Destroyed")
    }
}
```

### 2. **Android Architecture (Layers)**

- **Android architecture** is divided into 4 main layers:
  1. **Linux Kernel**:
     - Core layer, handles device drivers, memory management, and hardware abstraction.
  2. **Libraries & Android Runtime (ART)**:
     - Provides core libraries (e.g., SQLite, SSL) and ART for executing bytecode.
  3. **Application Framework**:
     - Manages system services like Activity Manager, Content Providers, Notification Manager.
  4. **Applications**:
     - The top layer, includes user applications like Contacts, Camera, etc.

**Real-life Scenario**: 
Imagine a smartphone like a building. The **Linux Kernel** is the foundation, **Libraries** are the utilities, the **Application Framework** is the interior design, and **Applications** are the residents.

### 3. **MVC Architecture**

- **Model-View-Controller (MVC)**:
  - **Model**: Manages data and business logic.
  - **View**: Displays the data to the user.
  - **Controller**: Handles user input and updates the model and view.

**Real-life Scenario**:
A restaurant: **Model** is the kitchen (data), **View** is the menu (display), **Controller** is the waiter (input handling).

**Code Example (Kotlin) using MVC**:
```kotlin
// Model
class User(val name: String, val age: Int)

// Controller
class UserController {
    fun getUser(): User = User("John", 25)
}

// View
val user = UserController().getUser()
println("User: ${user.name}, Age: ${user.age}")
```

### 4. **MVP Architecture**

- **Model-View-Presenter (MVP)**:
  - **Model**: Data and business logic.
  - **View**: Displays data, but is passive (no logic).
  - **Presenter**: Handles all logic, acts as a mediator between Model and View.

**Real-life Scenario**:
A sports coach (**Presenter**) instructs the player (**Model**) based on the game plan (**View**).

### 5. **MVVM Architecture**

- **Model-View-ViewModel (MVVM)**:
  - **Model**: Data and business logic.
  - **View**: The UI layer.
  - **ViewModel**: Manages the data for the UI, acts as a central data store.

**Real-life Scenario**:
A news app: The **Model** is the data source (news), the **View** is the news display, and the **ViewModel** updates the news content in the UI.

**Code Example**:
```kotlin
// ViewModel
class UserViewModel : ViewModel() {
    val userName = MutableLiveData<String>()
    fun updateUser(name: String) {
        userName.value = name
    }
}

// In Activity
val viewModel = ViewModelProvider(this).get(UserViewModel::class.java)
viewModel.updateUser("Alice")
```

### 6. **Data Storage in Android**

1. **Shared Preferences**:
   - For storing small key-value pairs.
   - Example: User login state.
   
2. **SQLite Database**:
   - For structured data storage, supports SQL queries.
   - Example: Storing user profile data.

3. **Room Database**:
   - An abstraction layer over SQLite.
   - Example: Caching API data locally.

4. **Internal and External Storage**:
   - For file storage like images or text files.

5. **Content Providers**:
   - For sharing data between applications.

### 7. **Layouts in Android**

1. **LinearLayout**:
   - Arranges elements in a single direction (horizontal or vertical).
   - Example:
   ```xml
   <LinearLayout
       android:orientation="vertical">
       <TextView android:text="Hello" />
       <Button android:text="Click Me" />
   </LinearLayout>
   ```

2. **RelativeLayout**:
   - Positions elements relative to each other or the parent.
   - Example:
   ```xml
   <RelativeLayout>
       <TextView android:id="@+id/textView" android:text="Hello" />
       <Button android:layout_below="@id/textView" android:text="Click Me" />
   </RelativeLayout>
   ```

3. **ConstraintLayout**:
   - Offers complex layouts with better performance using constraints.
   - Example:
   ```xml
   <ConstraintLayout>
       <TextView
           android:id="@+id/textView"
           app:layout_constraintTop_toTopOf="parent" />
       <Button
           app:layout_constraintTop_toBottomOf="@id/textView"
           android:text="Click Me" />
   </ConstraintLayout>
   ```

4. **FrameLayout**:
   - For displaying a single view, useful for overlays.
   - Example:
   ```xml
   <FrameLayout>
       <ImageView android:src="@drawable/image" />
   </FrameLayout>
   ```

---

### 1. **Tools and Views in Android (EditText and Layout Views)**

#### **EditText**
- **Type**: View
- **Purpose**: Allows users to input text.
- **Attributes**: `android:hint`, `android:maxLength`, `android:inputType`.
  
**Real-life scenario**: Think of an **EditText** as a form field where you type in your name or email on a webpage.

**Code Example**:
```xml
<EditText
    android:id="@+id/editTextName"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Enter your name" />
```

In **Activity** (Kotlin):
```kotlin
val editTextName = findViewById<EditText>(R.id.editTextName)
val userName = editTextName.text.toString()
```

#### **Layout Views**
- **LinearLayout**: Aligns child views either vertically or horizontally.
- **RelativeLayout**: Positions child views relative to each other.
- **ConstraintLayout**: Allows flexible positioning of elements with better performance.
- **FrameLayout**: A simple layout for stacking views.

**Code Example (LinearLayout)**:
```xml
<LinearLayout
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click me" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello, World!" />
</LinearLayout>
```

---

### 2. **Input and Output Operations**

#### **Input Operations**
- **User Input**: Gathering data from **EditText** fields, buttons, etc.
  - Example: Using **EditText** for collecting user-entered text.

**Code Example**:
```kotlin
val editText = findViewById<EditText>(R.id.editText)
val input = editText.text.toString()  // Get user input
```

#### **Output Operations**
- **Displaying Data**: Using **TextView**, **Toast**, **Snackbar**, or **AlertDialog** to display data.
  - **Toast**: Short message.
  - **Snackbar**: Message with optional action.
  - **TextView**: To display static or dynamic text.

**Code Example (TextView Output)**:
```kotlin
val textView = findViewById<TextView>(R.id.textView)
textView.text = "User input: $input"
```

#### **File I/O Operations**
- **Reading** and **writing** files from internal or external storage using **File** class or **FileInputStream**/**FileOutputStream**.

**Code Example (File Writing)**:
```kotlin
val file = File(filesDir, "user_data.txt")
file.writeText("User data: $input")
```

#### **Reading Data from a File**:
```kotlin
val file = File(filesDir, "user_data.txt")
val content = file.readText()
Log.d("FileContent", content)
```




$$
\Large \text{2nd InSem Ends here}
$$


<!-- ================================================================= -->

---
---



## Previous Rough Notes


```plaintext
13 Sept 2024
--------------------------------------------
Both java and kotlin are interoperable

For small scale applications - we use java
For large scale applications - we will use Kotlin because it can handle complexities

Kotlin was introduced in 2011 by jetbrain for developing the JVM (Java Virtual Machine)
In 2017 google officially announceed it as the main and preffered developing language for android

Key Features:
    1. Statiscally Typed language - Compiled time datatyping
    2. Consize Syntax
    3. Safe from any exceptions
    4. Nullablity - how null values are handled
    5. Kotlin is functional and object oriented based
    6. Less compilation time
    7. Tool Friendly



17 Sept 2024
-------------------------------------------------------------
Now starting kotlin:-

Variables - containers to store data in our memory

var - can be changed
val - constant cannot be changed

declaring a variable in koltin

var a:Int = 34;
var f:Float = 34.34;
var ch:Char = 'A';
var name:String = "Faze Flynn";
var arr:Array<Int> = (1,2,4,,5,6);

we often declare the variables to be null so that it can be safe.

Datatypes:-
    B - Byte
    S - Short
    I - Int
    L - Long
    F - Float
    D - Double
    C - Char
    S - String
    A - Array
    B - Boolean


TypeCasting:-
    int (var) : Boolean = "True"  -- Explicit Datatype   

var greet:String = "Hello"



imp topics
----------------------------------------------------------
history of android
activity lifecycle fragment lifecycle
architecture of android
layouts
```