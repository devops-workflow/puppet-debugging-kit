# Puppet Debugging Kit
_The only good bug is a dead bug._

This project provides a batteries-included Vagrant environment for debugging Puppet powered infrastructures.

## Installation ##

The Vagrantfile forwards https://localhost:4433, which allows access to the console.  The credentials are admin/puppetlabs 

### Ubuntu ###
 1. Install VirtualBox
 1. Install Vagrant
 1. `apt-get install ruby2.0 libruby2.0 ruby2.0-dev`
 1. `rake setup:global`
 1. `vagrant up pe-381-master`
