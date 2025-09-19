# Material 3 Bottom Sheet for Sketchware Pro 🚀

[![YouTube Thumbnail](https://raw.githubusercontent.com/FasterSoftwareDeveloper/Material3-Bottom-Sheet-In-Sketchware-Pro/refs/heads/main/thumbnail.png)](https://www.youtube.com/watch?v=your_video_id_here)
*(Click the image to watch the tutorial on YouTube)*

A comprehensive collection of **80+ powerful blocks** to implement modern Material Design 3 Bottom Sheets in your Sketchware Pro projects. This library provides full control over both **Modal** and **Standard** bottom sheets, including behavior, states, callbacks, and styles. It also includes blocks for the recommended `BottomSheetDialogFragment` approach.

## ✨ Features

* **Modal Bottom Sheets**: Dialogs that slide up from the bottom, disabling interaction with the rest of the screen.
* **Standard Bottom Sheets**: Surfaces that are part of the main UI and can be dragged, expanded, or collapsed.
* **`BottomSheetDialogFragment`**: A modern and lifecycle-aware way to display modal bottom sheets.
* **Full Behavior Control**: Programmatically control attributes like `PeekHeight`, `MaxHeight`, `isHideable`, `isDraggable`, `skipCollapsed`, and more.
* **State Management**: Easily set and listen for states like `STATE_EXPANDED`, `STATE_COLLAPSED`, `STATE_HIDDEN`, etc.
* **Callbacks**: Implement `onStateChanged` and `onSlide` listeners to create dynamic and interactive UIs.
* **Theming & Styling**: Supports default, dark, light, and custom Material 3 themes.
* **Data Passing**: Simple blocks for passing data to and from a `BottomSheetDialogFragment`.

---

## 🔧 Prerequisites & Dependencies

Before using these blocks, you must add the latest Material Components and AndroidX Core libraries to your Sketchware Pro project.

1.  Go to `Library Manager` > `Local Library`.
2.  Download the following dependencies:

    ```groovy
    // For Material Design 3 Components
    // The version 1.14.0-alpha04 is specified, but you can use newer stable versions too.
    com.google.android.material:material:1.14.0-alpha04

    // For AndroidX Core functionality
    androidx.core:core:1.17.0
    ```

---

## 📥 How to Import into Sketchware Pro

Follow these simple steps to get the blocks into your project:

1.  **Download Files**: Download the project `.zip` file from this repository, which includes the Sketchware project, the blocks (`.json`), and the menu manager file (`.json`).
2.  **Restore Project**: Restore the downloaded Sketchware Pro project.
3.  **Import Blocks**: Go to `Settings` > `Block Manager` and import the `FasterM3BottomSheet.json` file.
4.  **Import Menu**: Go to `Settings` > `Block selection menu manager` and import the corresponding menu JSON file to organize the blocks neatly.
5.  **Done!** 🎉 The blocks are now ready to use in your project.

---

## 👨‍💻 Complete Usage Guide

This section provides a detailed breakdown of how to use every block.

### Modal Bottom Sheet

A modal bottom sheet is a dialog that appears over the main content.

**Code Logic:**
The main block creates a `BottomSheetDialog`, inflates your custom layout file (`.xml`) into a `View`, sets that view as the dialog's content, and then displays it.

**Example:**
To show a simple modal bottom sheet:


1.  Use the `FaaterM3ModalBottomSheetBuilder` block.
2.  Provide a unique name for your dialog (e.g., `myDialog`).
3.  Specify the context (`YourActivity.this` or `getActivity()`).
4.  Provide a name for your custom view (e.g., `myCustomView`).
5.  Select the layout file you want to display.
6.  Choose a style (e.g., `Default Style` or `Dark Style`).
7.  Set `Cancelable` to true or false.

### 🔷 Faster M3 Modal Bottom Sheet

A modal bottom sheet is a dialog that appears over the main content.

#### Creating a Modal Bottom Sheet
Use the **`FaaterM3ModalBottomSheetBuilder`** block to initialize and show your dialog.

```java
// Create a new BottomSheetDialog instance, providing context and an optional style
BottomSheetDialog myDialog = new BottomSheetDialog(MainActivity.this, com.google.android.material.R.style.ThemeOverlay_Material3_BottomSheetDialog);

// Inflate your custom XML layout into a View object
View myCustomView = getLayoutInflater().inflate(R.layout.custom_view, null);

// Set the inflated view as the dialog's content
myDialog.setContentView(myCustomView);

// (Optional) Add other configurations here

// Set if the dialog can be canceled with the back button or by touching outside
myDialog.setCancelable(true);

// Show the dialog
myDialog.show();
```

#### Finding Views Inside the Modal Sheet
Use the **`FM3BS View In Modal Bottom Sheet`** block to get a reference to a widget inside your custom layout.

```java
// Find a Button with the ID 'myButton' inside your inflated 'myCustomView'
final Button myButton = myCustomView.findViewById(R.id.myButton);
```

#### Modal Sheet Styles
Use these blocks in the `Style` slot of the builder.

```java
// Block: FM3BS (Default Style) - No extra code, just leave the slot empty.

// Block: FM3BS ThemeOverlay Style
// Provides the standard M3 bottom sheet styling.
, com.google.android.material.R.style.ThemeOverlay_Material3_BottomSheetDialog

// Block: FM3BS Dark Style
// Forces a dark theme for the bottom sheet.
, com.google.android.material.R.style.Theme_Material3_Dark_BottomSheetDialog

// Block: FM3BS Light Style
// Forces a light theme for the bottom sheet.
, com.google.android.material.R.style.Theme_Material3_Light_BottomSheetDialog

// Block: FM3BS Custom Style
// Use a custom style defined in your styles.xml.
, R.style.MyCustomBottomSheetStyle
```

#### Modal Sheet Utilities
These blocks control the behavior and appearance of the shown `BottomSheetDialog`.

```java
// === General Control ===

// Close/hide the dialog.
// Block: FM3BS dialog Exit
myDialog.dismiss();

// === Appearance & Behavior ===

// Set if the dialog can be canceled by pressing the back button.
// Block: FM3BS setCancelable
myDialog.setCancelable(true); // or false

// Set if the dialog is canceled when touching outside of its window.
// Block: FM3BS setCanceledOnTouchOutside
myDialog.setCanceledOnTouchOutside(true); // or false

// Set the dim amount of the background (0.0f = transparent, 1.0f = fully black).
// Block: FM3BS setDimAmount
myDialog.getWindow().setDimAmount(0.6f);

// Set a custom background, e.g., for rounded corners from a drawable resource.
// Block: FM3BS setBackgroundDrawableResource
myDialog.getWindow().setBackgroundDrawableResource(R.drawable.my_custom_bg);

// Ensure an EditText inside the sheet can receive focus correctly.
// Block: Sheet edittext focusable in touch mode
myEditText.setFocusableInTouchMode(true);
```

#### Modal Sheet Listeners
Execute code when the dialog is clicked, canceled, or dismissed.

```java
// Block: FM3BS Click Listener
myButton.setOnClickListener(v -> {
    // Code to run on button click
});

// Block: FM3BS setOnCancelListener
// Triggers when the dialog is canceled (e.g., by back press).
myDialog.setOnCancelListener(dialog -> {
    // Code to run on cancel
});

// Block: FM3BS setOnDismissListener
// Triggers whenever the dialog is closed, either by cancel or programmatically.
myDialog.setOnDismissListener(dialog -> {
    // Code to run on dismiss
});
```

#### Context Blocks
Use the correct context block in the `Activity/fragment` slot of the builder.

```java
// Use in an Activity (e.g., MainActivity)
// Block: FM3BS (Activity)
MainActivity.this

// Use in a Fragment
// Block: FM3BS Fragment (getActivity)
getActivity()

// Block: FM3BS Fragment (requireContext) - Safer, prevents nulls
requireContext()

// Block: FM3BS Fragment (getContext)
getContext()
```

---
### 🔶 Faster M3 Standard Bottom Sheet & Behavior

A standard bottom sheet is part of your activity's layout, typically inside a `CoordinatorLayout`.

**Code Logic:**
You first get the `BottomSheetBehavior` from your `FrameLayout` and then use the behavior blocks to control it.


1.  Use the `FM3BS Behavior Builder` block, passing your `FrameLayout`'s ID (e.g., `my_bottom_sheet`). This gives you a behavior variable (e.g., `myBehavior`).
2.  Use other behavior blocks to modify its properties, such as `setPeekHeight`, `setHideable`, or `setState`, using the `myBehavior` variable.

#### 1. Layout Setup (`.xml`)
Your layout **must** have a `CoordinatorLayout` as the root. The view that acts as the bottom sheet should be a direct child (like a `FrameLayout`) and have the `layout_behavior` attribute.

```xml
<androidx.coordinatorlayout.widget.CoordinatorLayout
    ...
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <FrameLayout
        android:id="@+id/standard_bottom_sheet"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:layout_behavior="com.google.android.material.bottomsheet.BottomSheetBehavior">
        
        </FrameLayout>

</androidx.coordinatorlayout.widget.CoordinatorLayout>
```

#### 2. Getting the Behavior Controller
In your `onCreate`, get the `BottomSheetBehavior` instance from your `FrameLayout`.

```java
// Block: FM3BS Behavior Builder

// Get the FrameLayout from your XML.
FrameLayout sheetView = findViewById(R.id.standard_bottom_sheet);

// Get the Behavior controller from the FrameLayout.
BottomSheetBehavior<FrameLayout> myBehavior = BottomSheetBehavior.from(sheetView);
```

#### 3. Managing Content Inside the Sheet
You can dynamically add or remove views from your `FrameLayout`.

```java
// Inflate a new layout to be placed inside the bottom sheet.
// Block: FM3BS Standard Custom View
View newContent = getLayoutInflater().inflate(R.layout.sheet_content, standard_bottom_sheet, false);

// Add the new view to your FrameLayout.
// Block: FM3BS addView
standard_bottom_sheet.addView(newContent);

// Remove all views from the FrameLayout.
// Block: FM3BS removeAllViews
standard_bottom_sheet.removeAllViews();

// Find a view within the standard bottom sheet.
// Block: FM3BS View In Standard Bottom Sheet
final TextView title = standard_bottom_sheet.findViewById(R.id.title_text);
```

#### 4. Controlling the Behavior
Use the `myBehavior` variable to control every aspect of the sheet.

```java
// === State Control ===

// Expand, collapse, or hide the sheet. Use the State blocks here.
// Block: FM3BS setState
myBehavior.setState(BottomSheetBehavior.STATE_EXPANDED);
/* Available States:
   STATE_EXPANDED, STATE_COLLAPSED, STATE_HIDDEN, STATE_HALF_EXPANDED,
   STATE_DRAGGING, STATE_SETTLING
*/

// === Behavior Toggles ===

// Allow the sheet to be completely hidden by swiping down.
// Block: FM3BS setHideable behavior
myBehavior.setHideable(true); // or false

// Allow the user to drag the sheet up and down.
// Block: FM3BS draggable behavior
myBehavior.setDraggable(true); // or false

// If true, the sheet will skip the collapsed state when swiped.
// Block: FM3BS Collapsed State Behavior
myBehavior.setSkipCollapsed(true); // or false

// If true, the sheet's height wraps its content. If false, it fills the parent.
// Block: FM3BS setFitToContents
myBehavior.setFitToContents(true); // or false

// === Sizing & Position ===

// Set the height of the sheet when it's collapsed (in pixels).
// Block: FM3BS PeekHeight Behavior
myBehavior.setPeekHeight(250);

// Set the maximum height the sheet can have (in pixels).
// Block: FM3BS setMaxHeight
myBehavior.setMaxHeight(1800);

// Set the maximum width the sheet can have (in pixels).
// Block: FM3BS setMaxWidth
myBehavior.setMaxWidth(800);

// Set the ratio for the half-expanded state (0.0 to 1.0).
// Block: FM3BS setHalfExpandedRatio
myBehavior.setHalfExpandedRatio(0.6f);

// Set an offset from the top of the screen for the expanded state (in pixels).
// Block: FM3BS setExpandedOffset
myBehavior.setExpandedOffset(50);

// Set the velocity threshold for flinging the sheet.
// Block: FM3BS setSignificantVelocityThreshold
myBehavior.setSignificantVelocityThreshold(500);

// Force the bottom sheet to match parent height (fullscreen).
// Block: FM3BS Standard FULLSCREEN_MODE
standard_bottom_sheet.post(() -> {
    standard_bottom_sheet.getLayoutParams().height = ViewGroup.LayoutParams.MATCH_PARENT;
    standard_bottom_sheet.requestLayout();
});
```

#### 5. Save Flags
Control what state is saved on configuration changes (e.g., screen rotation).

```java
// Block: FM3BS setSaveFlags
// Combine flags with a '|' character.
myBehavior.setSaveFlags(BottomSheetBehavior.SAVE_PEEK_HEIGHT | BottomSheetBehavior.SAVE_HIDEABLE);

/* Available Flags (use blocks):
   SAVE_ALL, SAVE_NONE, SAVE_PEEK_HEIGHT, SAVE_HIDEABLE, 
   SAVE_SKIP_COLLAPSED, SAVE_FIT_TO_CONTENTS, SAVE_STATE
*/
```

#### 6. Behavior Callbacks
Listen for state changes or slide events.

```java
// Block: FM3BS BottomSheetCallback
myBehavior.addBottomSheetCallback(new BottomSheetBehavior.BottomSheetCallback() {
    @Override
    public void onStateChanged(@NonNull View bottomSheet, int newState) {
        // Use the State blocks here for comparison
        // Block: FM3BS state (if)
        if (newState == BottomSheetBehavior.STATE_EXPANDED) {
            // Sheet is expanded
        // Block: FM3BS State (else if)
        } else if (newState == BottomSheetBehavior.STATE_COLLAPSED) {
            // Sheet is collapsed
        }
    }

    @Override
    public void onSlide(@NonNull View bottomSheet, float slideOffset) {
        // Runs as the sheet is being dragged.
        // slideOffset ranges from -1.0 (hidden) to 1.0 (expanded)
    }
});
```

---

### 🧩 FasterBottomSheetDialogFragment

The most robust and modern approach. It handles its own lifecycle and is great for complex UIs.

#### 1. Showing the DialogFragment (from Activity)

```java
// === Create a Bundle to send data ===
// Block: FBSDF create new bundle
Bundle myBundle = new Bundle();

// Block: FBSDF Send data (putString)
myBundle.putString("user_name_key", "Alice");
// Block: FBSDF Send data (putInt)
myBundle.putInt("user_id_key", 123);
// Block: FBSDF Send data (putBoolean)
myBundle.putBoolean("is_admin_key", true);
// Block: FBSDF Send data (putDouble)
myBundle.putDouble("score_key", 95.5);


// === Show the Fragment ===
// Block: Faster BS Dialog Fragment Builder
MyCustomBSDF myFragment = new MyCustomBSDF(); // Your custom fragment class
myFragment.setArguments(myBundle);
myFragment.show(getSupportFragmentManager(), "my_dialog_tag");
```

#### 2. Inside Your `BottomSheetDialogFragment`
Place this logic inside the **`FBSDF onViewCreated`** block.

```java
// === Get the Dialog for more control ===
// Block: FBSDF get dialog
BottomSheetDialog dialog = (BottomSheetDialog) getDialog();
// Now you can use modal dialog utilities like setCancelable(), etc. on 'dialog'.

// === Make the dialog fullscreen ===
// First, get the FrameLayout using the behavior builder for modal dialogs.
FrameLayout bottomSheet = dialog.findViewById(com.google.android.material.R.id.design_bottom_sheet);
// Then, use the fullscreen block.
// Block: FBSDF Fullscreen mode
bottomSheet.getLayoutParams().height = ViewGroup.LayoutParams.MATCH_PARENT;


// === Receive Arguments from Activity ===
// Block: FBSDF getArguments null check
if (getArguments() != null) {
    // Block: FBSDF get data from bundle via Arguments
    String userName = getArguments().getString("user_name_key");
    int userID = getArguments().getInt("user_id_key");
    boolean isAdmin = getArguments().getBoolean("is_admin_key");
    double score = getArguments().getDouble("score_key");
}

// === Dismiss the Fragment ===
// Block: FBSDF dismiss dialog 
dismiss();
```

#### 3. Sending Data Back to the Activity

```java
// === In your Fragment (e.g., on a button click) ===

// Create a result bundle
Bundle resultBundle = new Bundle();
resultBundle.putString("result_key", "Data from dialog");

// Block: FBSDF send data
getParentFragmentManager().setFragmentResult("request_key", resultBundle);
dismiss(); // Close the dialog


// === In your Activity (e.g., in onCreate) ===

// Block: FBSDF receive data (activity)
getSupportFragmentManager().setFragmentResultListener("request_key", MainActivity.this,
(requestKey, bundle) -> {
    // Block: FBSDF receive getString
    String result = bundle.getString("result_key");
    
    // Other getter blocks:
    // int resultInt = bundle.getInt("int_key");
    // boolean resultBool = bundle.getBoolean("bool_key");
    // double resultDouble = bundle.getDouble("double_key");
});
```

# Android Edge-to-Edge UI 🚀

Enable full-screen UI using AndroidX Activity in Java.

---

## Prerequisites
- compileSdk 34+
- Material 3 theme

---

## 1. Dependency
```gradle
implementation "androidx.activity:activity:1.9.0"
implementation "org.jetbrains.kotlin:kotlin-stdlib:2.2.20-RC"
```
```Java
EdgeToEdge.enable(this);
````

---

## 📜 License

### Open & Free (No Restrictions)
This project is released as **CC0 1.0 Universal**. You are free to use, modify, and share it for any purpose, including commercial projects—no attribution required, no restrictions.

### Third-Party Libraries
This project may include third-party libraries. Each library is subject to its own license. Please review their licenses if you plan to use them.
