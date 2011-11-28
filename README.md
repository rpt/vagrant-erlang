vagrant-erlang
====================

What it is
--------------------

It's just a few scripts allowing you to quickly setup linux (Ubuntu) environment with erlang installed.
It uses [vagrant][3] with [puppet][2] to setup the VM and [puppet-erlang][1] with [kerl][4] to install erlang. 

### Files:

 * `Vagrantfile` - vagrant config file
 * `puppet/manifests/site.pp` - puppet script to install erlang
 * `puppet/modules/erlang` - puppet-erlang module (as a submodule)

How to use it
--------------------

First, remember to update git submodules to clone [puppet-erlang][1] into `puppet/modules/erlang`:

    $ git submodule update --init

Import `lucid64` box (change to whatever you like in `Vagrantfile`), start the VM and run puppet with:

    $ vagrant up

It takes about 6-7 minutes to start the VM and install erlang.

Now you can package your VM into a new box:

    $ vagrant package

This will create `package.box` file. Add it to vagrant using:

    $ vagrant box add vagrant-lucid64-erlang package.box

To use the newly create box in your project initiate vagrant like this:

    $ vagrant init vagrant-lucid64-erlang

   [1]: https://github.com/rpt/puppet-erlang "puppet-erlang - Erlang type for Puppet"
   [2]: https://github.com/puppetlabs/puppet "Puppet - Server automation framework and application"
   [3]: https://github.com/mitchellh/vagrant "Vagrant - Tool for building and distributing virtualized development environments"
   [4]: https://github.com/spawngrid/kerl "Kerl - Easy building and installing of Erlang/OTP instances"
