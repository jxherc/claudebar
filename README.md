# ClaudeUsageBar

macOS menu bar app that shows your Claude usage limits. based on [ClaudeUsageBar](https://github.com/Artzainnn/ClaudeUsageBar) (MIT).

the change: no more pasting session cookies out of dev tools. click "Log in with Claude" in the popup, sign in on the normal claude.ai page, and the window closes by itself once it has your session. "Log out" clears it, so you can switch accounts.

## build

```
./build.sh
```

needs Xcode (the script picks up `/Applications/Xcode*.app`). command line tools alone can't build SwiftUI on the macOS 27 SDK. output goes to `build/ClaudeUsageBar.app`, signed ad-hoc.

## install

quit the running app, then copy `build/ClaudeUsageBar.app` to `/Applications`.

macOS treats each new build as a different app, so the Cmd+U shortcut needs Accessibility permission again after you reinstall.
