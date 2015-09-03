Prerequisites
=============

Custom version of NS-3 (https://github.com/named-data-ndnSIM/ns-3-dev/tree/2c66f4c02008805eaa7f2a21b88162b4f46e5ec2)
and ndnSIM 2.1 needs to be installed.

The code should also work with the latest version of ndnSIM, but it is not guaranteed.

    mkdir ns-dev
    cd ns-dev

    git clone https://github.com/named-data-ndnSIM/ns-3-dev ns-3
    git checkout 2c66f4c02008805eaa7f2a21b88162b4f46e5ec2
    git clone https://github.com/named-data-ndnSIM/ndnSIM ns-3/src/ndnSIM

    git clone https://github.com/named-data-ndnSIM/ndn-ping-scenario my-simulations

    cd ns-3
    ./waf configure -d optimized
    ./waf
    sudo ./waf install

    cd ../my-simulations

After which you can proceed to compile and run the code

For more information how to install NS-3 and ndnSIM, please refer to http://ndnsim.net website.

Compiling
=========

To configure in optimized mode without logging **(default)**:

    ./waf configure

To configure in optimized mode with scenario logging enabled (logging in NS-3 and ndnSIM modules will
still be disabled, but you can see output from NS_LOG* calls from your scenarios and extensions):

    ./waf configure --logging

To configure in debug mode with all logging enabled

    ./waf configure --debug

If you have installed NS-3 in a non-standard location, you may need to set up ``PKG_CONFIG_PATH``
variable.

Running
=======

You can run the ping scenario by typing

    ./build/ndn-cxx-simple-ping

or using waf

    ./waf --run ndn-cxx-simple-ping

If NS-3 is installed in a non-standard location, on some platforms (e.g., Linux) you need to specify ``LD_LIBRARY_PATH`` variable:

    LD_LIBRARY_PATH=/usr/local/lib ./build/ndn-cxx-simple-ping

or

    LD_LIBRARY_PATH=/usr/local/lib ./waf --run ndn-cxx-simple-ping

To run scenario using debugger, use the following command:

    gdb --args ./build/ndn-cxx-simple-ping


Running with visualizer
-----------------------

The visualizer is not available, since the scenarios simulating a real application cannot use any
GUI operations.

Available simulations
=====================

<Scenario Name>
---------------

ndn-cxx-simple-ping: Simulation scenario of the ping application included in the
NDN Essential Tools (http://github.com/named-data/ndn-tools) repository.
