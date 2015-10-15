# Puppet Debugging Kit
_The only good bug is a dead bug._

This project provides a batteries-included Vagrant environment for debugging Puppet powered infrastructures.

## Installation ##

The Vagrantfile forwards https://localhost:4433, which allows access to the console.  The credentials are admin/puppetlabs 

### Cygwin ###
 1. Install Git and Ruby under Cygwin (using the Cygwin installer)
 2. Workaround for [Vagrant Requires TTY (#6026)](https://github.com/mitchellh/vagrant/issues/6026) issue.
   1. export VAGRANT_DETECTED_OS=cygwin
 3. Workaround for Vagrant-PE [Windows permission denied](https://github.com/liger1978/vagrant-pe/issues/4) issue in Oscar [Windows 7 Permission Denied](https://github.com/oscar-stack/vagrant-pe_build/issues/60).
   1. mkdir -p /cygdrive/c/Users/${USER}/.vagrant.d/pe_builds
   2. cd /cygdrive/c/Users/${USER}/.vagrant.d/pe_builds
   3. wget https://s3.amazonaws.com/pe-builds/released/3.8.1/puppet-enterprise-3.8.1-el-6-x86_64.tar.gz
   4. cd -
 4. Continue with the "Ubuntu" install, below (Note: equivalent apt-get step is no longer needed)

### Ubuntu ###
 1. Install VirtualBox
 1. Install Vagrant
 1. `apt-get install ruby2.0 libruby2.0 ruby2.0-dev`
 1. `git clone https://github.com/devops-workflow/puppet-debugging-kit && cd puppet-debugging-kit`
 1. `rake setup:global`
 1. `vagrant up pe-381-master`
 1. `vagrant ssh pe-381-master`
 1. `sudo sed -i '/^127.0.1.1 pe/d' /etc/hosts`
 1. `sudo /root/puppet-r10k/install.sh`
 1. `exit`
 1. `vagrant up pe-381-agent-jenkins`
 1. `vagrant ssh pe-381-agent-jenkins`
 1. `sudo /root/jenkins-job-builder-config/run-jjb.sh`


## Troubleshooting ##

Once the VM has been created, and the pe_build fails, you can restart the provisioning process.

Remove the git repository from the PE Master VM:

  vagrant ssh pe-318-master
  sudo rm -rf /root/puppet-r10k
  exit

Restart the provisioning from your machine:

  vagrant provision

