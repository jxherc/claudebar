# ClaudeUsageBar

macOS menu bar app that shows your Claude usage limits, with a real "Log in with Claude" button instead of pasting session cookies out of dev tools.

click the menu bar icon, hit **Log in with Claude**, and sign in on the normal claude.ai page. the window closes by itself once it has your session. **Log out** clears it so you can switch accounts.

## credit

this is a modified copy of [ClaudeUsageBar](https://github.com/Artzainnn/ClaudeUsageBar) by [Artzainnn](https://github.com/Artzainnn) ([claudeusagebar.com](https://www.claudeusagebar.com/)). the usage display, notifications, status tracking and the rest of the app are their work. it's MIT licensed and the original copyright notice is kept in [LICENSE](LICENSE).

what's different here:

- built-in claude.ai login window replaces the cookie paste box
- an expired session shows the login button again instead of a bare http error
- upstream update check is off, since installing an upstream release would swap this back to the cookie version
- popup sizes itself correctly when built on the macOS 27 SDK (the top used to get cut off)

if you just want the original, get it from their repo or site.

## build

```
./build.sh
```

needs Xcode (the script picks up `/Applications/Xcode*.app`). command line tools alone can't build SwiftUI on the macOS 27 SDK. output goes to `build/ClaudeUsageBar.app`, signed ad-hoc.

## install

quit the running app, then copy `build/ClaudeUsageBar.app` to `/Applications`.

macOS treats each new build as a different app, so the Cmd+U shortcut needs Accessibility permission again after you reinstall.
