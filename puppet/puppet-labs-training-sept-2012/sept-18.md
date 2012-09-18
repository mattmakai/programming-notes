Puppet Labs - Puppet Fundamental Training
=========================================

September 18, 2012 - taught by Zack Smith (zack@puppetlabs.com)

Introduction
------------
* Puppet advantage in level of detailed simulation
* Facts - pieces of inventoried data (custom pieces of information) that the
  client sends to the Puppet Master (facts are inventory information)
* conditional logic happens on the puppet master, not the puppet agents
* Puppet Master sends the Catalog to the individual nodes (puppet agents)
* Puppet caches the Catalog so it can manage itself even when network
  connectivity to the Puppet Master is cut off
* SSL encryption used on all transmission between Master and agents
* Reports can be many forms, such as emails, IRC chat, or custom
* Puppet Enterprise is a stack that uses Puppet Open Source and provides
  certain additional features better role-based access control, support
  contracts, GUI, VMWare VM provisioning, and MCollective built in
* Razor - tool built by EMC to provision bare metal servers
* command puppet 

Setting Up
----------
* "puppet cert --list" command on the puppet master lists all certs waiting
  to be signed
* search puppetlabs.com for autosign.conf to see how you can automatically
  sign certs from agents (useful for development environments)
* PSSigner on github - wrapper for web-based certificate signing protocol
* "puppet cert --sign [name]" to sign an individual certificate
* "puppet cert --sign --all" to sign all certificates

Puppet Enterprise Console
-------------------------
* no automatic syncing for puppet modules (intentional) - manage the disconnect
  in the user interface
* Puppet is idemopotent
* there is a desired configuration state, puppet sees the drift in a node state,
  and uses convergence back to the desired state, then creates and sends a report
* granularity in individual attributes
* Puppet builds a graph of dependent resources
* order does not matter in Puppet code, dependencies are set up automatically
  or manually
* Puppet Resources are building blocks, combine them to make larger components
* Package-File-Service for Puppet Resources
* Puppet can both create Resources and remove them (for example you can have
  it remove users you no longer want - and run that across 1000s of servers)
* "puppet describe user" - equivalent of man pages for "user", also do
  "puppet describe [command]" for other modules
* there is only a single Catalog, you cannot have 2 different packages with
  the same title
* providers are the interface between the underlying OS and the resource types
* "puppet resource user root" -> shows the puppet code for how you would write
  the Puppet source to create the user root that mimics the one on this system

Modules and Classes
-------------------
* nodes are groups of classes that define behavior
* site.pp is important in Puppet open source but not in Enterprise (because that
  is database-driven)
* classes must have unique names! otherwise code will not work
* modules are folders that contain the configuration
* manifests is a key folder for Puppet, along with init.pp inside of it
* auto-loading of classes (previously you had to tell your Puppet Master where
  to find your manifests)
* within modules, classes are placed in predictable locations (and manifests
  helps tell where they are)
* there is a difference between defining and declaring
* *define* - specify contents and behavior
* *declare* - direct Puppet to include or instantiate a class
* you can use "puppet apply" locally and not use a Puppet master if desired
* "puppet apply --noop" simulates what would actually happen without enforcing
  a change
