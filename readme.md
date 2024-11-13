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
<!-- ================================================================= -->



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