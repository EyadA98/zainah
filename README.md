# Zainah Workspace — approved sapphire branding (v2)

This package implements the approved logo, favicon and revised light/dark palettes in the **Workspace** and **Grids** pages. It preserves the existing fonts (Marcellus and Plus Jakarta Sans) and app logic. Assets are in `assets/`.

## Updated

- Rounded-square generated **Z** icon shared by the sidebar, sign-in, splash and Grids header.
- Light and dark full-size logos: `assets/zainah-logo-light.png`, `assets/zainah-logo-dark.png`.
- Favicon ICO and PNGs (16/32/48), mobile touch icon (180), app icons (192/512), manifest.
- Brand tokens and key UI contrast states for both files: `assets/zainah-theme.css`, `assets/zainah-grids-theme.css`.
- Replaced legacy purple/peach theme colors in the styles and the built-in Grids chart presets. User-saved custom spreadsheet colors are not modified.

## Supabase connection (configured)

The root `index.html` now includes the **Zainah Workspace** project URL and its **browser-safe publishable key** supplied by the site owner. Do not replace these values with a private `sb_secret_` / `service_role` key. `grids/index.html` communicates with Workspace and does not require its own key.

The connection details are included in the static website by design. This only configures the client: Supabase Authentication, `hub` table, RLS policies and the private `attachments` Storage bucket must be configured independently, and cloud sync must still be tested after deployment. Gmail/Calendar integration additionally requires Google OAuth and may require a `google-token` Edge Function.

## Deploy to GitHub Pages (zainah.co)

1. Download and extract this ZIP. Upload **all its contents** to the **root** of the GitHub Pages repository, preserving `index.html`, `grids/`, `assets/`, `site.webmanifest` and `CNAME` file paths exactly. Do not upload the parent directory as a nested folder.
2. The included `CNAME` file preserves the `zainah.co` custom domain. If an existing `CNAME` file is present, it should already contain `zainah.co`.
3. Commit changes to the publishing branch (`main`). Wait for GitHub Pages to publish, then hard-refresh the site to update cached styles and favicons.
4. **Do not use the website for passwords or sign-in until `https://zainah.co` loads with a valid HTTPS certificate**. The GitHub Pages Enforce HTTPS checkbox may still be pending.
5. When HTTPS works, sign in, create a note, check a new row in Supabase `hub`, then sign in in a different browser to check syncing. Verify file uploads and Grids separately.

**Not an automatic deployment:** This ZIP does not change your GitHub repository or Supabase settings by itself.

## Preview

For local viewing without an authenticated Supabase connection, run a local HTTP server from the package root: `python -m http.server 8765`, then visit `http://localhost:8765`. Use a temporary guest mode to review the UI; guest changes stay on the device.

## Branding palette

| UI token | Light | Dark |
|---|---|---|
| Background | `#FBFCFF` | `#0A1020` |
| Sidebar | `#F2F5FC` | `#0E1729` |
| Card | `#FFFFFF` | `#131D31` |
| Raised | `#F2F6FF` | `#1B2943` |
| Border | `#E3E9F3` | `#293955` |
| Text | `#19253F` | `#F5F7FF` |
| Secondary text | `#64748B` | `#A7B6D0` |
| Action | `#4657E8` | `#788BFF` |
| Selected | `#EDF0FF` | `#24365C` |

Brand originals `#5465FF`, `#788BFF`, `#9BB1FF`, `#BFD7FF`, `#E2FDFF` remain unchanged.


PASTEL SKIES UPDATE: Light and dark UI, widgets, prayer widget, patterns, three time-of-day hero treatments, Z logos and favicon recolored. Existing Supabase project URL and publishable key preserved. Upload all files including assets and grids.
