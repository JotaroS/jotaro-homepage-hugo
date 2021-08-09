+++
# Date this page was created.
date = "2020-08-28"

# Project title.
title = "SpeechIOForUnity"

# Project summary to display on homepage.
summary = "A ready-to-use Unity plugin for Speech Input/Output using native Speech API of both Apple macOS and MS Windows."

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = "speechio.png"

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["programming"]

# Does the project detail page use math formatting?
math = false

# Wide header image file
[header]
image = "speechio.png"
caption = "speechioforunity"

+++

A ready-to-use Unity plugin for Speech Input/Output using native Speech API of <i>both</i> Apple macOS and MS Windows.

[github project page is here.](https://github.com/HassoPlattnerInstituteHCI/SpeechIOForUnity)

Author: Jotaro Shigeyama and Thijs Roumen


## Features
- Custom command speech input
- Support for various speed / language.
- Async/await-based interaction design.

```example.cs

SpeechOut speechOut = new SpeechOut();
SpeechIn  speechIn  = new SpeechIn(OnRecognized);

void Start(){
    Dialog();
}

async void Dialog(){
    await speechOut.Speak("Hello!");
    await speechIn.Listen(new string[] { "Hello", "Hi", "Hey" });
    await speechOut.Speak("How are you doing?");
    await speechIn.Listen(new string[] { "I'm fine", "Nah", "I'm Sick" });
    //...
}

```

This project repo contains

- Unity project (this repo, tested with v.2019.3.0a8) 
- XCode project NSSpeechForUnity (author: Jotaro Shigeyama)
- Visual Studio project WindowsVoiceProject originally from here (https://chadweisshaar.com/blog/2015/07/02/microsoft-speech-for-unity/)
- Unity project contains pre-built `.dll` and `.bundle` from above source project.

## Installation

This plugin works and tested on macOS Catalina or above, and Windows 10 (Windows 8 is not supported).

### OS setup

Right now English / Dutch / German / Japanese are supported. You need to install necessary language module from your OS setting.

### Unity

Just simply grab all Scripts, Plugins (and if Scenes if you need) to your own Unity project file.

### Potential installation issue for macOS

Some macOS users will experience broken speech input due to missing dictation kits: mostly because of bug on Apple. If you encounter some issue on speech input, please try these.

- make sure your native voice command system works (System Preferences > Accessibility > Voice Command, enabling voice command will invoke macOS system voice command input windows.)
  - Go to "Preferences > Accessibility > Sound Control > Language" and install language pack.
- In case of macOS have some buggy issues: Try switching your OS language to another, then try to install your desired voice command module (macOS will prompt you to download missing dictation model.)
- Make sure your macOS is the latest version
- Try rebooting the system.

## dev-Installation

- XCode (mac)
- Visual Studio (win, latest Windows SDK required)

### Testing your NSSpeechRecognizer

tested on Apple Swift version 5.1.3

```
cd NSSpeechTest
swift run
```

### Using in your own Unity package

- Build NSSpeechForUnity in XCode.
- Copy generated `.bundle` file in `Assets/Plugins` of your Unity project.

### Modifying voice command dictionary

See `MyMacSpeechScript.cs`.

## Documentation

coming soon.

Your feedback is welcome!