# Balloon Party
This mobile game, developed in Unity, uses the microphone to let players blow up a balloon. On the screen, players will see a balloon and a silhouette indicating the target area where the balloon should be kept blown up for a varying amount of time each round. The challenge is to maintain the balloon within the silhouette for the required duration to progress through the levels.

<p align="center">
     <img src="https://github.com/rosibeluseda/Ballon_Party/assets/145386489/d9a630b9-e774-48db-9b17-ddbec287f2c6" alt="preview game" width="300px">
</p>


# Microphone Functionality
The game will prompt the player to set up the microphone before starting. If the player does not configure the microphone's sensitivity, the game will not be able to start. The initialization process includes the following steps:
```csharp
 void Start()
{
     InitializeMicrophone();
     _scaleFactor = PlayerPrefs.GetFloat("SliderValue");// Scale factor to adjust volume sensitivity.
     confettiEffect.Stop(true, ParticleSystemStopBehavior.StopEmittingAndClear);
     menuButton.onClick.AddListener(() => LoadScene("MainScreen"));
}
```
This code ensures that the microphone is initialized and the volume sensitivity is adjusted according to the player's settings. It also sets up a button to navigate back to the main screen and controls the confetti effect.
Once in play mode, the microphone will detect noice to blow the balloon. 

```csharp
void InitializeMicrophone()
{
     if (Microphone.devices.Length > 0)
     {
            _microphoneInput = Microphone.Start(null, true, 1, 44100);
            while (!(Microphone.GetPosition(null) > 0)) { } // Wait until the microphone has started
            _isMicrophoneInitialized = true;
     }
     else
             Debug.LogError("No microphone detected.");
}
```

# Particle System Unity
In my game, I used Unity's Particle System to create various visual effects that enhance the overall experience. For the intro and tutorial screens, I created a bunch of floating balloons to add a playful and welcoming atmosphere. Additionally, I implemented a confetti effect to celebrate when the player wins, adding a festive and rewarding visual cue.
<p align="center">
     <img src="https://github.com/rosibeluseda/Ballon_Party/assets/145386489/610a35a3-c8ec-47dd-85a3-b7a7922571b2" alt="particles" width="300px">
</p>
