# Zainah Workspace — Pastel Skies v5

This patch is based on the prior v4 package and changes actual HTML, CSS, and JavaScript.

## Fixes
- Time-aware dashboard hero: vivid but controlled sunrise, afternoon and evening color gradients. Gentle movement is disabled for reduced-motion preferences. No extra decorative blobs.
- Routine weekly schedule: selected day buttons have an explicit purple background in light and dark modes so all weekday labels remain legible.
- Notes: recolored the eight existing note choices to coordinated violet, lilac, blush, periwinkle and slate shades. Existing note color IDs and user data remain compatible. Updated note pins and shadows.
- Logo: removed icon wrapper outlines/glows and clipped its outer pixel fringe at render time in the signed-in sidebar, sign-in form, splash and Grids header. Kept the approved Z artwork and existing favicon files.

## Deployment
Extract this ZIP and upload all contents to your GitHub Pages repository ROOT (not a nested release folder). Preserve `CNAME`, `assets/`, and `grids/`. Commit to `main`. After GitHub Pages publishes, use a hard refresh or private window.

Your configured Supabase URL and publishable key were preserved from v4. Do not place a Supabase secret key into client-side HTML.

## Testing and limitations
Static syntax, CSS parse, package integrity, relevant CSS computed styles and standalone UI previews are validated during the build. Full live authentication and cloud sync must still be checked on the deployed site.
