# Flatpack version of drumgizmo using flathub's LV2 base extension

[DrumGizmo](https://www.drumgizmo.org) is an open source, multichannel, multilayered, cross-platform drum plugin and stand-alone application. It enables you to compose drums in midi and mix them with a multichannel approach. It is comparable to that of mixing a real drumkit that has been recorded with a multimic setup.

Features include:

- Stand-alone, Lv2 and VSTi versions available
- Open drumkit file format, allowing the community to create their own drumkits
- Drum velocity, allowing for several different hit velocities for each drum
- Multichannel output, making it possible to mix it just the way you would a real drumkit
- Optional built-in humanizer, analyzing the midi notes, adjusting velocities on-the-fly
- Stand-alone midi renderer, generating .wav files, 1 for each channel
- Stand-alone midi input, making it possible to use DrumGizmo as a software sampler for an electronic drumkit

This is a **flatpack version of drumgizmo** using `org.freedesktop.LinuxAudio.BaseExtension` available in flathub. It can be used to make drumgizmo LV2 plugin available for the flathub's versions of Ardour and/or Bitwig.

## Usage

- Add a midi track to Ardour/BitWig and add the DrumGizmo plugin to this track. Open the GUI and select the drumkit and midimap to use (download them at <https://www.drumgizmo.org/wiki/doku.php?id=kits>). The drumkit is loaded in the background so it might take a while before it is fully ready to use.
- Add 16 mono audio tracks or mono audio busses and connect the 16 output from the midi channel to each of these.
  > **Important**: The midi track has a 16 channel panner that is useless in the DrumGizmo context. Disable/bypass it. If you fail to do this DrumGizmo will seemingly only output to channel 5.
- Add some midi notes to the DrumGizmo tracks and play away.
- It is also possible to play the drums using the piano roll.

## Install

You will need `flatpack` and `flatpak` builder. Install them using your distribution's package manager (e.g. `apt`, `dnf`, or `pacman`)

> You should have as well flathub configured as a source of flatpaks. Assuming you already have flatpak in your system, run
>
> ```console
> flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
> ```

Install the Freedesktop 22.08 runtime and SDK if not already installed with:

```console
flatpak install flathub org.freedesktop.Platform//22.08 org.freedesktop.Sdk//22.08
```

Install the `stable` version of `org.freedesktop.LinuxAudio.BaseExtension` if not already installed with:

```console
flatpak install flathub org.freedesktop.LinuxAudio.BaseExtension
```

Now, clone this repository, and from the project's root run:

```console
git submodule update --remote --merge
sudo flatpak-builder --system --install --force-clean build-dir org.freedesktop.LinuxAudio.Plugins.drumgizmo.json
```

That's all! Enjoy drumming!
