# BOXT CircleCI Orbs

Reusable bundles of commands for our CircleCI deploys

## Prerequisites

To release a new version of an orb, please make sure you have the CircleCI CLI tool installed.

```sh
brew install circleci
```

## Development

To develop a bundle, you should clone this repo.

```sh
git clone https://github.com/boxt/orbs.git
cd ./orbs
```

### Orb Submodules

Each orb lives in its own repository, and is installed as a sub-repository of this repo. To download those, run the following commands:

```sh
git submodule init # to initialize your local configuration file
git submodule update # to fetch all the data from that project and check out the appropriate commit
```

Once you make changes to an orb, add and commit them to the submodule in the same way you would any other repo.

### Releasing a new orb version

**Orbs are versioned separately, and so should be managed as individual repos.**

1) Create a feature branch for your orb changes.

```sh
cd <orb name>
git flow feature start my-change
```

2) Stage and commit your changes to the repo.

```sh
git add .
git commit -am "I done stuff"
```

3) Release a dev version of your changes to test on another repository.

```sh
circleci orb publish config.yml boxt/<orb name>@dev:x.y.z
```

4) Test your changes by pointing your project's CircleCI config at your orb's development version.

``` yml
# config.yml
version: 2.1
# ... other stuff
orbs:
yourorb: boxt/yourorb@dev:x.y.z
```

5) Merge your changes into the `develop` branch.

```sh
git flow feature finish my-change
```

6) Release a new version via Git Flow

```sh
git flow release start 1.2.3
```

7) Merge in changes as required

8) Finish the release

```sh
git flow release finish 1.2.3
```

9) Push orb updated branches and tag to GitHub

```sh
git push origin master && git push origin develop && git push --tags
```

10) Release final version of your orb.

```sh
circleci orb publish config boxt/<orb name>@x.y.z
```

11) Update _this_ repo to make sure we're tracking the latest orb versions

## Install snippet

You'll see the HTML comment  `<!-- VERSION_SNIPPET_START --><!-- VERSION_SNIPPET_END -->` in each of the `README.md` documents. The contents of this are automatically maintained by a GitHub workflow. See the `./.github/workflows/*.yml` files for more info.
