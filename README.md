# Automatic changelog generation

## Concept
### What is all about
keepachangelog.com
[gitchangelog](https://pypi.python.org/pypi/gitchangelog)

### How to Git Tag
*major*.*minor*.*patch*[-*prerelease*][+*build*]

`[0-9]+\.[0-9]+(\.[0-9]+)?(-.+.*)?(\+.+.*)?`

#### Valid Tag examples
    0.6
    0.0.1
    1.0.0
    1.1.2
    2.1.2-beta1
    1.0.0-alpha
    1.0.0-rc.2
    1.0.0+build.3.ea34fd5c
    1.0.0-beta.3+build.20.f42cbd56

### rule of thumb

- Add `user:` or `usr:` to your commit message to appear in `CHANGELOG.md`
- Every log between tags are changelogged to a specific version
- The "unreleased" section is dynamically generated for what is not tagged (pull request compatibility)

## Install

`pip install gitchangelog pystache`

## Integration

How to make it work with your repository ?

### Prerequiste

- a file named `CHANGELOG.md` in your root folder of the repository
- at least one tag and his description in the `CHANGELOG.md` ([look here for inspiration](https://raw.githubusercontent.com/jdelasoie/gitchangelog.rc/03e5e8a3d8d5748ebcc39b9cdeafaadba2f20d94/CHANGELOG.md))

- have the .gitchangelog.rc in the root folder. Please choose your method :
    - or by getting as a static file
      `curl -sSL https://raw.githubusercontent.com/jdelasoie/gitchangelog.rc/master/.gitchangelog.rc`
    - or by using git submodule
    https://stackoverflow.com/questions/7597748/linking-a-single-file-from-another-git-repository

## Usage
After committing, go into your project folder and run
`gitchangelog`

### without a tag
it may be nice to keep the new generated version of the changelog by doing a
`git add CHANGELOG.md && git commit -m "chg: pkg: Update changelog"`

Everything that is not between a tag will be put in the "Unreleased" section.

### with a tag
Say you are happy with the state of the last commit and want to tag it. If you want to include the changed changelog into the tag, do

`git tag x.x`
`gitchangelog`
`git add CHANGELOG.md && git commit -m "chg: pkg: Update changelog"`
`git tag --delete x.x`
`git tag x.x`


## Commit message format
`ACTION: [AUDIENCE:] COMMIT_MSG [!TAG ...]`

### Examples
`new: usr: support of bazaar implemented`
`chg: re-indentend some lines !cosmetic`
`fix: pkg: updated year of licence coverage.`
`new: test: added a bunch of test around user usability of feature X.`
`fix: typo in spelling my name in comment. !minor`


### ACTION
What the change is about
#### `new:`
for new features, big improvement

#### `chg:`
for refactor, small improvement, cosmetic changes...

#### `fix:`
for bug fixes

### AUDIENCE

#### `dev:`
for developpers (API changes, refactors...)

#### `usr:`
for final users (UI changes)

#### `pkg:`
packaging changes

#### `test:`
test only related changes

#### `doc:`
doc only changes

### TAG

Making a change invisible

#### `!refactor`

for refactoring code only

#### `!minor`

for a very meaningless change (a typo, adding a comment)

#### `!cosmetic`

for cosmetic driven change (re-indentation, 80-col...)

#### `!wip`

for partial functionality but complete subfunctionality

## Example
[From mediatheque changelog](https://github.com/epfl-idevelop/site-diffusion-mediatheque/blob/feature/gitchangelog/CHANGELOG.md)
or
[from gitchangelog project, "sample" part](https://pypi.python.org/pypi/gitchangelog)
