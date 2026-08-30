# How to

## Goal

How-to section is good to achieve a specific result flowing some step by step.

## Table of contents

- [how to delete specific folder in the current workspace](#how-to-delete-specific-folder-in-the-current-workspace)
- [How to define dependencies by major version (semver)](#how-to-define-dependencies-by-major-version-semver)
- [How to update all Angular packages to the same major](#how-to-update-all-angular-packages-to-the-same-major)
- [How to clean the worktree based on the current commit](#how-to-clean-the-worktree-based-on-the-current-commit)
- [How to find text in files](#how-to-find-text-in-files)

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
\;: Terminates the -exec command string.
