# How to

## Goal

How-to section is good to achieve a specific result flowing some step by step.

## Table of contents

- [how to delete specific folder in the current workspace](#how-to-delete-specific-folder-in-the-current-workspace)
- [How to define dependencies by major version (semver)](#how-to-define-dependencies-by-major-version-semver)
- [How to update all Angular packages to the same major](#how-to-update-all-angular-packages-to-the-same-major)

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