# Dielňa — distribúcia APK

Verejné repo pre `version.json` (GitHub Pages) a APK cez GitHub Releases.

- **Pages:** https://pcwoodcraft.github.io/dielna-releases/version.json
- **APK:** len ako Release assets (nie v git histórii)

## Publish nového buildu

1. V `sledovanie-hodin`: `eas build --profile preview --platform android`
2. Skopíruj **build ID** z EAS dashboardu
3. V tomto repo: **Actions → Publish release → Run workflow**
   - `eas_build_id` — UUID z EAS
   - `version` — semver z `app.json` (napr. `1.4.3`)
   - `versionCode` — integer z `app.json` (napr. `8`)
4. Secret `EXPO_TOKEN` musí byť nastavený v repo settings

Workflow stiahne APK z EAS, spočíta MD5 + SHA-256, vytvorí Release a aktualizuje `version.json`.

## Prvé nasadenie

1. Vytvor verejné repo `pcwoodcraft/dielna-releases` na GitHube
2. Pushni obsah tohto priečinka na `main`
3. Settings → Pages → Source: **Deploy from branch `main`**, root
4. Pridaj secret `EXPO_TOKEN`
