# Ex.No:3 Develop a simple application to play and control the audio file in android studio.


## AIM:

To develop a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as audiofile and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml and create start,pause and stop button.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to play and control the audio file”.
Developed by: Venkatesh A
Registeration Number : 212225040485
*/
```
### activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Simple Audio Player"
        android:textSize="20sp"
        android:layout_marginBottom="30dp"/>

    <Button
        android:id="@+id/btnPlay"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PLAY"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnPause"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PAUSE"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnStop"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="STOP"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

</LinearLayout>
```
### MainActivity.java
```
package com.example.audioplayer;

import androidx.appcompat.app.AppCompatActivity;
import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private MediaPlayer mediaPlayer;
    private Button btnPlay, btnPause, btnStop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize buttons
        btnPlay = findViewById(R.id.btnPlay);
        btnPause = findViewById(R.id.btnPause);
        btnStop = findViewById(R.id.btnStop);

        // Create MediaPlayer
        mediaPlayer = MediaPlayer.create(this, R.raw.song);

        // If using assets folder instead, use:
        // mediaPlayer = new MediaPlayer();
        // try {
        //     mediaPlayer.setDataSource("file:///android_asset/audio.mp3");
        //     mediaPlayer.prepare();
        // } catch (Exception e) {
        //     e.printStackTrace();
        // }

        // PLAY Button
        btnPlay.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null && !mediaPlayer.isPlaying()) {
                    mediaPlayer.start();
                    showToast("Playing audio...");
                }
            }
        });

        // PAUSE Button
        btnPause.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null && mediaPlayer.isPlaying()) {
                    mediaPlayer.pause();
                    showToast("Audio paused");
                }
            }
        });

        // STOP Button
        btnStop.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null) {
                    if (mediaPlayer.isPlaying()) {
                        mediaPlayer.stop();
                    }
                    mediaPlayer.reset();
                    try {
                        mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.song);
                    } catch (Exception e) {
                        e.printStackTrace();
                    }
                    showToast("Audio stopped");
                }
            }
        });
    }

    private void showToast(String message) {
        Toast.makeText(this, message, Toast.LENGTH_SHORT).show();
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        if (mediaPlayer != null) {
            mediaPlayer.release();
        }
    }
}
```
## OUTPUT
<img width="1486" height="602" alt="Screenshot 2026-08-27 113902" src="https://github.com/user-attachments/assets/1c4006f2-bf5b-44ea-bce6-bd726a6072ed" />
<img width="1471" height="602" alt="Screenshot 2026-08-27 113841" src="https://github.com/user-attachments/assets/fd05bf95-9035-4958-afcc-389f53187717" />
<img width="1620" height="603" alt="Screenshot 2026-08-27 113805" src="https://github.com/user-attachments/assets/88a506ab-6772-4186-a430-4de24cd1220f" />




## RESULT
   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.
