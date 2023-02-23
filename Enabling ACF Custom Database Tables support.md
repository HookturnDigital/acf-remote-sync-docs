# Enabling ACF Custom Database Tables support

By default, ACF Remote Sync will remove any field group settings associated
with [ACF Custom Database Tables](https://hookturn.io/downloads/acf-custom-database-tables/). If you are using ACF
Custom Database Tables and wish to sync these settings, you may use the
the `acfrs/rest/should_export_acf_custom_database_table_settings` filter as per the example below.

```php
add_filter( 'acfrs/rest/should_export_acf_custom_database_table_settings', '__return_true' );
```

You may place this code in your theme's `functions.php` file, a custom plugin, or an mu-plugin. You may also
use a snippet manager plugin. Note that this needs to be added to the site where the custom tables are already enabled
on the field group.

Once the field group is imported with the ACF Custom Database Tables settings, it will need to be saved and the table
creation process will need to be executed to create the database tables and generate the table map.