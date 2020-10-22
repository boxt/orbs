# BOXT CircleCI Orbs

Reusable bundles of commands for our CircleCI deploys

## Development

To develop a bundle, you should download this repo

    git clone https://github.com/boxt/orbs.git
    cd ./orbs

### Submodules

Each orb lives in its own repository, and is installed as a sub-repository of this repo. To download those, run the following commands:

    git submodule init # to initialize your local configuration file

    git submodule update # to fetch all the data from that project and check out the appropriate commit

Once you make changes to an orb, add and commit them to the submodule in the same way you would any other repo.

### Releasing a new version

To release a new version of an orb, please make sure you have the CircleCI CLI tool installed (`brew install circleci`)

1. Create a feature branch for your changes

    ```
    git flow feature start my-change
    ```

2. Stage and commit your changes to the repo

    ```
    git add .

    git commit -am "I done stuff"
    ```

3. Release a dev version of your changes to test on another repository

    circleci orb publish boxt/<orb name>@dev:x.y.z

4. Test your changes, by pointing your main repository CircleCI config to your development version

    ``` yml
    # config.yml

    version: 2.1

    # ... other stuff

    orbs:
      yourorb: boxt/yourorb@dev:x.y.z

    ```

5. Merge your changes into the `develop` branch

    ``` bash
    git flow feature finish my-change
    ```

6. Release a new version via Git Flow

    ``` bash
    git flow release start 1.2.3
    ```

7. Merge in changes as required
8. Finish the release

    ``` bash
    git flow release finish 1.2.3
    ```

9. Push to GitHub

    ``` bash
    git push --all
    ```

    ``` bash
    git push --tags
    ```
