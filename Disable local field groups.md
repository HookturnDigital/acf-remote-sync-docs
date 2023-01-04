# Disable local field groups

By default, ACF Remote Sync will list all field groups for sync — this includes field groups registered via PHP or field
groups loaded via ACF JSON. If you wish to prevent local field groups from remote sync, you may use
the `acfrs/rest/list-local-field-groups` filter as per the example below.

```php
add_filter( 'acfrs/rest/list-local-field-groups', '__return_false' );
```

You may place this code in your theme's `functions.php` file, a custom plugin, or an mu-plugin. You may also
use a snippet manager plugin.