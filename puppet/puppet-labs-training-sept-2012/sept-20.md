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
* 
