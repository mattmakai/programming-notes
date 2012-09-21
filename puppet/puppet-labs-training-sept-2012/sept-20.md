Puppet Labs - Puppet Fundamental Training
=========================================

September 20, 2012 - taught by Zack Smith (zack@puppetlabs.com)

Review
------
* content => template('apache/foo.erb')
* functions happen master side, facts happen client side
* source => puppet:///modules/apache/filename.pp

Templates
---------
* <%= @port %>   # port is a variable that exists when the template was called
* never have more than 2 defined resource types within a .pp file


Language Constructs
-------------------
* metaparameters - alias, audit, noop, loglevel, schedule, tag
* you can create a tag for say, vhosts, so whenever a new vhost is created you
  can send out an email to notify interested parties
* noop - tells the resource to take no action (can be done on an individual
  resource types)
* schedule - schedule is not a guarantee, but creates a window of opportunity,
  so like run apt-get daily (cron is better for things that *must* run)
* Puppet has 3 conditional expressions: 1. selector, 2. case statement,
  3. if/else/elsif statements
* selectors return a value, while case & if/else/elsif alter logic flow
* important distinction between selectors & case/if/else/elsif statements, is
  "fail" function, which causes the run to fail completely
* you can use the fail function with case & if/else/elsif statements but not
  with the selector
* selector example:
  """
    name => $::operatingsystem ? {
      'Ubuntu' => 'ssh',
      default  => 'openssh',
    },
  """
* selectors are great for doing quick operating system independent queries and
  then doing something based on that
* selector statements are NOT case sensitive
* in-statement and out-statement (put conditional logic in params.pp) selector,
  then include params.pp and scope the variable with $params::var 
* case statements are generally better because with many branches it is just
  cleaner
* undef - undefined variable

Functions and Nodes
-------------------
* Functions are pieces of Ruby code that get executed on the master (or
  locally with "puppet apply")
* the results of the functions are included in the Catalog
* two types of functions: statements, rvalues
* "include" is a function of the statement type
* "template" is an rvalue function
* "notice" function runs on the master and you can debug on the master before the 
  Catalog is compiled
* "notify" runs on the client
* external node classifiers are highly recommended
* virtual resources - when two modules want to install the same package of 
  the same package
* use virtual resources with the @ symbol in front of function names and
  the "realize" command on other functions or commands
* if you want to realize a bunch of things at a time, then use the
  "<| tag == [whatever] |>" to realize everything with that tag at a time

Advanced Classes
----------------
* classes can inherit from other classes
* parameterized classes: when you want to modify a class behavior on different 
  nodes
* content & source are mutually exclusive
* so if you want to undo a source variable declared in the parent class,
  do "source => undef" then define the content

Misc
----
* "puppet module generate [module name]" - generates module structure
* "puppet module install [module name]" - install a module from the forge,
  where [module name] is the FORGE name, but not the actual module name,
  ex: makai-apache, will install as apache
* modules can have dependencies - but better to not go overboard

