# Shopify Theme: The Master Git & CLI Guide

This is your definitive reference for safe, professional Shopify development.

---

## 1. The Start of Every Session (Syncing)
Always run these commands before touching any code.

- **Check out Main**: `git checkout main`
- **Sync GitHub**: `git pull origin main`
- **Sync Shopify**: `shopify theme pull --live --nodelete`
  *(Only mandatory if you changed colors/fonts/content via the Shopify Admin UI since your last session.)*

---

## 2. Daily Development (Local Testing)
Never publish code without seeing it first.

1.  **Launch Local Preview**:
    ```bash
    shopify theme dev --store luma-labs-2.myshopify.com
    ```
2.  **View Changes**: Open the `127.0.0.1` link provided by the CLI.
3.  **Real-time Edits**: Save your code; the preview refreshes automatically.

---

## 3. Safe Staging (Testing New Designs)
Test complex changes without your live customers seeing them.

1.  **Create a Stage Branch**:
    ```bash
    git checkout -b feature/new-design
    git push origin feature/new-design
    ```
2.  **Connect a Draft Theme**:
    - Go to **Shopify Theme Library** → **Add Theme** → **Connect from GitHub**.
    - Link to your `feature/new-design` branch.
3.  **Review**: Use the "Preview" button on that draft theme to test your work.
4.  **Go Live**: Merge your branch into `main` and push.

---

## 4. Theme Updates (New Vendor Versions)
How to upgrade the theme without losing custom code.

1.  **Pull the Version**: `shopify theme pull --theme NEW_THEME_ID`
2.  **Commit the "Base"**: Commit the new files to a dedicated branch.
3.  **Re-Merge**: Merge your `main` branch (your custom code) into the new version branch.
4.  **Save Settings**: Ensure `config/settings_data.json` is preserved to keep your photos and fonts.

---

## 5. Session Close (Deploying)
Always back up your work to the cloud.

```bash
git add .
git commit -m "Briefly describe your changes"
git push origin main
```

> [!IMPORTANT]
> **The Golden Rule**: If you touch the Shopify Admin UI, you **must** sync your computer via `git pull` or `shopify theme pull` before you write code.
