# Music Player Version 2

This is a easy to use, developer/non-developer friendly Music Player/Music Handler for Unity C#


## Basic usage
1. Attach the MusicPlayer.cs script to your game object.
2. Add Clips to play in Clips.
3. Set your settings.
4. Done!

## Code Usage
1. Attach the MusicPlayer.cs script to your game object.
2. Initialize MusicPlayer using `GetComponent<MusicPlayer>()`.
3. Use in your code.
4. Done!

## API

You can view the source file [MusicPlayer.cs](./MusicPlayer.cs) or use the quick reference below!

| Function                | Description                                                         |
|---------------------------------|---------------------------------------------------------------------|
| ***Next()*** | Calls the next music to be played. (Does NOT auto play if run and not playing) |
| ***Prev()*** |  Calls previous next music to be played. (Does NOT auto play if run and not playing)  |
| ***AddMusic(Clip music)*** | Add Music to the end of the play Clips |
| ***RemoveMusic(Clip music)*** | Remove Music from the Clips List |
| ***Play()*** | Start Playing Music |
| ***Pause()*** | Pause Music |
| ***Stop()*** | Stop Music |
| ***PlayPause()*** |  Plays if currently paused/Never Played, and Pauses if currently Playing |
| ***Rewind()*** | Rewinds music this is the same as Stop() and Play() |
| ***Seek(float timeStampSeconds)*** | This is the same as setting the CurrentTime variable, which sets the current time in the track being played. |
| ***SetLoopBack(float startTimeSeconds, float endTimeSeconds)*** | If for wahtever reason you want to loop back a certain time period (in seconds) you can do that so if you want to loop the 1s and 5s mark in the track you would call SetLoopBack(1, 5) |
| ***UnsetLoopBack()*** | This unsets any currently playing loopback, no side-effects (nothing happens) if there is no loopback set. music_player.UnsetLoopBack() |
| ***IsLoopBackEnabled()*** | Returns if we are currently running a loopback. |
| ***GetCurrentClip()*** | Gets the current clip running. |


```C#
using UnityEngine;

public class EXAMPLE_DONOT_USE_CLASS : MonoBehaviour
{
    MusicPlayer music_player;

    void Start()
    {
        music_player = GetComponent<MusicPlayer>();

        // This is a list, you can do .Add() .Remove() or whatever.
        music_player.Clips.Add(/* put the clip you want to add here */);
        music_player.Clips.Remove(/* put the clip you want to remove here */);
        // this is the audio index you want to start at 0 being the first clip 1 being second etc... 
        music_player.AudioIndex = 0; 
        // Start delay in seconds, this is used with PlayOnStart (see below), and waits that many seconds before playing the clip 
        music_player.StartDelay = 0f;
        // This is play on scene start/scene load, it will immadlty play if StartDelay (see above) is set to 0 seconds.
        music_player.PlayOnStart = false;
        // This just enables shuffling to the music when you call .Next()
        music_player.Shuffle = false;
        // This has 3 values None (no looping), Track (loops the current track), Playlist (loops back on the playlist for every item)
        music_player.LoopMode = RepeatMode.None;
        // This sets the volume for music player by defualt it has a ramp time (see below)
        music_player.Volume = 1.0f;
        // This is how long it takes to go to a volume set so if did music_player.Volume = 0f, it would take VolumeRampTime seconds to fade that way, in this case 1 second.
        // NOTE: Setting VolumeRampTime = 0, turns this feature off.
        music_player.VolumeRampTime = 1.0f; 
        // This sets the playback speed for music player by default it has a ramp time (see below)
        music_player.PlayBackSpeed = 1.0f;
        // This is how long it takes to go to a playback speed set so if did music_player.PlayBackSpeed = 0f, it would take PlaybackRampTime seconds to fade that way, in this case 1 second.
        // NOTE: Setting VolumeRampTime = 0, turns this feature off.
        music_player.PlaybackRampTime = 1f;
        // Fade Time between clips when you are about to end this cross fades clips (if you want that)
        music_player.FadeTime = 0.15f;
        // Max amount of playback history to store.
        music_player.HistoryMax = 50;
        // Get the current track length with this variable
        music_player.TrackLength;
        // Get the curent Time playing in the Song in seconds (EXAMPLE: 140 seconds), you can also SET the current Time with this variable (auto adjusts)
        music_player.CurrentTime;
        // Get if the music player is playing right now, or set if its playing right now (auto adjust).
        music_player.IsPlaying;
        // Get if the music player is paused right now, or set if its paused right now (auto adjust).
        music_player.Paused;
        // Calls the next music to be played. (Does NOT auto play if run and not playing)
        music_player.Next();
        // Calls previous next music to be played. (Does NOT auto play if run and not playing)
        music_player.Prev();
        // Add Music to the end of the play Clips
        music_player.AddMusic();
        // Remove Music from the Clips List
        music_player.RemoveMusic();
        // Start Playing Music
        music_player.Play();
        // Pause Music
        music_player.Pause();
        // Stop Music
        music_player.Stop();
        // Plays if currently paused/Never Played, and Pauses if currently Playing
        music_player.PlayPause();
        // Rewinds music this is the same as Stop() and Play()
        music_player.Rewind();
        // This is the same as setting the CurrentTime variable, which sets the current time in the track being played.
        music_player.Seek();
        // If for wahtever reason you want to loop back a certain time period (in seconds) you can do that so if you want to loop the 1s and 5s mark in the track you would call SetLoopBack(1, 5);
        music_player.SetLoopBack(float startTime, float endTime);
        // This unsets any currently playing loopback, no side-effects (nothing happens) if there is no loopback set.
        music_player.UnsetLoopBack();
        // Returns if we are currently running a loopback.
        music_player.IsLoopBackEnabled();
        // Gets the current clip running.
        music_player.GetCurrentClip();
    }
}
```
