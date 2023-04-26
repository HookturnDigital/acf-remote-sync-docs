# Customizing request authentication

API keys are tokenised with each request using a time-based tokenisation algorithm. This ensures that the API key is
only valid for a maximum of two minutes (using UTC times). API tokens are sent via the `X-ACF-Remote-Sync-Token` request
header.

## Changing the request header name

You may change the request header if you wish using the `acfrs/api_token/request_header` filter as follows:

```php
add_filter( 'acfrs/api_token/request_header', function () {
	return 'My-Custom-Header';
} );
```

If you change the request header name, you will need to change the request header name on the remote site as well or the
plugin will not be able to validate the token and the request will fail.

## Disabling time-based tokenisation

If you are using a secure https connection between the sites,
you may wish to disable time-based tokenisation if you run into
the [Invalid API Token error](Invalid%20API%20token%20error.md).

To disable time-based tokenisation, add the following code to your site's `functions.php` file, a custom plugin, or a
code-snippet manager:

```php
add_filter( 'acfrs/api_token/disable_tokenisation', '__return_true' );
```

With tokenisation disabled, the raw API key is sent with each request in the authorization header. For security reasons,
you should only disable time-based tokenisation if you are using a secure https connection between the sites as this
will help reduce the chances of a replay attack if someone were recording network requests.

Whilst it is only necessary to disable tokenisation on the site sending the request, you may still wish to do this on
all sites in the network. 