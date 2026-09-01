# local research data handling

This document describes the minimum safe workflow for the prototype. It does not replace an institutional data-management plan or research-ethics approval.

## data categories

The application may create or receive:

- WhatsApp numbers and respondent profile fields;
- voice recordings and derived transcripts;
- extracted task data, reminders, feedback, and review metrics;
- SQLite databases, CSV exports, ZIP backups, logs, and temporary files.

Treat all categories as sensitive. Use synthetic data unless an authorized study specifically requires otherwise.

## development

1. Copy `.env.example` to `.env` and use local-only credentials.
2. Keep the admin host bound to `127.0.0.1` during development.
3. Run `npm test` before starting the bot.
4. Never add `data/`, session directories, exports, audio, transcripts, or backups with `git add`.
5. If sensitive data is accidentally created in the working tree, remove it and check `git status` and `git ls-files` before pushing.

## access and exports

- Protect the dashboard with a strong password and a random session secret of at least 32 characters.
- Use HTTPS and network restrictions before any authorized remote access.
- Export only the minimum necessary fields.
- Treat every CSV or ZIP export as a controlled copy of research data.
- Store backups encrypted, limit access, and test restoration without exposing the contents.

## retention and deletion

Before collecting real data, document an approved retention period and the responsible data custodian. At the end of that period, delete the database, audio, transcripts, exports, backups, temporary files, and relevant logs from every authorized copy. Record the deletion without recording the deleted personal data.

## external processing

Voice transcription or AI parsing can send content to an external service depending on configuration. Do not send identifiable data unless the service, legal basis, participant notice, retention settings, and institutional approval have been reviewed. Prefer local processing for sensitive testing.
