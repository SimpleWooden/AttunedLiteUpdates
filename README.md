# AttunedLiteUpdates

Public update channel for Attuned. Source stays in the private [AttunedLite](https://github.com/SimpleWooden/AttunedLite) repo.

The desktop app reads this repository with no GitHub login:

- `manifest.json` — versions, changelogs, installer URLs, and catalog cache version
- `setting-catalog/` — shipped Intune settings dictionary used by **Update Cached Values**
- GitHub Releases — `.exe` / `.msi` installers named in `manifest.json`

## Add an app version

1. Upload `Attuned_<version>_x64-setup.exe` as a GitHub Release asset (tag `v<version>`).
2. Add a `releases` entry in `manifest.json` with `changelog` and `downloadUrl`.
3. Set `latest` to that version if it should be offered as the current update.

## Refresh the settings catalog cache

Replace the files in `setting-catalog/`, then change `cache.version` (and `cache.updatedAt` / `cache.changelog`) in `manifest.json`. Attuned only downloads those files when `cache.version` differs from the last pull.
