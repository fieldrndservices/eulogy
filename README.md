# Eulogy: A dead simple LabVIEW&trade; add-on and toolkit for refactoring legacy code

[About](#what-is-eulogy) | [Installation](#installation) | [Documentation](#documentation) | [Tests](#tests) | [License](#license)

## What is Eulogy?

[Eulogy](http://sine.ni.com/nips/cds/view/p/lang/en/nid/215388) is a [LabVIEW&trade;](http://www.ni.com/labview) add-on and toolkit for refactoring legacy code in LabVIEW projects.

## Dependencies

- LabVIEW 2015 or newer (for installation and usage)
- LabVIEW 2017 or newer (for development)
- [VIPM Pro](https://vipm.jki.net/get) (only for automated builds)
- [VIPM API](https://support.jki.net/hc/en-us/articles/214136183-VIPM-API) (only for automated builds)

## Installation

A VI Package (VIP) is available on the [National Instruments (NI)](http://www.ni.com) [LabVIEW Tools Network](http://www.ni.com/labview-tools-network/). It is recommended to use the [VI Package Manager](https://vipm.jki.net/) published by [JKI](http://jki.net/) to install and update the library.

## Build

### VIPM Pro

If VIPM Pro is available, then open the `Eulogy.lvproj` file in any version of LabVIEW newer than 2015 and run the `Build.vi` located in the `Scripts` virtual folder of the Project Explorer window.

### VIPM Free

1. Start LabVIEW 2017 or newer and open the Eulogy.lvproj file.
2. From the Project Explorer window, File->Save for Previous Version..., a new dialog will appear.
3. Select "15.0" from the drop down menu.
4. Click "Save...". A new dialog will open.
5. Create the `target\15.0` folder hierarchy in the project root, i.e. same folder as the Eulogy.lvproj file, if it does not already exists.
6. Click "Save".
7. Close LabVIEW 2017 or newer and the Eulogy.lvproj file.
8. Start LabVIEW 2015.
9. Open the `<project root>\target\15.0\Eulogy.lvproj` file. Do NOT open the project in any other version of LabVIEW.
10. Build each Source Distribution under the "Build Specifications" tree item from within the Project Explorer. The output of each build will be available in `<project root>\target\15.0\builds`.
11. Open the `<project root>\target\15.0\configs\Eulogy.vipb` file in VIPM.
12. Build the VI package with VIPM. The output will be available at `<project root>\target\15.0\packages`. Do NOT modify anything in the package build specification, but ensure the "2015" version of LabVIEW is selected in the upper, right-hand corner of the VIPM application window.
13. Close VIPM.
14. Close LabVIEW 2015 and the `<project root>\target\15.0\Eulogy.lvproj` file.

## Documentation

See the in-app LabVIEW Help system for more information and documentation about using the library after it has been installed, or visit the [web-based documentation](https://help.fieldrndservices.com/eulogy). Examples are also available within the LabVIEW development environment using the `Help->Find Examples...` menu item.

## Tests

Tests are written in LabVIEW using the [Caraya](https://github.com/JKISoftware/Caraya) unit testing framework and included in the project via the `Tests` project library (.lvlib) and the `tests` on-disk folder. To run the tests, open the `Eulogy.lvproj` file found in the root folder of the source code distribution in the LabVIEW Development Environment (32-bit or 64-bit) and run the `Run All` VI that is found in the `Tests` project library. The tests are organized in a hierarchy based on their relationship to the source code. There is a `Run All` VI within each child project library (.lvlib) to run all of the tests for a specific portion of the project.

## License

See the `docs` folder for all information about licensing and copyright.

