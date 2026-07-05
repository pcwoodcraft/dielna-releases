# Dielňa — distribúcia APK

Verejné repo pre `version.json` (GitHub Pages) a APK cez GitHub Releases.

- **Pages:** https://pcwoodcraft.github.io/dielna-releases/version.json
- **Releases:** https://github.com/pcwoodcraft/dielna-releases/releases
- **APK:** len ako Release assets (nie v git histórii)

## Publish nového buildu

1. V `sledovanie-hodin`: `eas build --profile preview --platform android`
2. Skopíruj **build ID** (UUID) z EAS dashboardu
3. **Actions → Publish release → Run workflow**
   - `eas_build_id` — UUID z EAS
   - `version` — semver z `app.json` (napr. `1.4.3`)
   - `versionCode` — integer z `app.json` (napr. `8`)
4. Secret `EXPO_TOKEN` v repo settings (Expo access token s prístupom k projektu `dielna`)

Workflow stiahne APK cez Expo GraphQL API, spočíta MD5 + SHA-256, vytvorí Release a commitne `version.json`.

**Pravidlo:** `versionCode` v `version.json` vždy rastie — nikdy downgrade.

## Prvá verzia (1.4.3)

Tablety na staršej appke (1.4.2) nemajú checker — prvýkrát treba APK nainštalovať manuálne z Releases. Ďalšie verzie už cez modal v appke.
