# Wordpress_Hardening

## First based on hosting
>Qualities of a trusted web host might include:
Readily discusses your security concerns and which security features and processes they offer with their hosting.
Provides the most recent stable versions of all server software.
Provides reliable methods for backup and recovery.

## Second the application
> To understand where and why this is important you must understand how websites get hacked, Rarely is it attributed to the infrastructure, and most often attributed to the application itself (i.e., the environment you are responsible for).

## Two-step authentication as an additional security measure.
- plugin: https://wordpress.org/support/article/two-step-authentication/

## Brute force 
- article: https://wordpress.org/support/article/brute-force-attacks/

## Change username 
- plugin: https://wordpress.org/plugins/change-username/

## Backups automatic
- article: https://www.wpbeginner.com/plugins/7-best-wordpress-backup-plugins-compared-pros-and-cons/

## Automatically log out Idle Users in WordPress
- plugin: https://wordpress.org/plugins/inactive-logout/

## Firewall 
- plugin: https://www.wpbeginner.com/plugins/best-wordpress-firewall-plugins-compared/

## Hide login path
- https://wordpress.org/plugins/wps-hide-login/
- https://kinsta.com/blog/wordpress-login-url/
- https://it.siteground.com/kb/effettuare-login-wordpress/

## Disable XML-RPC in WordPress
- plugin: https://www.wpbeginner.com/plugins/how-to-disable-xml-rpc-in-wordpress/
- plugin: https://wordpress.org/plugins/sg-security/

## Restrict the WordPress REST API
- plugin: https://wordpress.org/plugins/disable-json-api/

## Monitoring
- plugin: https://sucuri.net/wordpress-security-plugin/
- article: https://www.malcare.com/

## Monitoring & integrity files
- article: https://www.wpwhitesecurity.com/wordpress-file-integrity-scanning-site/
- plugin: https://www.wpwhitesecurity.com/wordpress-plugins/website-file-changes-monitor/
- article: https://kinsta.com/blog/file-integrity-monitoring/

## Add Security Questions to WordPress Login Screen [not sure]
- plugin: https://www.wpbeginner.com/plugins/how-to-add-security-questions-to-wordpress-login-screen/

- https://developer.wordpress.org/reference/hooks/rest_authentication_errors/
- https://developer.wordpress.org/reference/hooks/rest_jsonp_enabled/

## Keep an audit log
- plugin: https://wordpress.org/plugins/wp-security-audit-log/

## Disable PHP File Execution in Certain WordPress Directories
- article: https://www.wpbeginner.com/wp-tutorials/how-to-disable-php-execution-in-certain-wordpress-directories/
- article: https://www.malcare.com/blog/disable-php-execution-directory-browsing/

## Change WordPress Database Prefix
- article: https://www.wpbeginner.com/wp-tutorials/how-to-change-the-wordpress-database-prefix-to-improve-security/

## Disable Directory Indexing and Browsing
- article: https://www.wpbeginner.com/wp-tutorials/disable-directory-browsing-wordpress/

## Implement least privilege permissions
- article: https://wordpress.org/support/article/roles-and-capabilities/

## Disable author pages with posts / Prevet enumeraiton
- https://blog.futtta.be/2015/03/03/quick-tip-disabling-wordpress-author-pages/
- https://www.wpbeginner.com/wp-themes/how-to-remove-author-name-from-wordpress-posts/
- https://www.wpwhitesecurity.com/wordpress-security/

## Change security keys
It’s recommended to replace your old keys and salts from time to time. To get a fresh set of keys and salts you can use this link: Secret Key. You will get a page that looks like this: 
https://api.wordpress.org/secret-key/1.1/salt/

## Disallow plugin installations
By adding a line of code to your wp_config php file
`define(‘DISALLOW_FILE_MODS’,true);`

## Disable edit file
By adding a line of code to your wp_config php file
- `define('DISALLOW_FILE_EDIT', true );`

## Use SFTP
- https://kinsta.com/knowledgebase/how-to-use-sftp/

## Prevent version disclosure
- https://gist.github.com/Auke1810/f2a4cf04f2c07c74a393a4b442f22267


## Prevent Hotlinking
- https://kinsta.com/blog/hotlinking/
- https://kinsta.com/blog/wordpress-security/#17-prevent-hotlinking

## Check files permissions
- https://www.wpwhitesecurity.com/wordpress-file-permissions-guide-secure-website-server/
- https://www.wordfence.com/learn/how-to-restrict-wordpress-file-permissions/

## Disable Trackbacks and Pingbacks
- https://wpmudev.com/blog/trackback-pingback-spam/

## Hide PHP Errors
By adding a line of code to your wp_config php file
`define( 'WP_DEBUG', true);`

## Add HTTP Security Headers
- https://kinsta.com/blog/wordpress-security/#11-add-latest-http-security-headers
- https://www.wpbeginner.com/beginners-guide/how-to-add-http-security-headers-in-wordpress/

## Filter upload files
- https://blog.hubspot.com/website/file-type-not-permitted-security-reasons

## Protected login with password
- https://websitesetup.org/wordpress-security/ (12-d)
- https://websitesetup.org/wordpress-security/ (18-a)
- https://websitesetup.org/tools/htaccess-generator/

## Deny Access to Your .htaccess and wp-config.php Files
- https://websitesetup.org/wordpress-security/ (21-a)

## Limit ip address
- https://websitesetup.org/wordpress-security/ (21-b)

## Remove defunct Plugins/themes
- https://www.getastra.com/blog/cms/wordpress-security/wordpress-security-guide/ (4)

## Fix File persions
- https://www.getastra.com/blog/cms/wordpress-security/wordpress-security-guide/ (19)

## Remove leakage information
- https://gist.github.com/zergiocosta/72f87176b236ed0c6e13 [error message]

## Remove untrusted entry point from the theme

## Protected from IP

## Track 404 pageviews

## Replace default jQuery file

# Reference
- https://secupress.me/wp-content/uploads/Beginner-SecuPress-WordPress-Security-Checklist.pdf
- https://www.keycdn.com/blog/wordpress-security
- https://99robots.com/wordpress-security-checklist/
- https://secure.wphackedhelp.com/blog/wordpress-security-checklist-guide/#6
- https://wpsupportdesk.com/blog/wordpress-security-checklist/
- https://www.wordfence.com/wp-content/uploads/2015/12/Wordfence-How-To-Secure-Your-WordPress-Website-Checklist.pdf
- https://www.wpsupporters.com/wordpress-security-checklist/
- https://deepsource.io/blog/zero-downtime-deployment/
- https://wordpress.org/support/article/hardening-wordpress/
- https://wordpress.org/support/category/security/
