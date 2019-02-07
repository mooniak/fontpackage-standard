> Fontpackage is the standard for packaging and distributing font projects. The Fontpackage format is a container for a font family's font files and extended metadata. Its purpose is to contain all necessary working files for a font family, as well as its meta-information.

# Fontpackage specification

[TODO: Introduction and background]


## Fontpackage file Structure

While the Fontpackage standard aims to  standard is simple and requires only minimum dataset to validate. The core of the standard is the higely custmisable manifest file `fontpackage.toml` which sits at the root of the respository. The reccomended repository layout for Fontpackage is Unified Font Respository (UFR) layout, which defines a standard for orgnising all source files and documentation of a font project. However, Fontpackage only requiers the following files to validate.

```
fontpackage.toml
LICENSE
FONTLOG.md
▾ fonts #This is compatible with UFR and the defult location for binaries.
  ▾ otf/
      *.otf
  ▾ otf/
      *.otf
  ▾ webfonts/
      *.woff
      *.woff2
      index.css
```

_NOTE:_  Package authours who choose not to use the UFR may point to font binaries and other files from the manifest file with URI relative to root. The minimum requierment for validating as a fontpackage is a `fontpackage.toml` at the root of the reposiotry, pointing to the font binaries.

[TODO: Include complete layout]


## fontpackage.toml: the manifest file

The manifest file `fontpackage.toml` on the root of the repo contains a superset of data provided in the 'METADATA.yml' of the UFR. `fontpackage.toml`  provides the information, metadata and classification data.

There are four main blocks in `fontpackage.toml`
- Package metadata (required)
- Display and classification data (optional)
- (classification, display strings and image urls)
- App specific blocks (Other metadata or config relating to specific apps)


## Versions


## Authoring
[TODO]

_NOTE:_ [TODO: Explanation] Why we commit binaries to the git repo? 


### Git repositories and Fontpackage
[TODO]

_Unified Font Repository:_ UFR is a standard repository layout to organize font project sources; covering all files including documentation, tests, source files and etc. Fontpackage is a standard for distributing font binaries and metadata. Fontpackage is fully compatible with UFR structure.
There are data duplication in the `METADATA.yml` and the `fontpackage.toml` This is something we have to

### Standalone archive (.fontpkg)
[TODO]


## Distributing

This specification aim to work with git artifacts and develop the standard to be provider-agnostic. Implementation will require working with APIs from respective Git service provider, in this case Github REST API.

### Type.World Git subscription (Github)
[TODO: Intro]

### Fontlet package
[TODO]

### Fontpackage to npm
[TODO]


## FAQ
[TODO]


## About

### Goals
- Develop a standard for font project repositories treating font project as a ‘font package’
- Develop an universal standard for the font package, providing metadata for direct distribution from the repository and consumption by conforming package managers or sync clients (primarily Type.World)
- Provide tooling and workflow to easily packages fonts for other platforms (ie; npm, Appstream specification)
- Optionally use the same manifest file to include build and testing configurations for other tools (fontmake, fontbakery)

### Existing related projects and standards
- [Unified Font Repository (UFR)](https://github.com/unified-font-repository/Unified-Font-Repository)
- [Google Fonts repositories](https://github.com/googlefonts/Inconsolata) Standard followed by the most of Google Fonts repositories
- [Google Fonts METADATA.pb files ](https://github.com/googlefonts/Inconsolata/blob/master/METADATA.pb): Metadata files in Google Fonts repositories by Google Fonts
- [Appstream specification metadata](https://github.com/unified-font-repository/Unified-Font-Repository/issues/25)
- [Foundry in a Box](https://gitlab.com/foundry-in-a-box/fib)
- [typefaces](https://github.com/KyleAMathews/typefaces): NPM packages for Open Source typefaces.
- [fontctrl](https://fontctrl.org): A package manager for fonts

### Credits
[TODO]

### License
[TODO]
