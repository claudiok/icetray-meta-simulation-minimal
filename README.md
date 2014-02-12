simulation-minimal IceTray meta-project
=======================================
An icetray meta-project pulling in all projects needed to run basic photon propagation.

Disclaimer
----------
This is a meta-project specific to the [IceCube neutrino telescope][icecube] (and Antares/KM3NeT)
simulation. It uses the [IceTray framework][icetray] and multiple IceCube-internal packages
which will be pulled in from external repositories using submodules.

Dependencies
------------
This package can use either packages provided by an IceCube-internal fork of MacPorts or
use system packages provided by package managers. If you haven't heard about I3_PORTS,
you should probably install system packages. On OS X, the [homebrew package manager][homebrew] will
make installing the dependencies really easy.

You will need to "tap" into the homebrew-science repository for hdf5, suite-sparse, and geant:

    brew tap homebrew/science

Install these packages (brew install XXX):

    boost cmake cdk gsl hdf5 libarchive cfitsio minuit2 mysql qt pyqt suite-sparse

To be able to use all simulation scripts, you will need to tap into Jakob's homebrew-icecube repository and
install the "sprng" package:

    brew tap jvansanten/icecube
    brew install sprng2

Note: Don't install Python from Homebrew. If you do, it will also want to waste a lot of time building boost
from source instead of using a binary distribution built against the system Python (2.7.2, which is just fine).

Installation
------------
To compile this IceTray meta-project, first check out the source and generate a build directory (out of source) using
something like this:

    git clone http://github.com/claudiok/icetray-meta-simulation-minimal.git simulation-minimal
    mkdir build
    cd build
    cmake ../simulation-minimal -DSYSTEM_PACKAGES=True

Then enter the project environment and compile away using "make":

    ./env-shell.sh
    make -j4

Usage
-----
(This section still needs work)
You should be able to load icetray in python and start using scripts

    from I3Tray import *
    from icecube import icetray, dataio, dataclasses

    tray = I3Tray()
    tray.Add('I3Reader', Filename="test.i3")
    tray.Add('Dump')

    tray.Execute()


[icecube]: http://icecube.wisc.edu
[icetray]: http://code.icecube.wisc.edu/projects/icetray
[homebrew]: http://brew.sh
