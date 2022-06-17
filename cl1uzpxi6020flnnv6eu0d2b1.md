## WP-CLI LocalWP without “Open Site Shell” (redux)

Note, this post is also posted over at [dev.to](https://dev.to/aubreypwd/wp-cli-localwp-without-open-site-shell-redux-k7e)

----------

This is going to be short (*I've been meaning to write it for a while*), **but first go read [this post](https://salferrarello.com/wp-cli-local-by-flywheel-without-ssh/) by my good friend Sal Ferrarello as a precursor to this one**, then come back and read this.

----------

Now that you've read Sal's post, you can actually do this easier now using [Local](https://localwp.com):

You **don't** need to create a `wp-cli.local.yml` or `wp-cli.local.php` file, all you need to do is edit your current `wp-config.php` and find this section:


![CleanShot 2022-04-11 at 11.24.10@2x.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649697864970/UAGgcDG7C.jpg)

Now change the part where you have `define( 'DB_HOST', 'localhost' );` and change it to:

```php
defined( 'WP_CLI' ) && WP_CLI
	? define( 'DB_HOST', 'localhost:/Users/aubreypwd/Library/Application Support/Local/run/do55POv0_/mysql/mysqld.sock' )
	: define( 'DB_HOST', 'localhost' );
```

...and replace `/Users/aubreypwd/Library/Application Support/Local/run/do55POv0_/mysql/mysqld.sock` with *your* sock file from Local:


![CleanShot 2022-04-11 at 11.19.14@2x.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649697564895/EEFOPyoAZ.jpg)

...and that's all you need to do now!

![CleanShot 2022-04-11 at 11.26.42@2x.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649698015043/XYN2zIUzd.jpg)
