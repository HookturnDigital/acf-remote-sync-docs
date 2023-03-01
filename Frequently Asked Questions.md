# Frequently Asked Questions

## Can I sync field groups from a remote that are defined using JSON only?

Yes. Field groups that are not in the database but are loaded via JSON are listed as available for remote sync. Note
that when syncing the field group from a remote site it will be inserted into the database and if ACF JSON is in use, a
JSON file will also be created in the registered acf-json directory.

## Can I sync field groups from a remote that are defined using PHP only?

Yes. PHP registered field groups are listed as available for remote sync. Note that when syncing the field group from a
remote site it will be inserted into the database and if ACF JSON is in use, a JSON file will also be created in the
registered acf-json directory. The field group will not be imported as PHP.
