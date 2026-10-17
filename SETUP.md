# Zainah Alfayez Workspace — deployment guide

This is a **new, isolated copy** of Workspace + Grids, branded with Electric Sapphire `#5465FF`, Cornflower Blue `#788BFF`, Baby Blue Ice `#9BB1FF`, Icy Blue `#BFD7FF`, and Light Cyan `#E2FDFF`. The existing Plus Jakarta Sans and Marcellus fonts remain.

## Contents

- `index.html` — Workspace, including Tasks, Notes, Calendar, Gmail integration and the Grids iframe.
- `grids/index.html` — Grids; **keep this path**, because Workspace loads `grids/index.html`.
- The standalone Apps page/nav and its dashboard widget have been removed. The original app-launcher logic remains unused internally to minimize collateral changes.

## 1. Create a new Supabase project (required for private cloud persistence)

1. In Supabase create a **new project** for Zainah, not the former Workspace project.
2. Configure authentication providers and an allowed redirect URL for your live site under **Authentication > URL Configuration**. Add your custom site URL and any development/preview URL you actually use.
3. Set up the **database tables, storage buckets, and row-level-security policies** expected by Workspace. **This bundle does not include a database schema or migrations**. Retrieve the original application's schema/migrations from its maintainer, review them, and deploy to the new project. Do not copy user records. Enforce `auth.uid()`-scoped access on all user data and storage objects, including Grids data.
4. From your *new* Supabase project take **Project URL** and **publishable key (or legacy anon key)**. In `index.html`, replace the empty strings in `SUPABASE_URL` and `SUPABASE_ANON_KEY`. Do not paste a `service_role`/secret key in browser HTML. Browser-visible publishable/anon keys are not secrets; data protection comes from RLS.
5. Test sign-in, sign-out, fresh-user empty state, cloud save/reload, cross-device sync, and file attachments before admitting users.

> The delivered HTML deliberately has **empty Supabase credentials** to prevent accidental connection to the previous user's project. Until configured, cloud authentication/synchronization is unavailable; do not assume the local/guest mode is a production login.

## 2. Publish to GitHub

1. Create a fresh GitHub repository, for example `zainah-workspace`.
2. Commit `index.html`, the entire `grids/` directory, and this guide. Avoid committing any export of the former user's data.
3. In **Settings > Pages**, set **Source: Deploy from branch**, choose `main` and `/ (root)`, and save. Wait for the generated `https://YOUR-USERNAME.github.io/REPOSITORY/` URL to become available.
4. Check Workspace and Grids loading together. Keep the directory layout intact, and test HTML imports/exports and both visual themes.

## 3. Use a custom domain

1. In GitHub **Settings > Pages > Custom domain**, enter the domain or subdomain chosen for Zainah.
2. Add the DNS records GitHub prescribes to the domain registrar (typically a `CNAME` for `www` or another subdomain pointing to `YOUR-USERNAME.github.io`; apex domains use GitHub's documented IP records). Do not guess records for an existing live domain.
3. Once DNS is verified and the certificate is issued, enable **Enforce HTTPS**.
4. In Supabase Authentication URL Configuration, update the **Site URL** and allowed redirects to the final HTTPS domain.
5. Update any canonical domain shown in the digest email template (`your-domain.example` fallback and anchor label in `index.html`) to the real domain. The public domain cannot be filled in until you provide it.

## 4. Connect Gmail and Google Calendar

1. Create or select a **Google Cloud project** for this new site and configure **OAuth consent** (app name, support email, permitted scopes, test users, and publishing/verification status as appropriate).
2. Enable **Google Calendar API** and **Gmail API** in Google Cloud.
3. Create a **Web application OAuth client**, with **Authorized JavaScript origins** matching your deployed HTTPS domain (and GitHub Pages preview origin, if testing there). If your Google OAuth configuration uses redirect flows, register the matching redirect URIs too.
4. Open Workspace **Profile & settings** and paste the Google OAuth **Client ID** into the field labeled `Google Client ID — Calendar & Gmail`.
5. Connect the new user's Google account, grant the requested permissions, and verify both the Calendar and Gmail widgets. Google may require OAuth verification for some requested scopes when used beyond test users.

## 5. Acceptance checks

- Fresh browser: profile defaults to `Zainah Alfayez`, no previous data or app links appear.
- Apps is absent from desktop navigation, mobile navigation, dashboard and page routing.
- Grids opens within Workspace and can save, reload, edit, import/export, and use its dashboard tools.
- Light/dark themes use the new blue family; selected spreadsheet swatches and semantic alert colors still remain customizable.
- Google Calendar and Gmail can connect *only* to the intended account; sign-out and reconnect work.
- Database RLS denies access to a different test user's records; browser console shows no failed storage requests.

## Security and deployment notes

GitHub Pages is static hosting; it doesn't provide per-user authentication or a private backend itself. Supabase must enforce data isolation server-side. **Do not rely on hiding HTML elements to secure data.** This package is a branded front-end, not a complete independently validated production deployment. The original code includes multiple legacy brand-specific selectors/colors; the override theme aligns the common surfaces, but a visual pass is still recommended for specialist chart and editor states.
