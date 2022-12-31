# Wordpress_Hardening

## First based on hosting
>Qualities of a trusted web host might include:
Readily discusses your security concerns and which security features and processes they offer with their hosting.
Provides the most recent stable versions of all server software.
Provides reliable methods for backup and recovery.

## Second the application
> To understand where and why this is important you must understand how websites get hacked, Rarely is it attributed to the infrastructure, and most often attributed to the application itself (i.e., the environment you are responsible for).

## Two-step authentication as an additional security measure.
- https://wordpress.org/support/article/two-step-authentication/

## Brute force 
- https://wordpress.org/support/article/brute-force-attacks/

## Change username 
```sql
UPDATE wp_users SET user_login = ‘newuser’ WHERE user_login = ‘admin’;
```
- https://wordpress.org/plugins/change-username/

## Backups automatic
- https://www.wpbeginner.com/plugins/7-best-wordpress-backup-plugins-compared-pros-and-cons/

## Monitoring
- https://sucuri.net/wordpress-security-plugin/?cjevent=2d7cadf7889311ed822b21110a18b8fc&cj_aid=13942195&cj_pid=3496629&cj_cid=2282257
- https://www.malcare.com/


## Monitoring & integrity files
- https://www.wpwhitesecurity.com/wordpress-file-integrity-scanning-site/
- https://www.wpwhitesecurity.com/wordpress-plugins/website-file-changes-monitor/
- https://kinsta.com/blog/file-integrity-monitoring/


## Firewall 
- https://www.wpbeginner.com/plugins/best-wordpress-firewall-plugins-compared/

## Disable PHP File Execution in Certain WordPress Directories
- https://www.wpbeginner.com/wp-tutorials/how-to-disable-php-execution-in-certain-wordpress-directories/
- https://www.malcare.com/blog/disable-php-execution-directory-browsing/


## Change WordPress Database Prefix
- https://www.wpbeginner.com/wp-tutorials/how-to-change-the-wordpress-database-prefix-to-improve-security/

## Disable Directory Indexing and Browsing
- https://www.wpbeginner.com/wp-tutorials/disable-directory-browsing-wordpress/

## Disable XML-RPC in WordPress
- https://www.wpbeginner.com/plugins/how-to-disable-xml-rpc-in-wordpress/

## Automatically log out Idle Users in WordPress
- https://wordpress.org/plugins/inactive-logout/

## Add Security Questions to WordPress Login Screen [not sure]
- https://www.wpbeginner.com/plugins/how-to-add-security-questions-to-wordpress-login-screen/

## Implement least privilege permissions
- https://wordpress.org/support/article/roles-and-capabilities/

## Keep an audit log
- https://wordpress.org/plugins/wp-security-audit-log/

## Change security keys
It’s recommended to replace your old keys and salts from time to time. To get a fresh set of keys and salts you can use this link: Secret Key. You will get a page that looks like this: 
https://api.wordpress.org/secret-key/1.1/salt/

## Disallow plugin installations
By adding a line of code to your wp_config php file

Follow the same method as detailed in the previous section, you need to add the following line:

`define(‘DISALLOW_FILE_MODS’,true);`

## Use SFTP
- https://kinsta.com/knowledgebase/how-to-use-sftp/

## Restrict the WordPress REST API
- https://wordpress.org/plugins/disable-json-api/
```php
add_filter( 'rest_authentication_errors', function( $result ) {
if ( ! empty( $result ) ) {
return $result;
}
if ( ! is_user_logged_in() ) {
return new WP_Error( 'rest_not_logged_in', 'You are not currently logged in.', array( 'status' =&amp;amp;gt; 401 ) );
}
return $result;
});
```

- https://developer.wordpress.org/reference/hooks/rest_authentication_errors/
- https://developer.wordpress.org/reference/hooks/rest_jsonp_enabled/

## Prevent version disclosure
- https://gist.github.com/Auke1810/f2a4cf04f2c07c74a393a4b442f22267

## Prevet enumeraiton
- /?author=<number>.
- https://www.wpwhitesecurity.com/wordpress-security/

## Prevent Prevent Hotlinking
- https://kinsta.com/blog/hotlinking/
- https://kinsta.com/blog/wordpress-security/#17-prevent-hotlinking


## Check files permission
- https://www.wpwhitesecurity.com/wordpress-file-permissions-guide-secure-website-server/
- https://www.wordfence.com/learn/how-to-restrict-wordpress-file-permissions/

## Disable Trackbacks and Pingbacks
- https://wpmudev.com/blog/trackback-pingback-spam/

## Hide PHP Errors
```php
define( 'WP_DEBUG', true);
```

## Add Latest HTTP Security Headers
- https://kinsta.com/blog/wordpress-security/#11-add-latest-http-security-headers
- https://www.wpbeginner.com/beginners-guide/how-to-add-http-security-headers-in-wordpress/


# Links
- https://wordpress.org/support/article/hardening-wordpress/
- https://wordpress.org/support/category/security/
