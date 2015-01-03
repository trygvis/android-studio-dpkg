SYNOPSIS
--------

    ./build-package [-v <version>/<build> ] -u [-c <channel>]

DESCRIPTION
--------

`build-package` will create a platform-specific package of Jetbrain's
Intellij IDEA. The packages can be installed using platform
specific/native tools and/or distributed from local package repositories.

It currently only supports building packages of the development builds
of IDEA, either by finding and downloading the latest version directly
from Jetbrain's servers or by being pointed to a build output directory
and use that.

OPTIONS
--------

* `-F`

    Force a build of a package, even if there is a package with the same
    version in the repository.

* `-s <directory>`

    Sets <directory> to be the input directory when creating the
    package. This is used to build packages from custom builds of IDEA.

    Note that you have to specify the version explicitly.

* `-u`

    Updates the package repository with the appropriate command for
    the platform.

    For debian this means dpkg-scanpackages, for solaris bldcat is used.

* `-v <version>`

    The version of the build to use. If not specified the script will
    automatically find and download the latest Canary build from
    https://dl.google.com/android/studio/patches/updates.xml

* `-c <channel>`

    The update channel that should be used. Current values:

    Channel          | Description
    AI-1-eap         | Canary
    AI-1-dev-channel | Development
    AI-1-beta        | Beta
    AI-1-release     | Full releases

EXAMPLES
-------

Example 1: Creating a package of the latest version:

    ./build-package

Example 2: Creating a Debian package of Android Studio 1.0.1:

    ./build-package -f IC -p debian -v 1.0.1/135.1641136

BUGS
----

The scripts are not bullet proof, so there might certainly be bugs in
them. The scripts also depend on jetbrains to not change the way they
package and distribute the tar files.

If you find a bug, please file a bug on GitHub:
http://github.com/trygvis/android-studio-dpkg/issues
