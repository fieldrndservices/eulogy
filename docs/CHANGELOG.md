# Field R&D Services: Eulogy Change Log

All notable changes to this project will be documented in this file, which is written in plain text (ASCII) using the [Markdown](http://daringfireball.net/projects/markdown/syntax) lightweight markup language. This project adheres to [Semantic Versioning](http://semver.org). 

## [Unreleased]

### Added

- Before (pre) and after (post) hooks for each action: Bury, Dig, Reanimate, and Smite. (Issue #14)
- Tools menu item to create hooks. (Issue #16)
- VI reference inputs and outputs for each toolkit action VI.
- Controls (inputs) to each toolkit action VI, i.e. Bury, Dig, Reanimate, and Smite, to customize behavior of hook execution.
- Condition variables to enable and disable hooks through out a project.

### Changed

- Toolkit VI documentation to match new hook-enabled API.

## [1.0.1] - 2019-11-25

### Added

- More theme appropriate status messages to the Bookmark Manager (Graveyard).
- Saving Bookmark Manager (Graveyard) position, scope, and grouping between usage.
- Preferences for customizing Bookmark Manager (Graveyard) behavior.
- Resizable Bookmark Manager (Graveyard) window.
- Prefix renaming to toolkit library to avoid name collisions.
- Smite example screenshot to help documentation.
- Acknowledgements section to the help documentation.

### Changed

- Automated build process to use Labricator instead of custom process.

### Fixed

- Table of Contents entry for Smite VI in toolkit API documentation.
- Bury shortcut menu action failing. (Issue #2)
- Reanimate shortcut menu action failing when Graveyard is open. (Issue #3)
- Populating Bookmark Manager (Graveyard) with graves and zombies performance. (Issue #1)
- Searching for bookmarks occurring in infinite loop. (Issue #1)
- Build to not package duplicate VIs for toolkit
- Wording and organization in the Concepts help documentation.
- Underscores used for emphasis instead of HTML tags for help documentation.
- Install location of Toolkit VIs.
- Install location of `Programmatically Find Graves.vi` example.
- Install location of `Programmatically find Zombies.vi` example.

## [1.0.0] - 2018-08-20

### Added

- Examples for digging a grave, reanimating, smiting, burying, and using the Graveyard
- Automated build process
- Help documentation
- Descriptions to all controls and indicators for all public VIs
- Quick Drop Keyboard Shortcuts
- Shortcut Menu Plugin
- Custom Bookmark Manager (Graveyard)
- Initial project structure and on-disk organization
- Apache-2.0 and MIT license documentation
- Build specifications for Bookmark Manager, Examples, Quick Drop Keyboard Shortcuts, Shortcut Menu Plugin, Toolkit API, Tools Menu
- Meaningful VI icons to public Toolkit API VIs
- Color coded bookmarks to Graveyard
- Filtering bookmarks by graves or zombies
- Reanimating corpse frames in graves (Diagram Disable Structures)
- Smiting zombie frames in graves (Diagram Disable Structures)
- Burying corpses, i.e. removing graves
- Double-click object highlighting from within the custom Bookmark Manager
- Run-time shortcut menus to the tree view of the custom Bookmark Manager

