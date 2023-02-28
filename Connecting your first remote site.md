# Connecting your first remote site

In order to connect your first remote site, you will first need to install and activate the plugin on both the local
site and the remote site. See [installing and activating the plugin](Installing%20and%20activating%20the%20plugin.md)
for more information.

## Adding a remote site

Once the plugin is installed and activated on both the local and remote sites, you will need to add the remote site's
domain and access key to the local site. Head to **WP Admin > Settings > ACF Remote Sync** and in the **Connected Sites
** field, click the **Add Site** button:

![Adding a remote site](../images/adding-a-new-acf-remote-site.jpg)

In the new site row, add the remote site's domain and access key. The access key can be found by logging into the remote
site and heading to **WP Admin > Settings > ACF Remote Sync**. The access key is displayed in the **Site Access Key**
field and can be copied by clicking the **Copy** button:

![Copying the site access key](../images/copying-an-acf-remote-site-access-key-to-clipboard.jpg)

Once the domain and access key have been added, click the **Update** button. The settings page should look similar to
the following:

![Remote site configured](../images/settings-page-with-remote-site-configured.jpg)

## Checking the remote site has been connected

To confirm that the remote site has been added successfully, head to **WP Admin > ACF > Field Groups** and click the
**Remote** view link. If the remote is configured correctly, all field groups on the remote site will be listed on
screen ready for import:

![Remote field groups listed](../images/viewing-remote-acf-field-groups.jpg)