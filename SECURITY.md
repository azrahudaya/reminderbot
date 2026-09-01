# security policy

## project boundary

This repository contains an academic prototype that can process personal data, voice recordings, transcripts, and WhatsApp identifiers. It is published for portfolio review and academic discussion. It is not approved for production or real-participant use.

Do not open a public issue containing credentials, personal data, voice recordings, transcripts, database files, or other sensitive information.

## reporting a vulnerability

Use GitHub's private vulnerability reporting form for this repository:

https://github.com/azrahudaya/penulisanilmiah/security/advisories/new

If private reporting is unavailable, contact the repository owner through the email address currently listed on the GitHub profile. Do not use a public issue for an undisclosed vulnerability. Include:

- a short description of the issue;
- the affected file, route, or dependency;
- safe reproduction steps using synthetic data only;
- the potential impact;
- a suggested mitigation, if known.

Allow reasonable time for triage before public disclosure. Do not test against systems, accounts, or data that you do not own or have explicit permission to assess.

## local data handling

Keep `.env`, WhatsApp session directories, SQLite databases, audio, transcripts, exports, and backups outside Git. Use synthetic fixtures for development. Before any authorized research deployment, establish ethics approval, informed consent, access control, retention and deletion rules, encrypted backups, and an incident-response procedure.

## dependency status

The project uses `npm audit` as an awareness check. Some vulnerabilities may come from the WhatsApp browser automation dependency tree and may require a breaking upgrade. Do not apply `npm audit fix --force` without compatibility testing and an explicit review of the resulting dependency changes.
