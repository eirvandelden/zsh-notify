**Find a version that works with iTerm2's nightlies in the
[“next-iterm” branch →](https://github.com/marzocchi/zsh-notify/tree/next-iterm)**

zsh-notify
=======

A plugin for the Z shell (on OS X and Linux) that posts desktop notifications
when a command terminates with a non-zero exit status or when it took more than
30 seconds to complete, if the terminal application is in the background (or
the command's terminal tab is inactive).

Requirements
---

- Terminal.app, [iTerm2][iterm2], or Ghostty on macOS, and any terminal
  emulator on Linux, should work. Only Terminal.app and iTerm2 support
  detecting whether their specific tab is active; Ghostty and Linux
  terminals can only detect whether the whole app/window is frontmost, and
  Linux falls back to always notifying if that can't be determined either.

- [noti][noti] is required for posting to macOS Notification Center or, on
  Linux, to notify-send.

- [growlnotify][growlnotify] is required for posting to Growl in previous
  versions of Mac OS X.

- notify-send (libnotify-bin) is required on Linux if noti isn't installed.
  Wmctrl is optional and provides support for focusing the terminal in
  addition to a notification in that fallback path.


Usage
---

Just source notify.plugin.zsh.

Configuration:
---

While notifications about failed commands are always posted, notifications
for successful commands are posted only if they took at least 30 seconds to
complete. To change the timeout set the NOTIFY_COMMAND_COMPLETE_TIMEOUT
environment variable to a different value in seconds.

Also, the plugin assumes that both `noti` and `growlnotify` are installed in
`/usr/local/bin`. You can change these defaults by setting the
`$SYS_NOTIFIER` or `$GROWL_NOTIFIER` environment variables.

On Linux if you have wmctrl installed and are falling back to notify-send
directly (no noti installed), then you can set the $ZSH_NOTIFY_FOCUS_TERMINAL
enviroment variable to "true" to change focus to the terminal emulator window
when a notification is posted. By default the terminal window will just
demand attention.


[growlnotify]: http://growl.info/extras.php/#growlnotify
[noti]: https://github.com/variadico/noti
[iterm2]: http://www.iterm2.com/

