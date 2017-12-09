# Fable.Import.WebMIDI


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
[![Travis Badge](https://travis-ci.org/magicmonty/Fable.Import.WebMIDI.svg?branch=master)](https://travis-ci.org/magicmonty/Fable.Import.WebMIDI) | [![Build status](https://ci.appveyor.com/api/projects/status/github/magicmonty/Fable.Import.WebMIDI?svg=true)](https://ci.appveyor.com/project/magicmonty/Fable.Import.WebMIDI)
[![Build History](https://buildstats.info/travisci/chart/magicmonty/Fable.Import.WebMIDI)](https://travis-ci.org/magicmonty/Fable.Import.WebMIDI/builds) | [![Build History](https://buildstats.info/appveyor/chart/magicmonty/Fable.Import.WebMIDI)](https://ci.appveyor.com/project/magicmonty/Fable.Import.WebMIDI)


## Nuget

Stable | Prerelease
--- | ---
[![NuGet Badge](https://buildstats.info/nuget/Fable.Import.WebMIDI)](https://www.nuget.org/packages/Fable.Import.WebMIDI/) | [![NuGet Badge](https://buildstats.info/nuget/Fable.Import.WebMIDI?includePreReleases=true)](https://www.nuget.org/packages/Fable.Import.WebMIDI/)w