# Introduction #

TODO: CMSMS Content

# CMSMS Installation #
  1. `svn co http://svn.cmsmadesimple.org/svn/cmsmadesimple/tags/<tag> /var/www/vhosts/domain.com/httpdocs/`
  1. Create DB:
    * Naming: domaincom\_cmsms
    * Collation: utf8\_unicode\_ci
    * `CREATE DATABASE  `domaincom\_cmsms` DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;`
    * add DB to your prefered cmsms user: `SGRANT SELECT , INSERT , UPDATE , DELETE , CREATE , DROP , INDEX , ALTER , CREATE TEMPORARY TABLES ON  'domaincom\_cmsms' . * TO 'cmsmsuser'@'localhost';`
  1. Edit config.php and adjust some non-default options:
  * `$config['persistent_db_conn'] = true;`
  * `$config['url_rewriting'] = 'mod_rewrite';`

# Update Process #

Short: Use the [shell script](http://code.google.com/p/mycodedump/source/browse/tools/cmsms-upgrade?repo=cmsms&amp;r=6c53bbb039124db628e3f6e3b1e3012b393e7761) and do `./cmsms-upgrade <domain> <svn-tag>`

Long:
  1. DB Backup
  1. cd to httpdocs of the website
  1. `svn cleanup`
  1. `svn update`
  1. `svn switch http://svn.cmsmadesimple.org/svn/cmsmadesimple/tags/ <new-tag> ./`
  1. `chmod 0777 config.php`
  1. if not existing: `create ./tmp/cache, ./tmp/templates_c`
  1. `http://domain.ch/install/upgrade.php`
  1. `chmod 0644 config.php`
  1. `svn remove ./install`
  1. `rm -Rf ./install`

# PHP Error reporting #
Error reporting should be configured in php.ini. If this option is not available try setting it in .htaccess:
```
#.htaccess settings for PHP 5.3.x
#The error reporting value in a .htaccess file has to be specified as an integer.  
php_value error_reporting 22527
```


# Smarty Plugins #
```
 * Smarty {mailto} function plugin
 *
 * Type:     function<br>
 * Name:     mailto<br>
 * Date:     May 21, 2002
 * Purpose:  automate mailto address link creation, and optionally
 *           encode them.<br>
 * Input:<br>
 *         - address = e-mail address
 *         - text = (optional) text to display, default is address
 *         - encode = (optional) can be one of:
 *                * none : no encoding (default)
 *                * javascript : encode with javascript
 *                * javascript_charcode : encode with javascript charcode
 *                * hex : encode with hexidecimal (no javascript)
 *         - cc = (optional) address(es) to carbon copy
 *         - bcc = (optional) address(es) to blind carbon copy
 *         - subject = (optional) e-mail subject
 *         - newsgroups = (optional) newsgroup(s) to post to
 *         - followupto = (optional) address(es) to follow up to
 *         - extra = (optional) extra tags for the href link
 *
 * Examples:
 * <pre>
 * {mailto address="me@domain.com"}
 * {mailto address="me@domain.com" encode="javascript"}
 * {mailto address="me@domain.com" encode="hex"}
 * {mailto address="me@domain.com" subject="Hello to you!"}
 * {mailto address="me@domain.com" cc="you@domain.com,they@domain.com"}
 * {mailto address="me@domain.com" extra='class="mailto"'}
 * </pre>
```


## Notes on upgrading to 1.10 ##
**[Upgrade notes](http://www.cmsmadesimple.org/2011/10/Announcing-CMS-Made-Simple-1-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+cmsmadesimple%2Fblog+%28CMS+Made+Simple%29)** upgrade all modules first!
**Need to set Microtiny in users preferences** config.php:
```
$config['persistent_db_conn'] = 'true';
$config['use_adodb_lite'] = 1;
```