
## 🛠️ Smart Tools

- **Live Preview**: Type sample comment, see AI response instantly
- **Scheduled Replies Dashboard**: View/manage delayed responses
- **Pending Human Tasks**: Review comments flagged for manual intervention

## 🔒 Security & Best Practices

- ✅ API keys never appear in code, version control, or debug logs
- ✅ All user inputs sanitized using `sanitize_text_field()` and `sanitize_textarea_field()`
- ✅ Admin AJAX endpoints require `manage_options` capability + valid nonce
- ✅ `.gitignore` prevents accidental commits of logs/config files
- ✅ Debug mode must be explicitly enabled — logs not written by default

## 🌐 Multi-Language Support

- **Auto-detection**: Uses character analysis to detect Persian vs. English
- **Response language**: Matches detected comment language
- **Admin UI**: Currently in Persian, but fully internationalizable
- **Language files**: `.pot` coming soon! Contribute translations via `/languages/`

## 🧩 How It Works

1. User submits comment or product review
2. If approved and not excluded, system:
   - Checks for canned responses or forbidden keywords
   - Fetches product/post context + recent manager replies
   - Builds rich prompt with dynamic placeholders
   - Sends request to chosen AI provider
3. If auto-reply on: response posted immediately (or scheduled)
4. If preview mode on: you see reply before publishing
5. If AI suspects high risk (complaint, legal issue):
   - Creates pending task in dashboard
   - Sends fallback message (e.g., "We'll review your feedback shortly")

**⚡ Asynchronous Processing**: Replies processed via WordPress cron (minute interval) — no page load blocking

## 🛑 Limitations

- Requires internet access to reach AI APIs
- API costs apply — monitor usage (OneAPI ~10x cheaper than OpenAI for GPT-4o)
- Not designed for high-frequency sites without usage caps (future: daily token limits)
- Comments from logged-in admins ignored (prevents self-dialogue)

## 🗑️ Uninstall

Deleting via **Plugins → Delete** will:

- Remove all plugin settings (`wc_ai_review_settings`)
- Drop the `wp_wc_ai_review_logs` table
- Delete scheduled replies, tasks, and transients
- Preserve replies (they're regular WordPress comments)

**💡 To keep settings, just deactivate — don't delete.**

## 🤝 Contributing

We welcome:

- Bug fixes
- New AI provider integrations (Claude, Gemini, Mistral, etc.)
- UI/UX improvements (Tailwind-based)
- Multi-language admin panels
- PDF/Excel export for analytics

**To contribute:**

1. Fork the repo
2. Create feature branch: `git checkout -b feature/your-idea`
3. Commit changes: `git commit -am 'Add XYZ'`
4. Push to branch: `git push origin feature/your-idea`
5. Open a Pull Request

**✍️ Write clear commit messages and test on real WordPress instance.**

## 📄 License

Licensed under **GNU General Public License v2.0** — same as WordPress.

You are free to:

- Use commercially
- Modify the code
- Distribute derivatives

...as long as you share alike under GPL.

## 🙏 Acknowledgements

- Built on WordPress Plugin API
- Powered by OpenAI, DeepSeek, and OneAPI.ir
- Inspired by need for smarter, kinder comment sections
- Uses Chart.js for analytics visualizations
- Persian font via Vazirmatn

## 📸 Screenshots

*Dashboard overview, settings page, comment meta box, AI analysis report*

**💡 Demo video coming soon on YouTube!**

## 💝 Support the Project

This plugin is free and open-source — but maintaining takes time and resources.

If you find it valuable:

- ⭐ Star this repo
- 🐦 Share with fellow developers
- ☕ Buy me a coffee → [Your Donation Link]

## ❓ Need Help?

**Contact directly:**
- Instagram: @mahyardev2
- Telegram: @mahyarrdev

**Or open GitHub Issue with:**
- WordPress version
- PHP version
- Steps to reproduce
- Error logs (sensitive data redacted)

**Make your site more engaging — let AI handle conversations, while you focus on what matters. 💬✨**
