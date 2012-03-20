Python and AWS Cookbook
=======================

Set Up
~~~~~~
* boto logging can be set up with the debug parameter, for example:
  boto.set_stream_logger('paws') # send debug output to Python shell
  ec2 = boto.connect_ec2(debug=2)
* for more info on debugging, see the Python logging module

EC2
~~~
* 

S3
~~
* S3 buckets must be unique across all regions (US East, US West, Europe, etc)
