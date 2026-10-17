# Zainah Workspace — Pastel Skies v4 (visual fixes)

This release corrects the visual issues reported from v3:
- Dark sign-in and dashboard use deeper rich-plum surfaces and clearer white text.
- Large sign-in circular overlay removed; hero ribbon's accidental full-width gray rectangle removed.
- Dashboard hero maintains morning/afternoon/evening three-color gradients with no oversized glowing blobs.
- Splash/loading screen now uses the new palette in both light and dark modes.
- Calendar month header's original rounded interlock SVG pattern restored (the v3 dot substitute was removed).
- Prayer widget rings, bars and dark card now use coordinated richer lavender/violet.
- Z logo alpha edges cleaned to remove unwanted colored fringe, and favicon/touch/app icons regenerated.
- Cache-busting `-v4` artwork filenames in Workspace, Grids, and webmanifest.
- Supabase URL / browser-safe publishable key and existing application logic preserved.

**Deployment:** Extract the ZIP and upload the contents inside the top-level folder to the GitHub Pages repository root. Preserve `CNAME` (`zainah.co`) and folder structure. Commit on `main`. Wait for the deployment, then hard refresh. Check the login screen, all three hero slots, prayer and calendar in both themes.

**Verification:** Static JavaScript syntax, CSS parsing, icon transparency and ZIP integrity were checked. Production authentication, sync, custom data, live browser graphics and layout require verification on the deployed site.

Existing Supabase credentials are publishable only; never replace with a secret key.
