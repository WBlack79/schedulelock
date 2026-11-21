# ScheduleLock

A KOReader plugin that restricts device usage based on daily quotas and weekly schedule windows. It can also require a PIN to exit KOReader, change plugins, or set the time and date. Useful as a simple screen-time control for a shared or child's e-reader.

## Tested on

Developed and tested on a **Kindle Paperwhite 12th Gen** running **KOReader 2026.07.02**.

Reports from other devices are welcome.

## Install or update

1. Download `schedulelock.koplugin.zip` from the Releases page and unzip it. You should have a folder named `schedulelock.koplugin`.
2. Connect your e-reader to a computer with USB.
3. Copy the whole `schedulelock.koplugin` folder into KOReader's `plugins` folder. When updating, replace the existing folder.
4. Eject the device and restart KOReader.

Your settings are kept when you update. To uninstall, delete the plugin folder (and `settings/schedulelock.lua` to remove your saved settings).

## Quick start

1. Open **Top menu → Tools icon → ScheduleLock** (it may be on page 2).
2. Change the passcode first under **Set/Change Passcode**. The default is `1234`.
3. Set your limits under **Set Days, Hours & Limits**.
4. Turn on **Enable ScheduleLock** to start the limits.
5. Under **Protections**, turn on whichever PIN locks you want.

Everything is off until you switch it on.

## Menu

- **Enable ScheduleLock**: switches the schedule limits on or off: time counting, the 5-minute warning and the lock screen. It does not affect the Protections. Turning it off requires the passcode.
- **Used Today**: minutes used today out of today's limit.
- **Set Days, Hours & Limits**: set a default limit, then tap a day to set its start time, end time and limit in minutes. Each part is optional.
- **Protections**: three separate switches, each independent of the schedule limits:
  - **Lock Exit**: exiting KOReader needs the passcode.
  - **Lock Plugin Management**: enabling or disabling any plugin needs the passcode.
  - **Lock Time & Date**: **Set time** and **Set date** need the passcode. (KOReader only shows these on devices where it can set the clock.)
- **Set/Change Passcode**: numeric passcode (digits only), shared by everything above.
- **Check For Update**: checks the latest GitHub release (needs Wi-Fi).
- **About**: version, repository and license.

While any lock is on, turning something off or changing a setting (limits, schedule, passcode, Protections) needs the passcode. Turning something on never does.

<img width="318" height="424" alt="FileManager_2026-11-21_175035" src="https://github.com/user-attachments/assets/5dedf3da-b324-4900-9e3e-080175ea19d7" />

## How it works

- **Limits:** each day can have its own limit in minutes. A day without one uses the default limit. A limit of 0 blocks that day.
- **Hours:** each day can have a start and end time. A day with none can be used at any hour. Overnight windows (for example 22:00 to 06:00) work and count toward the day they start.
- **What counts as usage:** only time spent with a book open and the screen awake. Time on the main screen, asleep, or with the screensaver showing is not counted.
- **Warning:** when 5 minutes remain, a message appears and stays on screen until tapped.
- **Locking:** when the limit is reached or you are outside the allowed hours, a full-screen lock covers KOReader, including the library. Tap **Unlock** and enter the passcode to lift the schedule lock until midnight. This does not unlock the Protections.
- **Reset:** used time resets to zero at midnight.
- **Restart:** restarting KOReader is not locked.

<img width="318" height="424" alt="FileManager_2026-11-21_175039" src="https://github.com/user-attachments/assets/733d1da8-1f78-4fd2-b54e-502e23ae83df" />

## Limitations

This is a simple deterrent, not a security system.

- The Protections cover KOReader's menu entries. A gesture or shortcut mapped to the Exit action is not covered.
- The plugin-management lock relies on a KOReader internal. If your version differs, the plugin logs a warning and plugin toggles stay unlocked.
- The passcode is stored in plain text in `settings/schedulelock.lua`.
- USB access or a forced reboot can bypass it.
- Changing the clock by any route other than the locked Set time and Set date entries can affect the schedule.
- An unlock is forgotten if KOReader restarts.

## Credits

Written by Walter Black, working with [Claude](https://claude.ai), Anthropic's AI model.

## License

[AGPL-3.0](LICENSE), the same license as KOReader.
