AWS OpsWorks "Getting Started" Example
======================================

This example implements the AWS OpsWorks "Getting Started" sample PHP application found [here](http://docs.aws.amazon.com/opsworks/latest/userguide/gettingstarted-db.html)

This example depends on the `centos7mini-opsworks` box which must be compiled and installed:
Repo for this found [here](https://github.com/ljay79/opsworks-vm)

    $ rake build[centos7mini] install[centos7mini]  # assuming you are using virtualbox

To run this example, first ensure that git submodules have been checked out:

    $ git submodule init
    $ git submodule update

Then simply type `vagrant up` and wait for it to provision the app. You can view the results by opening up a browser and pointing it to [192.168.56.11:8080](http://192.168.56.11:8080/)