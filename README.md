
<img src="/Screenshot_2019-12-15-00-27-27-780_com.mydreamworld.audiocontorll.jpg" height="500px" weidth="300px">

# code explanation<br/>

It is actually very simple audio and volume control app.Here , I have used to two SeekBar for one is volume and another one is for audio stream control.<br/>

<B>MediaPlayer mplayer=MediaPlayer.create(this,R.raw.cartoon);</B><br/>
MediaPlayer -- media player is a class name.<br/>
cartoon-- is audio file name.<br/>

# important lines in this code is<br/>
      
        int maxVolume=audioManager.getStreamMaxVolume(AudioManager.STREAM_MUSIC);
        getting max.volume of the android system
      
        int currentVolume=audioManager.getStreamVolume(AudioManager.STREAM_MUSIC);
        getting current volume of the android system.
        
        volumecontroll.setMax(maxVolume);
        volumecontroll.setProgress(currentVolume);
        
        Those two line are used to assign max.volume and current voume to the media player.Now, we are going to control the audio stream. By the following code.
      volumecontroll.setOnSeekBarChangeListener
      This line will automatically override the following methods
      
      1.onProgressChanged
      2.onStartTrackingTouch
      3.onStopTrackingTouch
     
      Here I used only the # onProgressChanged method. Inside this method, i used audioManager.setStreamVolume(AudioManager.STREAM_MUSIC,progress,0);to set changing volume level to the media player seekbar.
      Next initiate the second seekbar by using it's ID. Then Get the max. duration of the audio by the following code
                             scrubber.setMax(mplayer.getDuration());
   so now almost got the actual length of the audio file. By using the <i>Timer()</i> we can set any position as current state of the audio stream.and place the following line inside the run() method.
                           scrubber.setProgress(mplayer.getCurrentPosition());
Then call <i>setOnSeekBarChangeListener()</i> method. i already explained it's default override methods. So we are going to access only the <i>onProgressChanged()</i> method. done. set <i>mplayer.seekTo(progress);</i>

Now almost all the line of the codes i explained clearly. If you had any doubt in audio control topic feel free to ask me. or you can refer my code. I hope it will useful for many people.
