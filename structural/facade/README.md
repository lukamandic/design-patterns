# Facade

Okay, imagine you have a really cool video game, but it's really complicated to play. There are lots of different controls and settings that you have to use to make things happen in the game.

Now, imagine you have a friend who's never played this game before, and they're really excited to try it out. They ask you how to play the game, but you know that if you start explaining every little thing to them, they'll get overwhelmed and confused really quickly.

So instead, you decide to simplify things for your friend by showing them a simple set of controls that will let them do the most important things in the game. You might even make a little cheat sheet for them that they can refer to if they forget what to do.

In programming, we have something called the Facade pattern, which is kind of like that cheat sheet for your friend. It's a way of simplifying a complex system by providing a simplified interface that hides all the complicated details underneath.

So instead of having to deal with all the complex code and settings that make up a system, we can just use the simple interface provided by the Facade pattern to get things done. It's like having a friendly face that makes everything easier and more approachable.

## Code

```ts
class AudioPlayerFacade {
  private audioPlayer: AudioPlayer;
  private volumeControl: VolumeControl;
  private trackSelector: TrackSelector;
  private playbackSpeedControl: PlaybackSpeedControl;

  constructor() {
    this.audioPlayer = new AudioPlayer();
    this.volumeControl = new VolumeControl();
    this.trackSelector = new TrackSelector();
    this.playbackSpeedControl = new PlaybackSpeedControl();
  }

  playTrack(track: string) {
    this.trackSelector.selectTrack(track);
    this.volumeControl.setVolume(50);
    this.playbackSpeedControl.setSpeed(1.0);
    this.audioPlayer.play();
  }

  pause() {
    this.audioPlayer.pause();
  }

  stop() {
    this.audioPlayer.stop();
  }
}

const audioPlayer = new AudioPlayerFacade();

// Play a track
audioPlayer.playTrack("Awesome Song");

// Pause the track
audioPlayer.pause();

// Stop the track
audioPlayer.stop();

```