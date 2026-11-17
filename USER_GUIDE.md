# TKA Mod Manager — User Guide

**For The Killing Antidote | Native Edition | v1.1.0 development builds**

TKA Mod Manager helps you organise, install and manage mods for **The Killing Antidote**, maintain your game directories and savegame backups, and browse Nexus Mods from within the application. Features may vary between development builds.

> **Before you begin:** Close the game before changing installed mods. Keep backups of important files and saves. Only download mods from sources you trust.

## Contents
1. [Getting started](#getting-started)
2. [Home dashboard](#home-dashboard)
3. [Browse Mods and Nexus downloads](#browse-mods-and-nexus-downloads)
4. [Duplicate downloads and replacement](#duplicate-downloads-and-replacement)
5. [Install Mods](#install-mods)
6. [Manage Mods](#manage-mods)
7. [Manage Folders](#manage-folders)
8. [Manage SaveGames](#manage-savegames)
9. [Game status and updates](#game-status-and-updates)
10. [Privacy and browser data](#privacy-and-browser-data)
11. [Troubleshooting](#troubleshooting)

## Getting started

1. Extract the downloaded manager release to a folder where you want to keep it.
2. Launch **TKA Mod Manager**.
3. Check the game installation path on **Home**. If it was not detected correctly, use **Setup Game Directory** to select it.
4. Keep the manager's own **Mods** folder alongside the manager executable. This is the library for downloaded mod archives, **not** the game's installed mod directory.
5. Close The Killing Antidote before installing, removing or replacing game mod files.

The manager separates **downloading an archive** from **installing its contents into the game**. A mod appearing in the manager's Mods folder does **not** mean it has been installed into the game.

## Home dashboard

The Home page provides quick access to:
- **Install Mods:** Choose mod files from your library and install them into the game.
- **Manage Mods:** Review and organise installed mods.
- **Manage Folders:** Configure game and mod/backup folders.
- **Manage SaveGames:** Work with saved-game backups and restores.
- **Setup Game Directory:** Select the game installation manually.
- **Create Issue Log:** Generate a troubleshooting report to help investigate problems.
- **Manage Updates:** Check for manager updates.
- **Official TKA Discord** and **TKA Steam Discussions:** Community links.
- **View on GitHub:** Project information and releases.
- **User Guide & Documentation:** Instructions for using the manager (this page).

The Home information panel also shows the detected game directory and whether the game is running.

## Browse Mods and Nexus downloads

**Browse Mods** opens the Nexus Mods website inside the manager using **Microsoft Edge WebView2**. You can navigate the site and sign in to Nexus through its own website.

To download a mod:
1. Open **Browse Mods**.
2. Find a mod for The Killing Antidote and open its **Files** tab.
3. Start a supported manual download.
4. The manager receives the download in a temporary location and displays a **Review Nexus download** dialog.
5. Review the archive name, detected PAK files and any potential matches.
6. Choose what should happen to the downloaded archive.

When approved, the archive is moved into the **Mods** folder next to the manager. It is **not automatically installed into the game**.

The embedded browser has **Back**, **Forward**, **Refresh** and **Nexus Home** controls. Nexus login and website services are handled by Nexus Mods, not by a separate TKA Mod Manager account.

## Duplicate downloads and replacement

Mod authors frequently upload new ZIP files with names containing version numbers, timestamps or Nexus-generated suffixes. The internal `.pak` filename can remain unchanged across mod updates because the game expects specific asset paths.

The download review therefore looks at **both the archive filename and PAK filenames inside the archive** to identify possible existing versions. This is a *potential-match check*, not a cryptographic guarantee that two archives contain identical mods.

When a matching archive already exists, the intended choices are:
- **Replace existing:** Remove the matching older archive(s) from the manager's Mods library and retain the new download as the single library copy.
- **Keep Both:** Preserve the existing archive(s) and add the new download under a distinct filename.
- **No — Discard Download:** Reject the new download without changing existing library archives.

**Important:** Replacing an archive in the manager's Mods library does **not** automatically replace the mod already installed into the game. Use **Install Mods** separately when you want to install the new version.

Read the list of potential matches before confirming replacement. If the manager cannot reliably identify the intended mod, choose not to replace it and inspect the archives manually.

## Install Mods

Open **Install Mods** to view available mods from the manager's library. The page should refresh its archive list when you enter it.

The installer reads supported mod contents, including PAK files, rather than relying only on the downloaded ZIP filename. Select the intended mod and follow the on-screen installation controls. Installing a mod is a separate operation from downloading it.

If you have kept several versions of a mod, inspect them carefully before installation. Two archives may contain a PAK with the same filename; installing both may cause one version to overwrite or conflict with the other.

## Manage Mods

Use **Manage Mods** to inspect and organise installed mods, including the available enable/disable and management controls. Review the selected mod and its status before changing it. Close the game first.

## Manage Folders

Use **Manage Folders** to review or configure paths used by the manager. In particular, distinguish:
- **Manager Mods library:** Downloaded ZIP archives kept beside the manager executable.
- **Game installation/mod location:** The files used by The Killing Antidote.
- **Backup locations:** Folders used to preserve copies of saves or other managed files.

Do not manually delete folders unless you are certain what they contain.

## Manage SaveGames

Use **Manage SaveGames** to back up, restore and organise game saves. Before restoring a backup, make sure you have selected the correct save and consider preserving a copy of the current one. Close the game during save-file changes to avoid conflicts.

## Game status and updates

The **Game Running** indicator reports the manager's detected game state. A neutral state means the game is not detected as running; transitional status may appear while it starts; green indicates it is running.

Use **Manage Updates** on Home to check for newer manager versions. Update availability and supported installation steps depend on the build. Avoid overwriting your personal mod library or backups when updating.

## Privacy and browser data

### What the embedded browser stores

Browse Mods uses Microsoft Edge **WebView2**. Like a normal web browser, it can save sign-in cookies, session information, cached resources and website preferences **locally on your Windows PC**. This may keep you signed in across manager launches or updates.

Nexus Mods handles its own authentication. The manager does not require you to enter a Nexus password into a separate manager login form. However, visiting Nexus still connects to Nexus and services used by its website: **local browser storage does not mean website activity stays offline**.

### Find and remove the saved browser profile

Open **Privacy** from the manager's sidebar, then select **Open Browser Data Folder**. The Privacy page displays the actual profile location on your computer. In the development build shown here, the profile is named **TKA-Nexus-Profile** under the Windows temporary-data location.

To clear locally saved browser data:
1. Open **Privacy** and use **Open Browser Data Folder** to locate the profile.
2. **Completely close TKA Mod Manager.**
3. Delete the **TKA-Nexus-Profile** folder (not your manager's Mods folder).
4. Reopen the manager. WebView2 will create a fresh profile and you may need to sign in again.

**Signing out of Nexus alone does not necessarily remove cached browser files.** Deleting the local profile removes local session/cache data, not account information already held by Nexus or other websites. Never delete the profile while the manager is running.

### Your control and online safety

You can inspect and remove the local browser profile yourself. Downloaded mod archives and installed game mods are separate from that browser profile and should remain unaffected by clearing it.

As with Chrome or any other browser, exercise caution when signing in, downloading files or visiting external links. A locally stored browser session is not immune to malware or other software with access to your Windows account.

## Troubleshooting

### A download does not appear in Install Mods
Check that you approved the download review and that the archive is in the manager's **Mods** folder. Reopen **Install Mods** to refresh the list. Remember that a rejected or still-pending download is not part of the library.

### I downloaded the same mod multiple times
Check the **Review Nexus download** dialog. Use **Replace existing** to keep only the new library copy, **Keep Both** to preserve alternatives, or **Discard** to reject the new file. If duplicates remain from an older build, inspect the manager's Mods folder before deleting anything.

### Nexus keeps me signed in
This is normally caused by WebView2's locally saved browser profile. See [Privacy and browser data](#privacy-and-browser-data) for instructions to locate and clear it.

### The game directory is incorrect
Open **Home → Setup Game Directory** and select the correct The Killing Antidote installation.

### A mod does not work
Confirm that the mod is compatible with your game version, that you installed it (rather than merely downloaded its archive), and that conflicting versions are not installed together. Check the mod author's own instructions.

### I need help reporting a problem
Use **Create Issue Log** from Home and share the relevant details with the project's support channel. Review logs before sharing them in public, since paths and system details may be included.

---

**Project:** [TKA Mod Manager on GitHub](https://github.com/AkimboDK1990/TKA_Mod_Manager_Releases)

**Game:** The Killing Antidote

**Documentation note:** This guide describes the current native manager workflow and the Nexus browser experiment. Some labels and behaviour may change between development builds.
