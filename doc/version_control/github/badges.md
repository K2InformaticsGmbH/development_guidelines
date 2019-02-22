[Development Guidelines](../../../README.md) / [Version Control](../../../README.md#version_control) / [GitHub](../../../README.md#github)

## [Badges](../../../README.md#version_control_github)

### 1 Introduction

The badges used below are based on the free service [shields.io](https://shields.io/).

----

### 2 Example

The necessary program code in the `readme.md` file:

```markdown
![Travis (.org)](https://img.shields.io/travis/K2InformaticsGmbH/plsql_parser.svg)
![Coveralls github](https://img.shields.io/coveralls/github/K2InformaticsGmbH/plsql_parser.svg)
![GitHub](https://img.shields.io/github/license/K2InformaticsGmbH/plsql_parser.svg)
![GitHub release](https://img.shields.io/github/release/K2InformaticsGmbH/plsql_parser.svg)
![GitHub Release Date](https://img.shields.io/github/release-date/K2InformaticsGmbH/plsql_parser.svg)
![GitHub commits since latest release](https://img.shields.io/github/commits-since/K2InformaticsGmbH/plsql_parser/1.2.0.svg)
```

The result in the repository:

![Badges](https://i.imgur.com/9hRa0j1.jpg)

----

### 3 Template

```markdown
![Travis (.org)](https://img.shields.io/travis/K2InformaticsGmbH/repository.svg)
![Coveralls github](https://img.shields.io/coveralls/github/K2InformaticsGmbH/repository.svg)
![GitHub](https://img.shields.io/github/license/K2InformaticsGmbH/repository.svg)
![GitHub release](https://img.shields.io/github/release/K2InformaticsGmbH/repository.svg)
![GitHub Release Date](https://img.shields.io/github/release-date/K2InformaticsGmbH/repository.svg)
![GitHub commits since latest release](https://img.shields.io/github/commits-since/K2InformaticsGmbH/repository/version.svg)
```

- Replace the string `'repository'` with the name of your repository.
- Replace the string `'version'` with the current release number.

----

### 4 Application Rules

1. The badges are in the `readme.md` file and if the `wiki` exists in the `home.md` file.
2. The badges are placed directly after the headline.
3. The `'Coveralls github'` badge is omitted if no code coverage is established.
4. The version number in the `'GitHub commits since latest release'` badge has to be changed manually for a new release.

----

