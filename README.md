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
