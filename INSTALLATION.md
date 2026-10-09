# Installation and updates

## Requirements

Use Windows 11 x64 with Microsoft Edge WebView2 Evergreen Runtime. Install missing WebView2 from [Microsoft's official download page](https://developer.microsoft.com/microsoft-edge/webview2/) using the current-user Evergreen installer, then rerun Scriber Setup. Setup stops before replacing Scriber when the runtime is missing. Internet access is needed for AI requests, initial downloads, and optional sync; saved vocabulary and review remain available offline.

Run `Scriber-Setup-1.0.0.exe`. Installation is per-user and does not require elevation. The default directory is `%LOCALAPPDATA%\Programs\Scriber`. Data, encrypted credentials, and WebView2 state are stored in `%LOCALAPPDATA%\Scriber`.

Download Setup and ZIP only from the official Releases page. For ZIP installation, compare its SHA-256 with the accompanying `.sha256` file before extracting it.

## Updates and portable use

Settings → General → Updates shows the installed version and **Stable** channel. Checks use the public feed without a GitHub account. Automatic checks run about every eight hours with startup jitter. Downloading and Restart & install are explicit actions. Completed packages can be verified and installed offline. Failed binary startup restores the previous application directory.

The ZIP is a portable/manual fallback. Extract the complete archive, including `Web`, into a user-writable directory. A portable/custom-directory copy opens the public release page for manual installation. It uses the same Stable data profile; stop the other Stable copy first. Do not mix files from different versions. Prefer Setup for uninstall registration and Start menu shortcuts.

The included PowerShell installation scripts must be run from a complete release containing `release.json`; they select the installed build's identity and never target the other channel's process or directories.

## Existing private 5.5.0 installations

The old updater cannot offer 1.0.0 because it correctly considers it older and knows only its private feed. Close the old app and install the rebuilt public Stable package once manually. This is the only permitted version reset. Later updater operations continue rejecting equal or older versions. Setup and the manual install script also reject downgrades after the one-time 5.x → 1.0.0 reset; reinstalling the same version for repair remains supported.

Before overwriting files, Setup runs the candidate's migration preparation. SQLite's online backup includes committed WAL edits. Settings, vocabulary/review data, encrypted AI/cloud credentials, and legacy updater recovery information are preserved in `%LOCALAPPDATA%\Scriber\recovery\stable-1.0-<id>`. Old 5.x binaries are retained under `%LOCALAPPDATA%\Programs\.Scriber-legacy-<id>` when Setup prepares the migration. Legacy cached offers, packages, and timestamps are cleared; the old Windows recovery command is backed up and retired before it can resume a private 5.x update; only the obsolete GitHub updater credential is removed after its encrypted backup is saved.

The cloud environment is a separate migration. The previous development URL and account session remain recoverable. Stable blocks sync to an environment other than its verified production deployment; it does not silently adopt an empty production library. Confirm the intended account/library and back up any other device before changing its cloud settings. Dev starts with its own local data and never connects to production by default.

If migration preparation fails, Setup stops before replacing the old application. If later startup fails, close Scriber and restore the complete old binary directory. To restore data, preserve the failed profile first, then restore the backed-up `scriber.db`, settings, and credential files with all Scriber processes closed. Remove the current database's `-wal` and `-shm` sidecars before restoring its SQLite snapshot. Restore `stable-release.json` only if it matches the profile being restored. Cloud writes require a separate recovery decision; binary rollback does not undo them.

## Uninstallation

Use Windows Settings → Apps → Scriber or its Start menu uninstaller. Local data remains so reinstalling can recover it. To erase local data deliberately, close Scriber and delete `%LOCALAPPDATA%\Scriber`. Deleting local files does not remove your OpenAI account or cloud library. Internal Dev installations use separate uninstall registration and data paths.
