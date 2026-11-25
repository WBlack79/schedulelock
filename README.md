# ScheduleLock

A KOReader plugin that restricts device usage based on daily quotas and weekly schedule windows. It can also require a PIN to exit KOReader, change plugins, or set the time and date. Useful as a simple way to manage when and how long an e-reader is used, for yourself, a child, or a shared device.

## Why it exists

ScheduleLock isn't meant to discourage reading. It helps you choose when the e-reader gets used.

I built it for my child, who loves to read so much that homework and studying can get pushed aside. School also restricts electronics during the day, so reading time at home needs to fit around everything else. Setting allowed hours and a daily limit keeps study time free of distractions and still leaves plenty of time to read at the right moments, like after homework or before bed.

## Tested on

Developed and tested on a **Kindle Paperwhite 12th Gen** running **KOReader 2026.07.02**.

Reports from other devices are welcome.

## Install or update

1. Download `schedulelock.koplugin.zip` from the Releases page and unzip it. You should have a folder named `schedulelock.koplugin`.
2. Connect your e-reader to a computer with USB.
3. Copy the whole `schedulelock.koplugin` folder into KOReader's `plugins` folder. When updating, replace the existing folder.
4. Eject the device and restart KOReader.

Your settings are kept when you update. To uninstall, delete the plugin folder (and `settings/schedulelock.lua` to remove your saved settings).

### Updating from inside KOReader

From version 0.7 on, you can update without a computer: open Check For Update. If a newer release exists, you'll see its release notes and a Download & Install button. The new version is downloaded, checked, and swapped in with a backup of the old one, and then you can restart KOReader to start using it. If any lock is on, the passcode is asked for before installing. Version 0.7 itself has to be installed by hand (USB) once.

Requirements: Wi-Fi, an unzip command on the device, and a GitHub release with schedulelock.koplugin.zip attached.

## Quick start

1. Open **Top menu → Tools icon → ScheduleLock** (it may be on page 2).
2. Change the passcode first under **Set/Change Passcode**. The default is `1234`.
3. Set your limits under **Set Days, Hours & Limits**.
4. Turn on **Enable ScheduleLock** to start the limits.
5. Under **Protections**, turn on whichever PIN locks you want.

Everything is off until you switch it on.

<img width="318" height="424" alt="FileManager_2026-11-21_175030" src="https://github.com/user-attachments/assets/7b18b621-749b-4640-bdf9-a17ef6738469" />

## Menu

- **Enable ScheduleLock**: switches the schedule limits on or off: time counting, the 5-minute warning and the lock screen. It does not affect the Protections. Turning it off requires the passcode.
- **Used Today**: minutes used today out of today's limit.
- **Set Days, Hours & Limits**: tap a day to set its Start/End Time, Warning Before Day Ends, Daily Time Limit and Warning Before Time Limit. Every day starts at 09:00-21:00 with a 180-minute limit. A day's Copy To... button copies its settings to the weekdays, the weekend or all days (after a confirmation).
- **Protections**: three separate switches, each independent of the schedule limits:
  - **Lock Exit**: exiting KOReader needs the passcode.
  - **Lock Plugin Management**: enabling or disabling any plugin needs the passcode.
  - **Lock Time & Date**: **Set time** and **Set date** need the passcode. (KOReader only shows these on devices where it can set the clock.)
- **Set/Change Passcode**: numeric passcode (digits only), shared by everything above.
- **Check For Update**:checks the latest GitHub release, shows its release notes, and can download and install it (needs Wi-Fi).
- **About**: version, repository and license.

While any lock is on, turning something off or changing a setting (limits, schedule, passcode, Protections) needs the passcode. Turning something on never does.

<img width="318" height="424" alt="FileManager_2026-11-21_175035" src="https://github.com/user-attachments/assets/5dedf3da-b324-4900-9e3e-080175ea19d7" />      <img width="318" height="424" alt="FileManager_2026-11-21_175313" src="https://github.com/user-attachments/assets/694854b6-6060-45fd-89b4-5337f1a11889" />


## How it works

- **Limits:** each day has its own Daily Time Limit in minutes (180 to start). A limit of 0 blocks that day.
- **Hours:** every day allows 9:00 AM to 9:00 PM (09:00-21:00) by default. Each day can have its own start and end time, or **Any Hours (Clear Start/End)** for no restriction. Start/End Time opens two time pickers in a row, start first. Overnight windows (for example 22:00 to 06:00) work and count toward the day they start.
- **What counts as usage:** only time spent with a book open and the screen awake. Time on the main screen, asleep, or with the screensaver showing is not counted.
- **Warnings:** a popup appears 5 minutes before the Daily Time Limit runs out and 5 minutes before the allowed hours end, and stays on screen until tapped. Under **Warning Before Time Limit** and **Warning Before Day Ends** you can choose an earlier warning (10 to 60 minutes) for each day. When one is chosen, you get that warning and another with 1 minute left, instead of the 5-minute one. A limit or window that isn't longer than a warning time gets no warning for it.
- **Locking:** when the limit is reached or you are outside the allowed hours, a full-screen lock covers KOReader, including the library. The lock screen shows when the device can be used again. Tap **Unlock**, enter the passcode, then choose **Add 15 Minutes**, **Add 30 Minutes** or **Unlock For Today**. Added minutes ignore the limit and the allowed hours, count down only while you read, and end at midnight. None of these unlock the Protections.
- **Wrong passcodes:** three wrong passcodes in a row lock passcode entry for 5 minutes.
- **Reset:** used time resets to zero at midnight.
- **Restart:** restarting KOReader is not locked.

<img width="318" height="424" alt="FileManager_2026-11-25_143915" src="https://github.com/user-attachments/assets/5b92206e-3e84-4937-a4f7-010258481534" />

## Limitations

This is a simple deterrent, not a security system.
 
- The Protections cover KOReader's menu entries. A gesture or shortcut mapped to the Exit action is not covered.
- The plugin-management lock relies on a KOReader internal. If your version differs, the plugin logs a warning and plugin toggles stay unlocked.
- The passcode is stored in plain text in `settings/schedulelock.lua`.
- USB access or a forced reboot can bypass it.
- Changing the clock by any route other than the locked Set time and Set date entries can affect the schedule.
- An unlock is forgotten if KOReader restarts.
- In-app updating trusts whatever is attached to your latest GitHub release. It checks that the download is a ScheduleLock package but does not verify a signature or checksum.

## Credits

Written by Walter Black, working with [Claude](https://claude.ai).

## License

[AGPL-3.0](LICENSE), the same license as KOReader.
