WORK IN PROGRESS

# Fontpackage / Type.World subscription

## Introduction

<TODO>
- Support Type.World subscription
- Universal metadata format for fonts
- Accommodate automation building, testing and distributing libre fonts with common tooling and workflows   

## Type.World Git subscription (Github)

We will try to work with standard git artifacts primarily and develop the standard to be provider-agnostic.

### Versions

Type.world [version](https://github.com/typeWorld/api/tree/master/Python/Lib/typeWorld#class-version) object has the following attributes.

`
description
number
releaseDate
`
We need to represent above details and more in the Git repo. Git tags are used in other package systems for release management.

- Users subscribe to the repository link.
- TW app check the root of the repository for fontpackage.toml
- If `versions.provider` is `github-tags` app will get the versions using the Github REST API tags.
- With `versions.filter` publisher can remove specific tag or tags from being distributed as versions.

|  GH Response  | Type      | Description               |  TW object      |   |
|---            | ---       |---                        |---              |---|
| `tag`         |  `string` | The tag's name on github. | -               |   |
| `message`     |  `string` | The tag message.          | description     |   |
| `object`      |  `string` | SHA                       | SHA             |   |
| `tagger.date` |  `string` | YYYY-MM-DDTHH:MM:SSZ      | YYYY-MM-DD      |   |
| `object.url`  |  `string` |                           | <URL to source> |   |


#### Approach 2 - Use fontpackage.toml only

List the versions in `fontpackage.toml` as formatted table.
Like npm we can run a small script to add version bump. Which will create a new `git tag`, `commit` and write the data to `fontpackage.toml` This way we can avoid sending extra requests to GH API.

```
versions = [
{ number = "", description = "", release_date ="", commit = "", },
```
 or

```
{ number = "", description = "", release_date ="", url = ""},
```

### Release channels and git branches

https://docs.npmjs.com/adding-dist-tags-to-packages
