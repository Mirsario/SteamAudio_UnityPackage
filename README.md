# Steam Audio Unity Package

This repository is a simple extraction of Valve Software's [Steam Audio](https://github.com/ValveSoftware/steam-audio/releases) 4.5.3's `.unitypackage` files, with a few patches applied to make it compatible with the modern declarative Unity Package Manager. This was done for the following reasons:
- Intended way of installation, that being manual package extraction, pollutes games' source-control repositories with large binary files.
- Steam Audio is not listed on any Unity Package Manager registry.
- Steam Audio's git tree does not contain a package manifest file, and contains non-meta-backed C++ & Unreal files that distress Unity.

An approach of forking SteamAudio and morphing it into this state was considered (since the original repo also includes native binary files), however every single file in the repo would be needed to be either moved or removed, becoming a maintenance hassle that would outweight the benefit in authenticity. Compare the file tree to a manual `.unitypackage` extraction of your own for safety checks.

## How to add this to your Unity project
- Click the Plus sign in the Package Manager window;
- Select `Add package from git URL...`;
- Paste in `https://github.com/Mirsario/SteamAudio_UnityPackage.git`. Note the `.git` suffix;
- Continue with the fifth bullet-point [in the official documentation](https://valvesoftware.github.io/steam-audio/doc/unity/getting-started.html).

## Modifications
The following changes were applied to files taken out of the `.unitypackage` file:
- The `package.json` manifest was added, to actually make the repository work as a UPM package.
- `SteamAudio/Scripts/Runtime/SteamAudioSettings.cs` was modified to fix its settings asset generation assuming presence at a mutable `Assets/Plugins/SteamAudio` path.
- `LICENSE.md` (Apache License 2.0) was included from the Steam Audio git repository.
- `THIRDPARTY.md` was included from the release zip file, the one which contained the `SteamAudio.unitypackage` file.

## Licensing
- Steam Audio is a property of Valve Software, and is licensed under the `Apache License 2.0`, found in `LICENSE.md`.
- FMOD is a property of Firelight Technologies Pty Ltd. and is subject to its own [special terms](https://fmod.com/licensing). In this package's context, setting the `Audio Engine` property of `Steam Audio Settings` to `FMOD Studio` means distributing FMOD with your game, thus agreeing to [FMOD's End User License Agreement](https://fmod.com/legal) and all of its requirements and restrictions. It is not used by default.
- Licensing of other third-party libraries that come with Steam Audio is described in `THIRDPARTY.md`.
