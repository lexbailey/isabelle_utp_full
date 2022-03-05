# Isabelle ITrees Full

This git repository is a wrapper around various other repositories.

The other repositories are submodules in this repository. The modules include the isabelle source, the isabelle AFP, and all of components required for ITrees.

All of the ITree related repositories and dependencies can be found here: https://github.com/isabelle-utp

## Building

To build everything, first clone this repository, then

`git submodule update --init --recursive`

Once everything has been cloned, you can build isabelle and all the required components using the provided build script

`./build`

it's really not very long, you can have a look at it and see what it does

## Notes:

The isabelle submodule is a modified version with some additional code required for ITrees to work

The isabelle version also default to putting the `contrib` components in the isabelle directory, instead of the user's home directory, and uses a custom `$ISABELLE_IDENIFIER` value so this will not interfere with other isabelle instances on the system.
