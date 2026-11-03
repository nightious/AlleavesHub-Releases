# AlleavesHub releases

Release binaries for **AlleavesHub**, the app that sets up Alleaves POS terminals and keeps the
Alleaves Terminal app running. This repo holds release files only. The source code is private, and
issues and pull requests here are not monitored.

> **Status:** no releases yet.

## Download

Staff download AlleavesHub from the button on the Alleaves website. That button points at the
latest stable build:

```
https://github.com/nightious/AlleavesHub-Releases/releases/latest/download/AlleavesHub.exe
```

### First run: "Windows protected your PC"

AlleavesHub is not code-signed yet, so Windows warns the first time it runs:

1. Click **More info**.
2. Check that the app name is `AlleavesHub.exe`, then click **Run anyway**.
3. Click **Yes** on the "Do you want to allow this app to make changes" prompt.

After that the app installs itself and updates itself. You won't see this warning again on that
computer.

If Windows says **Smart App Control blocked** the app, it can't run on that PC yet. Contact Alleaves
support; don't turn off Smart App Control yourself.

## Updates

Installed copies check this repo for a new version at startup and once a day. Before installing,
an update must:

- carry a release manifest signed with the AlleavesHub release key (Ed25519; the public key is built
  into the app);
- match the size and SHA-256 listed in that manifest for every file.

An update that fails either check is discarded. A new version that doesn't start up healthy is
rolled back to the previous one automatically. Releases go to a share of terminals first, then to
all of them.

## What each release contains

| File | Purpose |
|---|---|
| `AlleavesHub.exe` | Installer that staff download (small, rarely changes) |
| `*-win-x64.zip` | The app itself, fetched by the installer and by updates |
| `manifest-<channel>.json` | Version, rollout share, and the size and SHA-256 of each file (`stable` is the default channel) |
| `manifest-<channel>.json.sig` | Ed25519 signature over the manifest |
