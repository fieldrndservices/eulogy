# Eulogy: A dead simple LabVIEW&trade; add-on and toolkit for refactoring legacy code

[Eulogy](http://sine.ni.com/nips/cds/view/p/lang/en/nid/217170) is a [LabVIEW&trade;](http://www.ni.com/labview) add-on and toolkit for refactoring legacy code in LabVIEW projects.

## Table of Contents

- [Dependencies](#dependencies)
  - [Installation](#dependencies-installation)
  - [Development](#dependencies-development)
- [Installation](#installation)
- [Build](#build)
  - [Packaging using VIPM Pro (recommended)](#packaging-using-vipm-pro-recommended)
  - [Packaging using VIPM Free](#packaging-using-vipm-free)
- [Documentation](#documentation)
- [Tests](#tests)
- [License](#license)

## Dependencies

### Installation <a name="dependencies-installation"/>

- LabVIEW 2015 or newer (All systems)

### Development <a name="dependencies-development"/>

- [Caraya](http://sine.ni.com/nips/cds/view/p/lang/en/nid/215909) (for development)
- [HTML Help Workshop](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/htmlhelp/microsoft-html-help-downloads) (for compiling the help documentation)
- [JKI State Machine](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209025)
- LabVIEW 2015 or newer (for building)
- LabVIEW 2018 or newer (for development)
- Labricator (only for automated builds, private package available upon request)
- [OpenG Array Library](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209027)
- [OpenG File Library](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209027)
- [VIPM Pro](https://vipm.jki.net/get) (only for automated builds)
- [VIPM API](https://support.jki.net/hc/en-us/articles/214136183-VIPM-API) (only for automated builds)

The Caraya, JKI State Machine, OpenG Array Library, OpenG File Library, and VIPM API must be installed for all versions of LabVIEW (2015 and 2018) to avoid errors during automated builds.

## Installation

A [VI Package (VIP)](https://www.vipm.io/package/field_rnd_services_eulogy/) is available at [VIPM.io](https://www.vipm.io). The recommended installation instructions are to:

1. Navigate to the [Eulogy package](https://www.vipm.io/package/field_rnd_services_eulogy/) at [VIPM.io](https://www.vipm.io/).
2. Click on the _Install_ button to the right. The [VI Package Manager (VIPM)](https://www.vipm.io/download/) (freely available from [JKI](https://jki.net)) will start automatically.
3. Follow the on-screen instructions to complete the installation.

Alternatively, the toolkit can be installed by: (i) downloading the source code and building the VIP, (ii) downloading a VIP from the [releases](https://github.com/fieldrndservices/eulogy/releases) section of this project, or (iii) manually copying the VIs from the source code into a project.

## Build

Eulogy is made of several components: Bookmark Manager (Graveyard), Shortcut Menu Plugin, Quick Drop Plugins, Tools Menu, and a Toolkit API. Each component has a Source Distribution build specification within the project. The destination of each source distribution build is the `builds` folder relative to the project root, i.e. same folder as the `Eulogy.lvproj` file. Additionally, the output for the compiled help documentation is also the `builds` folder. The `builds` folder should _not_ be included in the version control repository. A `Build.vi` script is available in the `Scripts.lvlib` project library that will build all of the components and the help documentation automatically (VIPM Pro is not needed).

The VI Package Build (.vipb) specification, located in the `configs` folder relative to the project root, is configured for the package source to be `builds` folder. Thus, the Source Distribution for each component must be built **before** opening the `Eulogy.vipb` file in the <abbr title="VI Package Manager">VIPM</abbr>; otherwise, the package configuration will be lost.

### Packaging using VIPM Pro (recommended)

__Important__, if creating a package for LabVIEW 2015 from LabVIEW 2018, the [VI Server TCP/IP ports](http://zone.ni.com/reference/en-XX/help/371361P-01/lvhowto/configuring_the_vi_server/) must be different for each version of LabVIEW and verified with the [VIPM](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA00Z000000P9YmSAK) application _before_ proceeding. An error will occur when the VIPM is started if both LabVIEW 2015 and 2018 are running at the same time. Basically, VIPM will not know which VI server to use if both versions of LabVIEW are using the same TCP/IP port.

If VIPM Pro is available, then open the `Eulogy.lvproj` file in any version of LabVIEW newer than 2015 and run the `Package.vi` located in the `Scripts` project library of the Project Explorer window. Ensure all dependencies are installed before running the `Package.vi` script.

Note, the version number for the package is set in the `configs\Eulogy.vipb` file. The version number in the VIP build specification file should be modified and saved _before_ running the `Package.vi` script.

### Packaging using VIPM Free

If VIPM Pro is _not_ available, then the following steps can be executed to do essentially the same thing as the `Package.vi` script. Ensure all dependencies, except VIPM Pro and the VIPM API, are installed before completing these steps.

1. Start LabVIEW 2018 or newer and open the `Eulogy.lvproj` file.
2. From the Project Explorer window, **File>>Save for Previous Version...**, a new dialog will appear.
3. Select **15.0** from the drop down menu.
4. Click **Save...**. A new dialog will open.
5. Create the `target\15.0` folder hierarchy in the project root, i.e. the same folder as the `Eulogy.lvproj` file, if it does not already exists.
6. Click **Save**.
7. Close LabVIEW 2018 or newer and the `Eulogy.lvproj` file.
8. Navigate to `<project root>\src`.
9. Copy the `Help` folder to `<project root>\target\15.0\src`.
10. Start LabVIEW 2015.
11. Open the `<project root>\target\15.0\Eulogy.lvproj` file. Do NOT open the project in any other version of LabVIEW.
12. Run the `Build.vi` in the `Scripts` project library to build each Source Distribution under the "Build Specifications" tree item and the compiled help documentation file (`Eulogy.chm`). The output of each build will be available in `<project root>\target\15.0\builds`.
13. Open the `<project root>\target\15.0\configs\Eulogy.vipb` file in VIPM.
14. Build the VI package with VIPM. The output will be available at `<project root>\target\15.0\packages`. Do NOT modify anything in the package build specification, but ensure the "2015" version of LabVIEW is selected in the upper, right-hand corner of the VIPM application window.
15. Close VIPM.
16. Close LabVIEW 2015 and the `<project root>\target\15.0\Eulogy.lvproj` file.

## [Documentation](https://help.fieldrndservices.com/eulogy)

See the in-app LabVIEW Help system for more information and documentation about using the library after it has been installed, or visit the [web-based documentation](https://help.fieldrndservices.com/eulogy). Examples are also available within the LabVIEW development environment using the "Help->Find Examples..." menu item.

## Tests

Tests are written in LabVIEW using the [Caraya](https://github.com/JKISoftware/Caraya) unit testing framework and included in the project via the various `Tests.lvlib` project libraries and the `tests` on-disk folder. To run the tests, open the `Eulogy.lvproj` file found in the project root in the LabVIEW Development Environment (32-bit or 64-bit) and run the `Test.vi` script located in the `Scripts.lvlib` project library. This will run all of the tests defined in all of the various `Tests.lvlib` project libraries located in the project. 

The tests are organized in a hierarchy based on their relationship to the source code. The `Tests.lvlib` project library for the "My Computer" tree item in the Project Explorer are generally for integration-style tests, i.e. tests for the public API of the toolkit and components. The `Tests.lvlib` project libraries found within each component's project library (`Bookmark Manager.lvlib`, `Toolkit.lvlib`, etc.) are generally for unit-style tests, i.e. tests for private/support VIs of the components. None of the tests are included in the VIP distribution. They are only included with the source code.

## License

Eulogy is licensed under either the [BSD-3-Clause license](https://opensource.org/licenses/BSD-3-Clause) or the [Apache-2.0 license](http://www.apache.org/licenses/LICENSE-2.0). See the `docs` folder for more information about licensing and copyright. 

