# Fontpackage / Type.World subscription

## Introduction

_Goals_
- Develop a standard for font project repositories treating font project as a ‘font package’ (like-a-npm-package)
- Develop an universal manifest file standard for the font package, providing metadata for direct distribution from the repository and consumption by conforming package managers or sync clients (primarily Type.World)
- Provide tooling and workflows to easily build other kinds of packages from repository (ie; npm, Appstream specification)
- Optionally use the same manifest file to include build and testing configurations

### Existing related projects and standards

- [Unified Font Repository](https://github.com/unified-font-repository/Unified-Font-Repository)
- [Google Fonts repositories](https://github.com/googlefonts/Inconsolata)
- [Google Fonts METADATA.pb files ](https://github.com/googlefonts/Inconsolata/blob/master/METADATA.pb)
- [Appstream specification metadata](https://github.com/unified-font-repository/Unified-Font-Repository/issues/25)
- TODO: Add more

## Type.World Git subscription (Github)

Specification should aim to work with git artifacts and develop the standard to be provider-agnostic. Implementation will require working with APIs from respective Git service provider, in this case Github REST API.   

### Versions

Type.world [version](https://github.com/typeWorld/api/tree/master/Python/Lib/typeWorld#class-version) object has the attributes `description``number``releaseDate`. We need to represent above details and more in the Git repository. Git tags are used in other package systems for release management.

- Users subscribe to the repository link.
- TW app reads the fontpackage manifest file in the root
- If `versions.provider` is `github-tags` app will get the versions using the Github REST API tags.
- With `versions.filter` publisher can remove specific tag or tags from being distributed as versions.

|  GH Response  | Type      | Description               |  TW object      |   |
|---            | ---       |---                        |---              |---|
| `tag`         |  `string` | The tag's name on github. | -               |   |
| `message`     |  `string` | The tag message.          | description     |   |
| `object`      |  `string` | SHA                       | SHA             |   |
| `tagger.date` |  `string` | YYYY-MM-DDTHH:MM:SSZ      | YYYY-MM-DD      |   |
| `object.url`  |  `string` |                           | <URL to source> |   |
