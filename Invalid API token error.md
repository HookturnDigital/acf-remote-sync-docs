# Invalid API Token Error

You may see the following error when trying to connect to a remote site:

```
Error fetching remote field groups. Invalid API token.
```

If you are seeing this error, it could mean one of a few things:

## The site access key for the remote site is incorrect.

The key may have been copied from the remote site to the local site incorrectly. Or, the remote site access key may have
been regenerated on the remote site since copying it to the local site. You can check the remote site access key by
logging into the remote site and navigating to **Settings > ACF Remote Sync**. Check the `Site Access Key` value is the
same as the value that is on the local site.

## The API token sent with each request is being removed or modified during the request.

The API token is sent with each request to the remote site in the `X-ACF-Remote-Sync-Token` request header. It's
possible that a plugin, theme, or the webserver itself is removing or modifying the request header in some way. You may
wish to use WordPress' core [`http_api_debug` filter](https://developer.wordpress.org/reference/hooks/http_api_debug/)
to check the request headers are being sent correctly. On the recieving end, you may use a plugin such
as [REST API Log](https://wordpress.org/plugins/wp-rest-api-log/) to log requests received by the server.

## The API token request header name may have been changed on one site only.

It is possible
to [change the request header name](Customizing%20request%20authentication.md#changing-the-request-header-name) used to
transmit the API token. If you have changed the request header on one site and not the other, the plugin will not be
able to validate the token. Make sure the request header name is changed across all sites in your network.

## The time-based tokenisation and validation is failing due to a time difference between the servers.

The API token is generated using a time-based tokenisation algorithm and ensures a token is only valid for a maximum of
two minutes (using UTC times). If one of the servers time is out of sync with the other, the token may be considered
expired. You
may [disable time-based tokenisation](Customizing%20request%20authentication.md#disabling-time-based-tokenisation) in
the situation although we only recommend doing this if you are using a secure https connection between the sites.