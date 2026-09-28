# Adjustable Base Config

This repository stores the shared adjustable-base configuration used by the mobile app.

## How syncing works

- The app loads its locally cached list immediately.
- On every app launch, it checks `bases.json` for a newer `version`.
- If the remote version is newer, the app downloads and saves it locally.
- If internet is unavailable, the app keeps using the last successful local copy.
- The UI can show a small `Updated: <date/time>` line based on the last successful sync.

## bases.json format

```json
{
  "version": 1,
  "updatedAt": "2026-09-28T10:00:00Z",
  "bases": [
    {
      "id": "base_001",
      "friendlyName": "Front King Lifestyle Base",
      "manufacturer": "",
      "model": "",
      "showroomLocation": "",
      "bluetooth": {
        "advertisedName": "",
        "serviceUuids": [],
        "knownIdentifiers": []
      },
      "capabilities": {
        "head": true,
        "feet": true,
        "lumbar": false,
        "massage": false,
        "audio": false,
        "lighting": false,
        "flat": true,
        "zeroGravity": false,
        "memoryPresets": false
      },
      "protocolProfile": null,
      "notes": "",
      "enabled": true
    }
  ]
}
```

## Admin behavior

When the admin adds, edits, renames, or removes a base, the app should update `bases.json`, increment `version`, and update `updatedAt`.

Do not store passwords, GitHub tokens, private keys, or other secrets in this repository.
