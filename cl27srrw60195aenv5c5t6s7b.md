## In Process.php line 441: The process has been signaled with signal "6" when running composer on Mac

Note, this post is also posted on [dev.to](https://dev.to/aubreypwd/in-processphp-line-441-the-process-has-been-signaled-with-signal-6-when-running-composer-on-mac-5b62) where I am primarily writing right now!

----------

![CleanShot 2022-04-20 at 10.29.02@2x.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1650472147900/8Udoy1bou.jpg)

As you can see, I've been through some hell this morning. First of all, you're only going to get presented with:

```bash
In Process.php line 441:

  The process has been signaled with signal "6".
```

...if there is a `composer.json` file in the current working directory, so if you run `composer` right now in, say, `$HOME` you're going to think it's working, but if you're here you likely have figured this out...

I did _so_ much googling this morning. But I eventually landed on [this](https://bekirdag.com/post/macosx-composer-the-process-has-been-signaled-with-signal-6/), which gave me a clue...

Running `composer -vvv` I saw the same thing, and running `svn --version` I was presented with a new error:

```bash
dyld[92827]: Symbol not found: _apr_crypto_block_cleanup
  Referenced from: /opt/homebrew/Cellar/subversion/1.14.2/lib/libsvn_subr-1.0.dylib
  Expected in: /usr/lib/libaprutil-1.0.dylib
```

So I reinstalled `svn`, `php`, and `composer` a bazillion times, no effect. But then I landed on [this](https://github.com/afragen/setup-phpunit/issues/5) in my _googling_ and figured, what the hell and ran the suggested fix on that seemingly unrelated issue:


```bash
brew reinstall apr-util
```

And...it worked! I don't really know what [`apr-util`](https://formulae.brew.sh/formula/apr-util#default) is, but it seems to have at least fixed my problem for now, *and hopefully yours!*

![CleanShot 2022-04-20 at 10.35.00@2x.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1650472505732/VnIojsO06.jpg)
