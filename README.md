### myproject
##Step-1
In this application, we require three buttons. Each of them will have a different purpose. The three buttons will be to play the sound, pause it, and stop it.
For our ease of use, we will add the linear layout first and drop the three buttons inside it.


##Step-2
In activity.main xml we have to add the following code:


<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="play"
        android:text="Play" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="pause"
        android:text="Pause" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="stop"
        android:text="Stop" />
</LinearLayout>


![one](https://user-images.githubusercontent.com/39096090/48328630-e0caff80-e612-11e8-9928-7ec617f5a015.JPG)



## Step-3

res -> new-> android resource directory -> select raw

 ## step 4
 
 raw-> add songs
 
 ## step 5
 
 add the java code in main activity.java
 
 package com.example.nayan.myapplication;

import android.media.MediaPlayer;
import android.os.Bundle;
import android.os.Environment;
import android.app.Activity;
import android.view.Menu;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends Activity {
    MediaPlayer player;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

    }

    public void play(View view) {
        if ((player == null)) {
            player = MediaPlayer.create(this, R.raw.song);
            player.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
                @Override
                public void onCompletion(MediaPlayer mediaPlayer) {

                }
            });
        }
    }

    public void pause(View view) {
        if (player != null) {
            player.pause();
        }
    }

    public void stop(View view) {
        stopPlayer();
    }

    private void stopPlayer() {
        if (player != null) {
            player.release();
            player = null;
            Toast.makeText(this, "mediaplayer released", Toast.LENGTH_SHORT).show();
        }

    }
    protected  void onstop(){
        super.onStop();
        stopPlayer();
    }
}

##output
 
![media1 1](https://user-images.githubusercontent.com/39096090/48329139-4d46fe00-e615-11e8-83bd-a9bacc978574.gif)
