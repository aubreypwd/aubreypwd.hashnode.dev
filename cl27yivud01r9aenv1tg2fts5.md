## How to fix Mail.app on Mac taking long time to load

The answer is [here](https://apple.stackexchange.com/questions/138537/how-can-i-delete-my-mail-app-and-re-install-it), but I wanted to post with something that would catch Google searches, since _none_ of mine today worked until I was trying to delete `Mail.app` all-together to re-install it (which you can't really do).

----------

But, just run:

```bash
killall Mail &> /dev/null; mv ~/Library/Containers/com.apple.mail/Data/Library/Preferences/com.apple.mail.plist ~/Desktop && open -a Mail
```

If it works, delete the `com.apple.mail.plist` file on your Desktop!

...it worked on my machine ;)

**I did have to re-set all my Mail.app settings again, but worth it!**
