# Isabelle ITrees Full

This git repository is a wrapper around various other repositories.

The other repositories are submodules in this repository. The modules include the isabelle source, the isabelle AFP, and all of components required for ITrees.

All of the ITree related repositories and dependencies can be found here: https://github.com/isabelle-utp

## Building

To build everything, first clone this repository, then

`git submodule update --init --recursive`

This includes one private repo (UTP) which can be skipped if you don't need it or don't have access.

Once everything has been cloned, you can build isabelle and all the required components using the provided build script

`./build`

it's really not very long, you can have a look at it and see what it does

## Notes:

The isabelle submodule is a modified version with some additional code required for ITrees to work

The isabelle version also default to putting the `contrib` components in the isabelle directory, instead of the user's home directory, and uses a custom `$ISABELLE_IDENIFIER` value so this will not interfere with other isabelle instances on the system.

## Known issues

I don't know if I've configured the thing badly, but sometimes if you have to retry a failed run of the build script, it will complain about being unable to download "thys". This is because it's trying to download something that doesn't exist, thinking that it needs to do it, when really the thing it's looking for is the local copy of the AFP.

The fastest way to deal with this is to delete the config in the home directory:

`rm -rf ~/.isabelle/itrees_utp_2021-1`

and then just run the build again

another related issue is with isabelle complaining of a session being duplicated, for example:

    *** Duplicate session "Berlekamp_Zassenhaus" (line 3 of "some/path/mirror-afp-2021-1/thys/Berlekamp_Zassenhaus/ROOT") (line 3 of "some/other/path/mirror-afp-2021-1/thys/Berlekamp_Zassenhaus/ROOT")

This is normally because you have two different instance of this version of isabelle on your system.

You can resolve this as above, by deleting the appropriate subdirectory in your isabelle config dir, or you can set your `ISABELLE_IDENTIFIER` variable differently for each one, and rebuild the user config appropriately.
