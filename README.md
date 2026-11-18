# TimeLock

A KOReader plugin that restricts device usage based on daily quotas and weekly schedule windows.

## Tested on

Developed and tested on a **Kindle Paperwhite 12th Gen** running **KOReader 2026.07.02**.

Reports from other devices are welcome.

## Install or update

1. Download `timelock.koplugin.zip` from the Releases page and unzip it. You should have a folder named `timelock.koplugin`.
2. Connect your e-reader to a computer with USB.
3. Copy into or replace the `timelock.koplugin` folder in KOReader's `plugins` folder.
4. Eject the device and restart KOReader.

To uninstall, delete the folder.

### Settings

Top menu → Tools icon → More tools → Time Lock (might be on page 2):

- **Enable Time Lock**: the main on/off switch that is passcode protected
- **Used Today**: Let's the user know usage minutes of the day. 
- **Set Days, Hours & Limits**: You can set hours and usage time per day.
- **Set/Change Passcode**: set or change your passcode here. Restart KOReader after setting passcode. 
- **Check For Update**: Checks the GitHub repository for updates.
- **About**: Additional information.

## Credits

Written by Walter Black, working with [Claude](https://claude.com/claude-code), Anthropic's AI model.

## License

[AGPL-3.0](LICENSE), the same license as KOReader.
