Please read [CONTRIBUTING](https://github.com/cucumber/gherkin/blob/master/CONTRIBUTING.md) first.
You should clone the [cucumber/gherkin](https://github.com/cucumber/gherkin) repo if you want
to contribute.

## Run tests

### OS X/Linux

Install dependencies:

    brew cask install mono-mdk
    brew install xamarin-studio

Just run `make` from this directory.

### Windows

Open `Gherkin.CSharp.sln` from this directory in Visual Studio 2013 and build.

Alternatively, run `msbuild` from this directory.

Keep in mind that this will only run unit tests. The acceptance tests are only
run when you build with `make`.

## Make a release

If this is your first time, read through NuGet's guidelines for
[Creating and Publishing a Package](https://docs.nuget.org/create/creating-and-publishing-a-package).

    # Replace X.Y.Z with the version
    # Change version in `Gherkin.NuGetPackages\Gherkin.nuspec`
    git clean -dfx
    mono .nuget/NuGet.exe restore Gherkin.CSharp.sln
    xbuild /p:Configuration=Release
    mono .nuget/NuGet.exe pack Gherkin.NuGetPackages/Gherkin.nuspec
    mono .nuget/NuGet.exe push Gherkin.X.Y.Z.nupkg
    git commit -am "Release X.Y.Z"
    git tag -a -m "Version X.Y.Z" vX.Y.Z
    git push
    git push --tags
