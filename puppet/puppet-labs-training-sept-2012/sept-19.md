Puppet Labs - Puppet Fundamental Training
=========================================

September 19, 2012 - taught by Zack Smith (zack@puppetlabs.com)

Review
------
* "puppet apply" does not have parameter passing from the master, but you can
  use an open source tool pick (on github) or wait for the next version of
  Puppet (will include it in standard library)
* autosign.conf - sign based on DNS or domain name (can be a security disadvantage)
* unless autosigning is enabeld, certificates must be signed manually using
  "puppet cert"
* "puppet cert --list" to see all certificates on the master where agents certs are 
  waiting to be signed 
* cert names and host names are two separate things
* "puppet describe" is like the man page for Puppet
* See "Learning Puppet" series on the web

Reporting
---------
* certain things that are of interest can be tagged
* in a report is transaction data and metric data
* if a run takes an hour (installing a bunch of packages), the next run will
  not occur again until another half an hour goes by
* built-in report handlers - http, https, tagmail, log, rrdgraph, store
* new report handlers can be written in Ruby
* tagmail delivers log reports based on tags to one or more email inboxes
* "puppet exec" can run an external script or command on the agent
* exec can be made sort of idempotent based on onlyif and other logic

Resources
---------
* Core resource types: user, group, host, cron, exec, file, package, service
* Learn more about each resource type with "puppet describe [resource type]"
* Meta resources: filebucket, notify, resources, schedule
* File resource: symlink with "ensure => symlink"
* You can manage file content, in source we would have:
  puppet:///modules/sudo/sudoers (always have modules, sudo is module name, then
  sudoers is file name)
* when Puppet starts managing a file, the file will always be reverted back to
  what is in the module itself
* service completes the "trifecta" of package-file-service, where we install
  with package, manage its configuration files, and start/stop the service
* exec operates similar to a service

Dependency Management
---------------------
* metaparameters - explicitly define resource relationships
* metaparameters work with all resource types
* four metaparameters to establish relationships between resources
* require <--> before (sometimes a service requires a package, or sometimes
  a service must be running before a package is installed)
* subscribe <--> notify
* example: "require => File['/root/master_home/'],"
* example:
  "
         package { 'openssh':
           ensure => present,
         }
         service { 'ssh':
           ensure => running,
           enable => true,
           require => Package['openssh']
         }
  "
* refer to references by their title, not the name
* Catalog is exactly the same whether you use require or before
* subscribe is when Puppet changes the referenced resource, the containing
  reference receives a refresh event
* example subscribe: "subscribe => File['/etc/ssh/sshd_config'],"
* there is a newer Puppet construct for chaining dependencies
* run stages are not good - recommendation to not use them except where you
  really know what you are doing
* package-file-service design pattern is useful and common
* puppet parser validate ensures curly braces are set, you are not missing
  commas and colons, etc, but does not validate attribute => value pairs
* puppet-lint is on github and is a style guide tool for Puppet code
* Implicit dependencies: files and directories (directory must exist before
  the file), also between file ownership and user resources (create user
  before file which is owned by that user)
* 

