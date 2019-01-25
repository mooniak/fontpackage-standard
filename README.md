> Fontpackage is the standard for packaging and distributing font projects. The Fontpackage format is a container for a font family's font files and extended metadata. Its purpose is to contain all necessary working files for a font family, as well as its meta-information.

# Fontpackage specification

## Fontpackage layout

While the Fontpackage standard aims to  standard is simple and requires only minimum dataset to validate. To be validate with Fontpackage a project team would only add `fontpackage.toml` at the root.  

```
./fonts
  |--otf/
  |--ttf/
  |--webfonts/
        |--index.css
./fontpackage.toml
```

## fontpackage.toml: the manifest file

The manifest file `fontpackage.toml` on the root of the repo contains a superset of data provided in the 'METADATA.yml' of the UFR. `fontpackage.toml`  provides the information, metadata and classification data.

There are four main blocks in `fontpackage.toml`
- Package metadata (required)
- Display and classification data (optional)
- (classification, display strings and image urls)
- App specific blocks (Other metadata or config relating to specific apps)

## Distribution

### Versions and git
Type.world [version](https://github.com/typeWorld/api/tree/master/Python/Lib/typeWorld#class-version) object has the attributes `description``number``releaseDate`. We need to represent above details and more in the Git repository. Git tags are used in other package systems for release management.

- Users subscribe to the repository link.
- TW app reads the fontpackage manifest file in the root
- If `versions.provider` is `tags` app will get the versions using the Github REST API tags.
- With `versions.filter` publisher can remove specific tag or tags from being distributed as versions.

|  GH Response  | Type      | Description               |  TW object      |   |
|---            | ---       |---                        |---              |---|
| `tag`         |  `string` | The tag's name on github. | -               |   |
| `message`     |  `string` | The tag message.          | description     |   |
| `object`      |  `string` | SHA                       | SHA             |   |
| `tagger.date` |  `string` | YYYY-MM-DDTHH:MM:SSZ      | YYYY-MM-DD      |   |
| `object.url`  |  `string` |                           | <URL to source> |   |

### Standalone archive (.fontpkg)
[TODO]


## Validating a Fontpackage
[TODO]

### Fontpackage and other projects
Fontpacakge is an accumulation of some of the earlier projects and builds on the existing standards and practices. Here is how Fontpackage is

## Fontpackage and Unified Font Repository
Unified Font Repository layout is a standard repository layout to organize font project sources; covering all files including documentation, tests, source files and etc. Fontpackage is a standard for distributing font binaries and metadata. Fontpackage is fully compatible with UFR structure.

There are data duplication in the `METADATA.yml` and the `fontpackage.toml` This is something we have to

## Fontpackage and npm
[TODO]

### Type.World Git subscription (Github)
Specification should aim to work with git artifacts and develop the standard to be provider-agnostic. Implementation will require working with APIs from respective Git service provider, in this case Github REST API.

## About

### Goals
- Develop a standard for font project repositories treating font project as a ‘font package’
- Develop an universal standard for the font package, providing metadata for direct distribution from the repository and consumption by conforming package managers or sync clients (primarily Type.World)
- Provide tooling and workflows to easily build other kinds of packages from repository (ie; npm, Appstream specification)
- Optionally use the same manifest file to include build and testing configurations for other tools (fontmake, fontbakery)

### Existing related projects and standards
- [Unified Font Repository (UFR)](https://github.com/unified-font-repository/Unified-Font-Repository)
- [Google Fonts repositories](https://github.com/googlefonts/Inconsolata)
- [Google Fonts METADATA.pb files ](https://github.com/googlefonts/Inconsolata/blob/master/METADATA.pb)
- [Appstream specification metadata](https://github.com/unified-font-repository/Unified-Font-Repository/issues/25)
- [Foundry in a Box](https://gitlab.com/foundry-in-a-box/fib)
- [typefaces](https://github.com/KyleAMathews/typefaces): NPM packages for Open Source typefaces.

### Credits
[TODO]

### License
[TODO]
