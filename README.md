# Puppet Debugging Kit
_The only good bug is a dead bug._

This project provides a batteries-included Vagrant environment for debugging Puppet powered infrastructures.

## Installation ##

The Vagrantfile forwards https://localhost:4433, which allows access to the console.  The credentials are admin/puppetlabs 

### Ubuntu ###
 1. Install VirtualBox
 1. Install Vagrant
 1. `apt-get install ruby2.0 libruby2.0 ruby2.0-dev`
 1. `git clone https://github.com/devops-workflow/puppet-debugging-kit && cd puppet-debugging-kit`
 1. `rake setup:global`
 1. `vagrant up pe-381-master`
 1. `vagrant ssh pe-381-master`
 1. `sudo sed -i '/^127.0.1.1 pe/d' /etc/hosts`
 1. `sudo puppet agent -t`
 1. `sudo /root/puppet-r10k/install.sh`
 1. `exit`
 1. `vagrant up pe-381-agent-jenkins`
 1. `vagrant ssh pe-381-agent-jenkins`
 1. `sudo yum -y install git python-pip`
 1. `git clone https://github.com/devops-workflow/jenkins-job-builder-config.git`
 1. `cd jenkins-job-builder-config && sudo run-jjb.sh`
