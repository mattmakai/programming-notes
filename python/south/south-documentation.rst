South Official Tutorial
=======================
http://south.aerocode.org/docs/tutorial/

Part 1: The Basics
~~~~~~~~~~~~~~~~~~
* install South with the usual: `pip install South`, add South to settings.py,
  then `python manage.py syncdb` to create the South migration tables
* several ways of creating migrations, some automatic, some manual
* two automatic ways are `--auto` and `--initial`
* `--inital` used to create the initial migration so you can then use `--auto`
* example initial migration for southtut app: 
  `./manage.py schemamigration southtut --initial`, 
  then `./manage.py migrate southtut`
* to apply change to table after initial migration, first create a migration
  for the change, then apply it to the database
* make a new migration: `./manage.py schemamigration southtut --auto`
* apply migration: `./manage.py migrate southtut`

Part 2: Advanced Changes
~~~~~~~~~~~~~~~~~~~~~~~~
* if a column is NOT NULL then South needs a default value for previous
  data in the databasea
* either add a default value for the NOT NULL field to the models.py file
  or when creating a migration it will prompt for a one-off value
* if a one-off value is used, it will only be used for existing rows, never
  for new rows that are created after the database migration
* South detects changes such as unique=True and adds the unique constraint
  when the migration is applied (also with unique_together in Meta)
* custom fields are not automatically handled by South - there are manual
  ways to handle them

Part 3: Advanced Commands and Data Migrations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* to list available and applied migrations, use `./manage.py migrate --list`
* migrations with an asterisk next to them have been applied while those that
  have not been applied have a space
* data migrations are also covered by South, see the documentation for an 
  example of transitioning from plaintext to hashed passwords in three
  migration steps
* data migrations are performed with skeleton data migrations that are
  Python functions meant to be edited manually
* a caveat to the data migration is that custom methods and managers on models
  are not preserved - they must be copied manually

Part 4: Custom Fields
~~~~~~~~~~~~~~~~~~~~~

