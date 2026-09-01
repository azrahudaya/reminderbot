# WhatsApp voice note reminder bot

[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=flat-square&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-Web.js-25D366?style=flat-square&logo=whatsapp&logoColor=white)](https://wwebjs.dev/)
[![Express](https://img.shields.io/badge/Express-5-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com/)
[![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=flat-square&logo=sqlite&logoColor=white)](https://sqlite.org/)
[![OpenAI](https://img.shields.io/badge/OpenAI-Whisper-412991?style=flat-square&logo=openai&logoColor=white)](https://platform.openai.com/docs/guides/speech-to-text)
[![CI](https://github.com/azrahudaya/penulisanilmiah/actions/workflows/ci.yml/badge.svg)](https://github.com/azrahudaya/penulisanilmiah/actions/workflows/ci.yml)

A WhatsApp bot prototype for an academic study of voice-based task extraction. It accepts voice notes or text, extracts a title and deadline, asks for confirmation through a poll, and sends reminders before and at the deadline.

This repository is published for academic discussion and portfolio review. It is not a production-ready research platform and must not be connected to real respondents without ethics approval, informed consent, an approved data-management plan, and an independent security review.

## What it demonstrates

- Voice-note transcription and reminder extraction.
- Save, edit, or cancel confirmation through WhatsApp polls.
- Reminder scheduling and recovery after server restarts.
- Admin dashboard for review, metrics, exports, and operational status.
- Local SQLite storage with no external database service.

## Run locally

Requirements: Node.js 18+, npm, FFmpeg, Chrome/Chromium, and a WhatsApp account.

```bash
git clone https://github.com/azrahudaya/penulisanilmiah.git
cd penulisanilmiah
npm install
cp .env.example .env
npm test
npm start
```

Add the minimum configuration to `.env`:

```env
OPENAI_API_KEY=
TIMEZONE=Asia/Jakarta
ADMIN_PHONE=628xxxxxxxxxx
DASHBOARD_PASSWORD=change-this-password
ADMIN_SESSION_SECRET=replace-with-a-random-string-at-least-32-characters-long
```

Scan the WhatsApp QR code shown in the terminal. Run the dashboard separately:

```bash
npm run admin
```

The local dashboard is available at `http://127.0.0.1:3000`.

## Data and privacy boundary

The application uses the local `data/` directory by default, but `DB_PATH` and `RESEARCH_AUDIO_DIR` can point to another local location. Temporary transcription files may also exist briefly in the operating system temporary directory. Treat phone numbers, respondent profile fields, voice files, transcripts, extracted tasks, research logs, and all derived copies as sensitive research data.

- Use synthetic data for development and testing.
- Keep `.env`, WhatsApp sessions, databases, audio, transcripts, and exports outside Git.
- Do not send identifiable research data to external transcription or AI services without documented approval and participant notice.
- Define retention, deletion, access, and backup procedures before collecting data.
- Use the admin export and deletion features only on an authorized local machine.

See [`docs/data-handling.md`](docs/data-handling.md) and [`SECURITY.md`](SECURITY.md) for the project boundary and reporting process.

## Bot commands

```text
help
list
done <id>
delete <id>
reschedule <id> <YYYY-MM-DD HH:mm>
profile
editdata
deletedata confirm
```

## VPS deployment reference

The repository includes an example Nginx configuration at [`deploy/reminderbot.nginx`](deploy/reminderbot.nginx). Do not treat it as a complete production deployment guide. Before any deployment, configure HTTPS, a strong dashboard password, a random session secret, restricted network access, encrypted backups, monitoring, and a tested deletion procedure.

```bash
pm2 start src/index.js --name reminderbot
pm2 start admin/server.js --name reminderbot-admin
pm2 save
```

## License

The source is available under the restricted terms in [`LICENSE.md`](LICENSE.md).
