# Oman AI Case Guardian — MarufEdge FINAL

This is a **fresh rebuild**, not a patch of the previous package.

## Primary working deployment
Use **PHP 8.2+ + MySQL/MariaDB + HTTPS** on cPanel/Apache or another PHP host.

1. Create a MySQL database and user.
2. Import `database/schema.sql`.
3. Copy `.env.example` values into your host environment, OR edit `config/config.php`.
4. Make `storage/uploads`, `storage/logs`, and `storage/backups` writable by PHP.
5. Open `/auth/setup.php` once.
6. The only approved signup/initial-owner emails are:
   - habiburmaruf@gmail.com
   - marufsage@gmail.com
   - lion.maruf@gmail.com
7. Create the owner with a 12+ character password.
8. **Delete or rename `auth/setup.php` immediately after setup.**
9. Open `/auth/login.php`.
10. Test `/health.php`.

## What is included
- Secure session login/logout
- Approved-email signup policy
- Password reset token flow that works without SMTP
- CSRF protection
- Password hashing
- Case registry
- Evidence upload + SHA-256 integrity hash
- Evidence status separation
- Legal source registry
- AI research endpoint with optional Gemini API
- AI-1 / AI-2 / AI-3 separation at UI level
- Alerts
- Audit trail
- Health check
- EN/BN/AR language-ready data model
- Firebase static authentication portal
- Netlify and Vercel static/serverless adapters

## Important hosting reality
The **PHP/MySQL application itself should not be uploaded to Firebase Hosting, Vercel, or Netlify as if those platforms were ordinary PHP servers**. Firebase Hosting is primarily static and pairs dynamic workloads with Cloud Functions/Cloud Run; Netlify uses serverless functions; this package therefore keeps the real PHP backend separate and includes adapter folders.

For the simplest free/low-cost deployment, use a PHP/MySQL host. For Firebase, use `firebase/public` as the static auth portal and then connect a proper API/backend separately.

## AI
No API key is embedded in this ZIP. Put `GUARDIAN_AI_API_KEY` in server environment variables or config. Without a key, the research screen still works in safe checklist mode and clearly states that AI is not configured.

## Legal safety
This system is a research/document-management assistant. It must not invent Oman law, convert an allegation into a fact, or present AI text as a court judgment. Verify primary official sources and obtain qualified legal advice before filing.

## Backup
Back up both the MySQL database and `storage/uploads/`. Evidence originals should be preserved separately from AI-generated summaries.
