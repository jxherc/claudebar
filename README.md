# ClaudeUsageBar

macOS menu bar app that shows your Claude usage limits. no cookies to paste and no login window: it reads the login Claude Code already has.

if Claude Code is signed in on your Mac, the app just works. if it isn't, run `claude` in a terminal and sign in, then hit **Try again** in the popup. it shows the account Claude Code is signed into.

## credit

this is a modified copy of [ClaudeUsageBar](https://github.com/Artzainnn/ClaudeUsageBar) by [Artzainnn](https://github.com/Artzainnn) ([claudeusagebar.com](https://www.claudeusagebar.com/)). the usage display, notifications, status tracking and the rest of the app are their work. it's MIT licensed and the original copyright notice is kept in [LICENSE](LICENSE).

what's different here:

- usage comes from `api.anthropic.com` with Claude Code's login, read from the keychain through `/usr/bin/security`. claude.ai's api now puts a cloudflare "verify you are human" check in front of apps, so the cookie way stopped working (upstream issue [#112](https://github.com/Artzainnn/ClaudeUsageBar/issues/112))
- the free credits line is gone, that number only came from claude.ai
- upstream update check is off, since installing an upstream release would swap this back to the cookie version
- popup sizes itself correctly when built on the macOS 27 SDK (the top used to get cut off)

Claude Code's login token lasts a few hours and Claude Code renews it when you use it. if you haven't used Claude Code in a while, the app says the login expired until you open it again.

if you just want the original, get it from their repo or site.

## build

```
./build.sh
```

needs Xcode (the script picks up `/Applications/Xcode*.app`). command line tools alone can't build SwiftUI on the macOS 27 SDK. output goes to `build/ClaudeUsageBar.app`, signed ad-hoc.

## install

quit the running app, then copy `build/ClaudeUsageBar.app` to `/Applications`.

macOS treats each new build as a different app, so the Cmd+U shortcut needs Accessibility permission again after you reinstall.
