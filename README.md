# EX.NO: 06 – ImageView Animations Using Android Studio

## AIM

To develop an Android application using Android Studio to perform different animation operations on an ImageView, such as Move, Blink, Fade, Clockwise Rotation, Zoom and Slide.

## EQUIPMENTS REQUIRED

- Android Studio (Latest Version)
- Java Programming Language
- Android Emulator

## ALGORITHM

1. Start Android Studio and create a new project using Java.
2. Design the application interface using XML.
3. Add an ImageView to display an image.
4. Create buttons for Move, Blink, Fade, Clockwise, Zoom and Slide operations.
5. Initialize the ImageView and buttons using `findViewById()`.
6. Implement click listeners for each animation button.
7. Use animation properties such as translation, alpha, rotation and scale to perform different animations.
8. Apply the selected animation to the ImageView when the corresponding button is clicked.
9. Display the animation effects in the Android application.
10. Run and test all animation operations.
11. Stop the application.

## PROGRAM

### MainActivity.java

```java
/*
Program to display animation operations on ImageView.
Developed by: Jayani N
Registration Number: 212224100025
*/

package com.example.animatorapp;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;
import android.animation.ObjectAnimator;
import android.animation.ValueAnimator;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    ObjectAnimator animator;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);

        Button move = findViewById(R.id.btnMove);
        Button blink = findViewById(R.id.btnBlink);
        Button fade = findViewById(R.id.btnFade);
        Button clockwise = findViewById(R.id.btnClockwise);
        Button zoom = findViewById(R.id.btnZoom);
        Button slide = findViewById(R.id.btnSlide);
        Button reset = findViewById(R.id.btnReset);

        // Move Animation
        move.setOnClickListener(v -> {
            resetImage();

            animator = ObjectAnimator.ofFloat(
                    imageView, View.TRANSLATION_X, 0f, 150f, 0f);

            startAnimation();
        });

        // Blink Animation
        blink.setOnClickListener(v -> {
            resetImage();

            animator = ObjectAnimator.ofFloat(
                    imageView, View.ALPHA, 1f, 0f);

            animator.setRepeatCount(4);
            animator.setRepeatMode(ValueAnimator.REVERSE);

            startAnimation();
        });

        // Fade Animation
        fade.setOnClickListener(v -> {
            resetImage();

            animator = ObjectAnimator.ofFloat(
                    imageView, View.ALPHA, 1f, 0.1f);

            startAnimation();
        });

        // Clockwise Rotation
        clockwise.setOnClickListener(v -> {
            resetImage();

            animator = ObjectAnimator.ofFloat(
                    imageView, View.ROTATION, 0f, 360f);

            startAnimation();
        });

        // Zoom Animation
        zoom.setOnClickListener(v -> {
            resetImage();

            animator = ObjectAnimator.ofFloat(
                    imageView, View.SCALE_X, 1f, 1.5f, 1f);

            animator.start();

            animator = ObjectAnimator.ofFloat(
                    imageView, View.SCALE_Y, 1f, 1.5f, 1f);

            startAnimation();
        });

        // Slide Animation
        slide.setOnClickListener(v -> {
            resetImage();

            animator = ObjectAnimator.ofFloat(
                    imageView, View.TRANSLATION_Y, 0f, 150f, 0f);

            startAnimation();
        });

        // Reset Animation
        reset.setOnClickListener(v -> resetImage());
    }

    // Start Animation
    void startAnimation() {
        animator.setDuration(1000);
        animator.start();
    }

    // Reset Image Properties
    void resetImage() {

        if (animator != null) {
            animator.cancel();
        }

        imageView.setTranslationX(0f);
        imageView.setTranslationY(0f);
        imageView.setAlpha(1f);
        imageView.setRotation(0f);
        imageView.setScaleX(1f);
        imageView.setScaleY(1f);
    }
}



```

### activity_main.xml

```xml

<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#F5F5F5">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:gravity="center"
        android:padding="16dp">

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="ImageView Animations"
            android:textSize="24sp"
            android:textStyle="bold"
            android:textColor="#222222"
            android:gravity="center"
            android:padding="12dp"/>

        <ImageView
            android:id="@+id/imageView"
            android:layout_width="200dp"
            android:layout_height="200dp"
            android:layout_margin="25dp"
            android:src="@android:drawable/ic_menu_gallery"
            android:scaleType="fitCenter"
            android:contentDescription="Animation Image"/>

        <Button
            android:id="@+id/btnMove"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Move"/>

        <Button
            android:id="@+id/btnBlink"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Blink"/>

        <Button
            android:id="@+id/btnFade"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Fade"/>

        <Button
            android:id="@+id/btnClockwise"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Clockwise"/>

        <Button
            android:id="@+id/btnZoom"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Zoom"/>

        <Button
            android:id="@+id/btnSlide"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Slide"/>

        <Button
            android:id="@+id/btnReset"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Reset"/>

    </LinearLayout>

</ScrollView>


```

## OUTPUT

### 1. Initial Application Screen

<img width="1066" height="977" alt="image" src="https://github.com/user-attachments/assets/7d72b2f3-e2be-4ad2-a369-12d3eba37a06" />
<img width="190" height="416" alt="image" src="https://github.com/user-attachments/assets/b5ca4049-9905-4b4a-9ee5-f843c3a0658f" />


### 2. Move Animation

<img width="185" height="420" alt="image" src="https://github.com/user-attachments/assets/072f9edd-e332-46ca-bc7d-439adb9fa3c4" />


### 3. Blink Animation

<img width="190" height="422" alt="image" src="https://github.com/user-attachments/assets/a3e7e5bb-7cd9-4532-98ef-71615e30886a" />


### 4. Fade Animation

<img width="190" height="413" alt="image" src="https://github.com/user-attachments/assets/e203b771-4bc5-4742-a99f-121d2beca2b9" />


### 5. Clockwise Rotation

<img width="195" height="417" alt="image" src="https://github.com/user-attachments/assets/a70f57f0-629a-4e1d-a37e-b36adf88223b" />


### 6. Zoom Animation

<img width="186" height="412" alt="image" src="https://github.com/user-attachments/assets/1693b7a5-fbc3-4907-a145-4f464ee99a02" />


### 7. Slide Animation

<img width="186" height="418" alt="image" src="https://github.com/user-attachments/assets/ac8e43e4-a769-436d-ba9e-8e1cd8b7eb03" />


## RESULT

Thus, an Android application was successfully developed using Java in Android Studio to perform Move, Blink, Fade, Clockwise Rotation, Zoom and Slide animations on an ImageView.
