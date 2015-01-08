LIS-Tempest - The Linux on Hyper-V Integration Test Suite
=========================================================

This is a set of integration tests to be run against a live OpenStack
cluster with Hyper-V compute nodes. LIS-Tempest has batteries of tests 
for Linux clients running on Hyper-V, including Storage, Networking,
Live Backup, Live Migration and other specific tests useful in validating
a Linux client on Hyper-V.

Tempest
---------
LIS-Tempest adds a new set of specific tests on top of  
https://github.com/openstack/tempest targeting Linux clients running on Hyper-V.

Quickstart
----------

To run LIS-Tempest, first clone this repo on your OpenStack controller, 
create a configuration file that will tell LIS-Tempest where to find the 
various OpenStack services, Hyper-V nodes and other testing behavior 
switches.

The easiest way to create a configuration file is to copy the sample
one in the `etc/` directory:

```sh
    cd $TEMPEST_ROOT_DIR
    cp etc/tempest.conf.sample etc/tempest.conf
```

After that, open up the `etc/tempest.conf` file and edit the
configuration variables to match valid data in your environment.
This includes your Keystone endpoint, a valid user and credentials,
and reference data to be used in testing.

**Note:**

    If you have a running devstack environment, tempest will be
    automatically configured and placed in `/opt/stack/tempest`. It
    will have a configuration file already set up to work with your
    devstack installation.

LIS-Tempest is not tied to any single test runner, but testr is the most commonly
used tool. After setting up your configuration file, you can execute
the set of Tempest tests by using `testr`:

```sh
testr run --parallel
```

To run one single test:
```sh
testr run tempest.lis.core.test_time_sync.TimeSync.test_time_sync_ntp
```