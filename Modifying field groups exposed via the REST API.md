# Modifying field groups exposed via the REST API

You may override the field groups that render via the REST API by using the `acfrs/rest/field-groups` filter. This
filter makes it possible to:

1. Add field groups that are not already available.
2. Remove field groups.
3. Modify field groups and their fields in order to protect any data that should not be exposed.

## Examples

You may use any of these examples in your theme's `functions.php` file, a custom plugin, or an mu-plugin. You may also
use a snippet manager plugin.

### Add an ACF field group

```php
add_filter( 'acfrs/rest/field-groups', function ( $field_groups ) {

	$field_groups[] = [
		'key' => 'group_0987654321',
		'title' => 'My new field group',
		'fields' => [
			[
				'key' => 'field_0987654321',
				'label' => 'My new field',
				'name' => 'my_new_field',
				'type' => 'text',
			],
		],
	];

	// Return modified field groups array.
	return $field_groups;
} );

```

### Remove an ACF field group

```php
add_filter( 'acfrs/rest/field-groups', function ( $field_groups ) {

	// Remove the field group with the key 'group_1234567890'.
	foreach ( $field_groups as $index => $group ) {
		if ( $group['key'] === 'group_1234567890' ) {
			unset( $field_groups[ $index ] );
		}
	}

	// Return modified field groups array.
	return $field_groups;
} );
```

### Modify an ACF field group and/or its fields

```php
add_filter( 'acfrs/rest/field-groups', function ( $field_groups ) {

	// Modify a field group.
	$field_groups = array_map( function ( $group ) {
	
		if ( $group['key'] === 'group_639c42fde73e0' ) {
		
			// Modify the title of the field group.
			$group['title'] = 'My modified field group';

			// Modify the fields array.
			$group['fields'] = array_map( function ( $field ) {
			
				// Modify the label of a specific field.
				if ( $field['key'] === 'field_639c42fe7aa58' ) {
					$field['label'] = 'My modified field';
				}
				
				return $field;
				
			}, $group['fields'] );

			// Unset a field.
			foreach ( $group['fields'] as $index => $field ) {
				if ( $field['key'] === 'field_639c42fe7aa58' ) {
					unset( $group['fields'][ $index ] );
				}
			}
		}

		return $group;

	}, $field_groups );

	// Return modified field groups array.
	return $field_groups;
} );
```