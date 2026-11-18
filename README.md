# TimeLock

A KOReader plugin that restricts device usage based on daily quotas and weekly schedule windows. Useful as a simple screen-time control for a shared or child's e-reader.

## Tested on

Developed and tested on a **Kindle Paperwhite 12th Gen** running **KOReader 2026.07.02**.

Reports from other devices are welcome.

## Install or update

1. Download `timelock.koplugin.zip` from the Releases page and unzip it. You should have a folder named `timelock.koplugin`.
2. Connect your e-reader to a computer with USB.
3. Copy the whole `timelock.koplugin` folder into KOReader's `plugins` folder. When updating, replace the existing folder.
4. Eject the device and restart KOReader.

Your settings are kept when you update. To uninstall, delete the plugin folder (and `settings/timelock.lua` to remove your saved settings).

## Quick start

1. Open **Top menu → Tools icon → More tools → TimeLock** (it may be on page 2).
2. Change the passcode first. The default is `1234`.
3. Set your limits under **Set Days, Hours & Limits**.
4. Turn on **Enable TimeLock**. It is off until you enable it.

## Menu

- **Enable TimeLock**: the main on/off switch. Turning it off requires the passcode.
- **Used Today**: minutes used today out of today's limit.
- **Set Days, Hours & Limits**: set a default limit, then tap a day to set its start time, end time and limit in minutes. Each part is optional. Changes require the passcode while the lock is on.
- **Set/Change Passcode**: numeric passcode (digits only). Changing it requires the current passcode while the lock is on.
- **Check For Update**: checks the latest GitHub release (needs Wi-Fi).
- **About**: version, repository and license.

## How it works

- **Limits:** each day can have its own limit in minutes. A day without one uses the default limit. A limit of 0 blocks that day.
- **Hours:** each day can have a start and end time. A day with none can be used at any hour. Overnight windows (for example 22:00 to 06:00) work and count toward the day they start.
- **What counts as usage:** only time spent with a book open and the screen awake. Time on the main screen, asleep, or with the screensaver showing is not counted.
- **Warning:** when 5 minutes remain, a message appears and stays on screen until tapped.
- **Locking:** when the limit is reached or you are outside the allowed hours, a full-screen lock covers KOReader, including the library. Tap **Unlock** and enter the passcode to lift the lock until midnight.
- **Reset:** used time resets to zero at midnight.

## Limitations

This is a simple deterrent, not a security system.

- It does not block exiting or restarting KOReader.
- KOReader's plugin manager can disable it.
- The passcode is stored in plain text in `settings/timelock.lua`.
- USB access, a forced reboot or changing the device clock can bypass it.
- An unlock is forgotten if KOReader restarts.

## Credits

Written by Walter Black, working with [Claude](https://claude.ai), Anthropic's AI model.

## License

[AGPL-3.0](LICENSE), the same license as KOReader.
