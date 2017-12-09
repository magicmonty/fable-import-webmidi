# Fable.Import.WebMIDI

Fable bindings for [Web MIDI](https://www.w3.org/TR/webmidi/)

install with DotNet:
```
dotnet add package Fable.Import.WebMIDI
```

or with Paket:
```
paket add Fable.Import.WebMIDI
```

### Usage

Example in Elmish:

```fsharp
open Fable.Import.WebMIDI

type Model = { MIDIAccess: IMIDIAccess option 
               ErrorMessage: string option }

type Msg = | MIDISuccess of IMIDIAccess
           | MIDIError of exn
           | MIDIStateChanged of IMIDIConnectionEvent

let init () : Model*Cmd<Msg> =
  { MIDIAccess = None 
    ErrorMessage = None }, Cmd.ofPromise MIDI.requestAccess [ Sysex true ] MIDISuccess MIDIError 

let update (msg: Msg) (model: Model) : Model*Cmd<Msg> = 
  match msg with
  | MIDISuccess of midiAccess ->
    let stateChangeSub dispatch =
      let onStateChange ev =
        dispatch (MIDIStateChanged ev)

      midiAccess.OnStateChange <- onStateChange

    { model with MIDIAccess = Some midiAccess }, Cmd.ofSub stateChangeSub
  | MIDIError of ex ->
    { model with ErrorMessage = Some ex.Message }, Cmd.none
  | MIDIStateChanged ev ->
    printfn "MIDI state changed"
    model, Cmd.none

...

```

### Building

Make sure the following **requirements** are installed in your system:

* [dotnet SDK](https://www.microsoft.com/net/download/core) 2.0.2 or higher
* [node.js](https://nodejs.org) 6.11 or higher
* [yarn](https://yarnpkg.com)
* [Mono](http://www.mono-project.com/) if you're on Linux or macOS.

Then you just need to type `./build.cmd` or `./build.sh`

### Release

In order to push your package to [nuget.org][https://nuget.org] you need to add your API keys to `NUGET_KEY` environmental variable.
You can create a key [here](https://www.nuget.org/account/ApiKeys).

- Update RELEASE_NOTES with a new version, data and release notes [ReleaseNotesHelper](http://fake.build/apidocs/fake-releasenoteshelper.html).
Ex:

```
#### 0.2.0 - 30.04.2017
* FEATURE: Does cool stuff!
* BUGFIX: Fixes that silly oversight
```


- You can then use the Release target. This will:
  - make a commit bumping the version: Bump version to 0.2.0
  - publish the package to nuget
  - push a git tag

`./build.sh Release`



MacOS/Linux | Windows
--- | ---
[![Travis build status](https://travis-ci.org/magicmonty/fable-import-webmidi.svg?branch=master)](https://travis-ci.org/magicmonty/fable-import-webmidi) | [![AppVeyor Build status](https://ci.appveyor.com/api/projects/status/github/magicmonty/fable-import-webmidi?svg=true)](https://ci.appveyor.com/project/magicmonty/fable-import-webmidi)
[![Travis Build History](https://buildstats.info/travisci/chart/magicmonty/fable-import-webmidi)](https://travis-ci.org/magicmonty/fable-import-webmidi/builds) | [![AppVeyor Build History](https://buildstats.info/appveyor/chart/magicmonty/fable-import-webmidi)](https://ci.appveyor.com/project/magicmonty/fable-import-webmidi/history)


## Nuget

Stable | Prerelease
--- | ---
[![NuGet Badge](https://buildstats.info/nuget/Fable.Import.WebMIDI)](https://www.nuget.org/packages/Fable.Import.WebMIDI/) | [![NuGet Badge](https://buildstats.info/nuget/Fable.Import.WebMIDI?includePreReleases=true)](https://www.nuget.org/packages/Fable.Import.WebMIDI/)