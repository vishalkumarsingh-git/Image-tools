# Programming Blitz. — Image Studio

A responsive image workspace with local editing, metadata controls and optional cloud accounts.

## Implemented in the current build

- Upload images with the file picker or drag and drop
- Preview image dimensions
- Brightness, contrast, saturation and blur adjustments
- Rotate and flip
- Resize with optional aspect-ratio lock
- Export as PNG, JPEG or WebP with quality control
- Metadata editor for JPEG export (EXIF): make, model, lens, capture date, creator, copyright and description
- Editable device presets for selected smartphones, mirrorless/DSLR cameras, action cameras and smart glasses
- Supabase email/password sign-up and sign-in UI
- Per-user profile and edit-history database schema with Row Level Security

## Supabase setup (free tier)

1. Create a Supabase project at https://supabase.com.
2. Open **SQL Editor** in the Supabase dashboard and run `supabase/schema.sql`.
3. In **Project Settings → API**, copy the Project URL and the anon/public key.
4. Put those two public values into `config.js`.
5. Open **Authentication → URL Configuration** and add your deployed website URL to the allowed redirect URLs. Configure email confirmation as desired.
6. Reload the website and create an account.

The browser client must use only the Supabase anon/public key. Never put a Supabase service-role key in `config.js`, HTML, JavaScript or Git history.

Supabase currently lists a $0 Free plan with a 500 MB database, 1 GB file storage and 50,000 monthly active users. Free projects may pause after one week of inactivity, and the plan has usage limits. Check the live pricing page before production use.

## AI connection status

The AI connection panel matches the requested API-key/model layout. The key is not written to the database. The current UI does **not** send Gemini requests yet. Before enabling AI tools, add a server-side API endpoint and store the Gemini key in the server/deployment secret environment. Do not expose a Gemini key in browser code or commit it to GitHub.

## Metadata notes

Metadata presets are editable suggestions, not proof of the actual capture device. EXIF metadata is written on JPEG export; PNG and WebP exports use the normal image export path. No location metadata is added automatically. Do not use edited metadata to misrepresent the origin or ownership of an image.

The metadata editor uses Piexifjs for JPEG EXIF reading/writing. See its documentation: https://piexifjs.readthedocs.io/.

## Run locally

Open `index.html` through a local static web server. The app uses browser-side JavaScript and CDN-loaded libraries; a network connection is needed for those libraries and Supabase.

## Project

Created for **Programming Blitz.**

Repository: https://github.com/vishalkumarsingh-git/Image-tools
