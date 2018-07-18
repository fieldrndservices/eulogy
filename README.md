# Eulogy: A dead simple LabVIEW&trade; add-on and toolkit for refactoring legacy code

[About](#what-is-eulogy) | [Installation](#installation) | [Documentation](#documentation) | [Tests](#tests) | [License](#license)

## What is Eulogy?

[Eulogy]() is a [LabVIEW&trade;](http://www.ni.com/labview) add-on and toolkit for refactoring legacy code in LabVIEW projects.

## Dependencies

- LabVIEW 2015 or newer (for installation and usage)
- LabVIEW 2017 or newer (for development)
- [Caraya](https://github.com/JKISoftware/Caraya) (for development)
- [HTML Help Workshop](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/htmlhelp/microsoft-html-help-downloads) (for compiling the help documentation)
- [VIPM Pro](https://vipm.jki.net/get) (only for automated builds)
- [VIPM API](https://support.jki.net/hc/en-us/articles/214136183-VIPM-API) (only for automated builds)

## Installation

A VI Package (VIP) is available on the [National Instruments (NI)](http://www.ni.com) [LabVIEW Tools Network](http://www.ni.com/labview-tools-network/). It is recommended to use the [VI Package Manager](https://vipm.jki.net/) published by [JKI](http://jki.net/) to install and update the library.

## Build

Eulogy is made of several components: Bookmark Manager (Graveyard), Shortcut Menu Plugin, Quick Drop Plugins, Tools Menu, and a Toolkit API. Each component has a Source Distribution build specification within the project. The destination of each source distribution build is the `builds` folder relative to the project root, i.e. same folder as the `Eulogy.lvproj` file. Additionally, the output for the compiled help documentation is also the `builds` folder. The `builds` folder should _not_ be included in the version control repository. A `Build.vi` script is available in the `Scripts.lvlib` project library that will build all of the components and the help documentation automatically (VIPM Pro is not needed).

The VI Package Build (.vipb) specification, located in the `configs` folder relative to the project root, is configured for the package source to be `builds` folder. Thus, the Source Distribution for each component must be built **before** opening the `Eulogy.vipb` file in the <abbr title="VI Package Manager">VIPM</abbr>; otherwise, the package configuration will be lost.

### Packaging using VIPM Pro (recommended)

If VIPM Pro is available, then open the `Eulogy.lvproj` file in any version of LabVIEW newer than 2015 and run the `Package.vi` located in the `Scripts` project library of the Project Explorer window. Ensure all dependencies are installed before running the `Package.vi` script.

### Packaging using VIPM Free

If VIPM Pro is _not_ available, then the following steps can be executed to do essentially the same thing as the `Package.vi` script. Ensure all dependencies, except VIPM Pro and the VIPM API, are installed before completing these steps.

1. Start LabVIEW 2017 or newer and open the `Eulogy.lvproj` file.
2. From the Project Explorer window, "File->Save for Previous Version...", a new dialog will appear.
3. Select "15.0" from the drop down menu.
4. Click "Save...". A new dialog will open.
5. Create the `target\15.0` folder hierarchy in the project root, i.e. the same folder as the `Eulogy.lvproj` file, if it does not already exists.
6. Click "Save".
7. Close LabVIEW 2017 or newer and the `Eulogy.lvproj` file.
8. Start LabVIEW 2015.
9. Open the `<project root>\target\15.0\Eulogy.lvproj` file. Do NOT open the project in any other version of LabVIEW.
10. Run the `Build.vi` in the `Scripts` project library to build each Source Distribution under the "Build Specifications" tree item and the compiled help documentation file (`Eulogy.chm`). The output of each build will be available in `<project root>\target\15.0\builds`.
11. Open the `<project root>\target\15.0\configs\Eulogy.vipb` file in VIPM.
12. Build the VI package with VIPM. The output will be available at `<project root>\target\15.0\packages`. Do NOT modify anything in the package build specification, but ensure the "2015" version of LabVIEW is selected in the upper, right-hand corner of the VIPM application window.
13. Close VIPM.
14. Close LabVIEW 2015 and the `<project root>\target\15.0\Eulogy.lvproj` file.

## Documentation

See the in-app LabVIEW Help system for more information and documentation about using the library after it has been installed, or visit the [web-based documentation](https://help.fieldrndservices.com/eulogy). Examples are also available within the LabVIEW development environment using the "Help->Find Examples..." menu item.

## Tests

Tests are written in LabVIEW using the [Caraya](https://github.com/JKISoftware/Caraya) unit testing framework and included in the project via the various `Tests.lvlib` project libraries and the `tests` on-disk folder. To run the tests, open the `Eulogy.lvproj` file found in the project root in the LabVIEW Development Environment (32-bit or 64-bit) and run the `Test.vi` script located in the `Scripts.lvlib` project library. This will run all of the tests defined in all of the various `Tests.lvlib` project libraries located in the project. 

The tests are organized in a hierarchy based on their relationship to the source code. The `Tests.lvlib` project library for the "My Computer" tree item in the Project Explorer are generally for integration-style tests, i.e. tests for the public API of the toolkit and components. The `Tests.lvlib` project libraries found within each component's project library (`Bookmark Manager.lvlib`, `Toolkit.lvlib`, etc.) are generally for unit-style tests, i.e. tests for private/support VIs of the components. None of the tests are included in the VIP distribution. They are only included with the source code.

## License

Eulogy is licensed under either the [MIT license](https://opensource.org/licenses/MIT) or the [Apache-2.0 license](http://www.apache.org/licenses/LICENSE-2.0). See the `docs` folder for more information about licensing and copyright. 

