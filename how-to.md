# How to

## Goal

How-to section is good to achieve a specific result flowing some step by step.

## Table of contents

- [how to delete specific folder in the current workspace](#how-to-delete-specific-folder-in-the-current-workspace)
- [How to define dependencies by major version (semver)](#how-to-define-dependencies-by-major-version-semver)
- [How to update all Angular packages to the same major](#how-to-update-all-angular-packages-to-the-same-major)
- [How to clean the worktree based on the current commit](#how-to-clean-the-worktree-based-on-the-current-commit)
- [How to find text in files](#how-to-find-text-in-files)
- [How to define a notification to remind the MacBook is charging](#how-to-define-a-notification-to-remind-the-macbook-is-charging)

### how to delete specific folder in the current workspace

```bash
find . -type d -name dist -prune -exec rm -rf {} +
```

### How to define dependencies by major version (semver)

#### **1. Use the caret (`^`) to lock only the *major* version**

This is the default and recommended approach.

```json
"dependencies": {
  "@angular/core": "^21.0.0"
}
```

✔ Allows updates like:

* `21.0.1`
* `21.1.0`
* `21.9.4`

✘ Will NOT allow installing Angular `22.x.x`.

This keeps your project **within major 21**.

---

#### **2. Use the tilde (`~`) to lock *major + minor*, allowing only patch updates**

```json
"dependencies": {
  "@angular/core": "~21.0.0"
}
```

✔ Updates allowed:

* `21.0.1`, `21.0.2`

✘ Will NOT install `21.1.0`
✘ Will NOT install `22.0.0`

---

#### **3. Lock *exact* version**

```json
"dependencies": {
  "@angular/core": "21.0.4"
}
```

✔ No automatic updates
✔ Good for guaranteed stability
✘ Harder to maintain long-term

---

#### **4. Allow *any* version of a major**

Use a wildcard:

```json
"dependencies": {
  "@angular/core": "21.x"
}
```

This means:

✔ Accept any `21.*.*`
✘ Rejects 22+

### How to update all Angular packages to the same major

Run:

```bash
ng update @angular/core@21 @angular/cli@21
```

Or manually:

```bash
npm install @angular/common@21 @angular/core@21 @angular/compiler@21 @angular/platform-browser@21 @angular/platform-browser-dynamic@21
```

### How to clean the worktree based on the current commit

Show for you, what are the files that will be delete it.
```bash
git clean -fdn
```

In fact, the comand to delete all files that are not tracking.
```bash
git clean -fdn
```

### How to find text in files

## Why

Sometimes, you need to verify specific content, and you do not know how to find — e.g. a term or word — The command below
helps you find where you can check.

## Syntax

```sh
find /path/to/search -type f -exec grep -H "your_search_string" {} \;
```

## Breakdown of the Syntax

- /path/to/search: The starting directory (use . for the current directory).
- -type f: Restricts the search strictly to regular files, skipping directories and system files.
- -exec: Tells find to run an external command on every file it encounters.grep: The command used to search text inside the files.
- -H: Forces grep to print the filename alongside the matching line.
- {}: A placeholder that find dynamically replaces with the path of each file found.
- \;: Terminates the -exec command string.

### How to define a notification to remind the MacBook is charging

#### 1. Create the script

Create a file named `battery-check.sh`:

```bash
#!/bin/bash

BATTERY_INFO=$(pmset -g batt)

PERCENT=$(echo "$BATTERY_INFO" | grep -o '[0-9]\+%' | tr -d '%')

# Check if Mac is charging
if echo "$BATTERY_INFO" | grep -q "AC Power"; then
    if [ "$PERCENT" -ge 80 ]; then
        osascript -e 'display notification "Battery reached 80%. Unplug the charger." with title "Battery Reminder" sound name "Glass"'
    fi
fi
```

Save it, for example, as:

```text
~/Scripts/battery-check.sh
```

Make it executable:

```bash
chmod +x ~/Scripts/battery-check.sh
```

---

#### 2. Create a LaunchAgent

Create the folder if needed:

```bash
mkdir -p ~/Library/LaunchAgents
```

Create this file:

```text
~/Library/LaunchAgents/com.user.batterycheck.plist
```

Paste:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
"http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>

    <key>Label</key>
    <string>com.user.batterycheck</string>

    <key>ProgramArguments</key>
    <array>
        <string>/bin/bash</string>
        <string>/Users/YOUR_USERNAME/Scripts/battery-check.sh</string>
    </array>

    <key>StartInterval</key>
    <integer>60</integer>

    <key>RunAtLoad</key>
    <true/>

</dict>
</plist>
```

Replace `YOUR_USERNAME` with your macOS username.

---

#### 3. Validate the plist

Run:

```bash
plutil ~/Library/LaunchAgents/com.user.batterycheck.plist
```

If it's valid, you'll see:

```
... OK
```

If not, paste the output here.

#### 4. Use the correct command

For a user LaunchAgent, **don't use `sudo`**. Run:

```bash
launchctl bootout gui/$(id -u) ~/Library/LaunchAgents/com.user.batterycheck.plist 2>/dev/null
launchctl bootstrap gui/$(id -u) ~/Library/LaunchAgents/com.user.batterycheck.plist
```

or on some macOS versions:

```bash
launchctl load ~/Library/LaunchAgents/com.user.batterycheck.plist
```

#### 5. Check the logs

If it still fails:

```bash
log show --last 5m --predicate 'process == "launchd"' --style compact
```

This often tells you the exact reason.

---

#### Prevent repeated notifications

The script above will notify you every minute while the battery stays at or above 80%. Here's an improved version that only notifies **once** until you unplug the charger:

```bash
#!/bin/bash

STATE_FILE="/tmp/battery80_notified"

BATTERY_INFO=$(pmset -g batt)
PERCENT=$(echo "$BATTERY_INFO" | grep -o '[0-9]\+%' | tr -d '%')

if echo "$BATTERY_INFO" | grep -q "AC Power"; then
    if [ "$PERCENT" -ge 80 ]; then
        if [ ! -f "$STATE_FILE" ]; then
            osascript -e 'display notification "Battery reached 80%. Unplug the charger." with title "Battery Reminder" sound name "Glass"'
            touch "$STATE_FILE"
        fi
    fi
else
    rm -f "$STATE_FILE"
fi
```

This version sends a single notification at 80% or higher, then won't notify again until the charger is unplugged and plugged back in.
