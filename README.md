# AIGen-Replies

**Automated, intelligent replies to WordPress comments and WooCommerce reviews — powered by AI, built for real-world use.**

> 🇮🇷 Developed by an Iranian developer. Optimized for cost-efficiency, privacy-aware deployment, and Persian-language contexts — but ready for global use.

---

## ✨ Key Features

- ✅ **Dual Support**: Works with **standard WordPress comments** (`comment_type = ''`) **and WooCommerce reviews** (`comment_type = 'review'`). Toggle behavior in settings.
- 🤖 **Multi-Provider AI Backend**: Choose between **OpenAI**, **DeepSeek**, or **[OneAPI.ir](https://one-api.ir/)** (a low-cost, Iran-friendly proxy for OpenAI models).
- ⚙️ **Dynamic Context-Aware Prompts**: Use placeholders like `{product_title}`, `{customer_comment}`, `{short_description}`, `{attributes}`, and even `{previous_replies}` to shape highly relevant responses.
- 🧠 **Style Mimicry**: AI learns from your last 1–10 manual replies to match your brand’s tone and phrasing.
- ⏰ **Smart Scheduling**:  
  - Set a **default delay** (e.g., 60 minutes) before replying.  
  - Define **keyword-triggered rules**: if a comment contains “warranty” or “refund”, wait 2 hours or only reply between 9 AM–5 PM.
- 🚫 **Advanced Spam & Content Filtering**:  
  - Block duplicate comments.  
  - Define **forbidden keywords** (e.g., profanity). When detected, auto-send a custom message and skip AI processing.
- 💬 **Canned Responses**: Predefine replies for FAQs (e.g., “What’s your return policy?”) — no API call needed.
- 👤 **Dedicated AI User**: Auto-created admin user named `🤖 هوش مصنوعی` (AI Assistant) with full comment privileges.
- 📊 **AI-Powered Sentiment & Insight Analysis**:  
  - Generate a **comprehensive Persian-language report** on customer feedback.  
  - Identifies **promoters** (“I’ll buy again!”), **pain points**, strengths, and improvement suggestions.  
  - Includes a **rating distribution chart** (via Chart.js).
- 🤔 **Human Intervention Detection**: AI self-assesses if a reply is too risky — if so, it creates a **pending task** in your dashboard and sends a fallback message.
- 🧹 **Zero-Trace Uninstall**: Removes all options, logs, transients, and database tables on deletion.
- 🔒 **Secure by Design**:  
  - API keys stored only in `wp_options` — never in files or logs.  
  - All inputs sanitized. All admin actions protected by nonces and capability checks.
- 🌐 **Multi-Language Ready**: Auto-detects comment language (Persian/English) and responds in-kind. Extendable to `fa`, `en`, `ar`, and more.
- 🧪 **Debug & Diagnostic Suite**: Built-in tools to test API, clear logs, rebuild tables, and simulate replies.

---

## 📥 Installation

### Option 1: Manual Upload
1. Upload the `aigen-replies` folder to `/wp-content/plugins/`.
2. Go to **Plugins → Installed Plugins** and activate **AIGen-Replies**.
3. Navigate to **Smart Replies → Settings** to configure your AI provider and preferences.

### Option 2: ZIP Upload
1. Download the latest release as a ZIP file.
2. In WordPress Admin: **Plugins → Add New → Upload Plugin**.
3. Choose the ZIP file, install, and activate.

> 💡 **WooCommerce is optional**. If not installed, the plugin works exclusively on standard post/page comments.

---

## ⚙️ Configuration

After activation, go to **Smart Replies → Settings**.

### Required Settings
- **AI Provider**: `OneAPI` (recommended for low cost & Iranian users), `OpenAI`, or `DeepSeek`.
- **API Key**: Get one from your chosen provider.
- **Enable Auto-Reply**: Toggle to auto-respond to approved comments.

### Advanced Settings
- **Model**: `gpt-4o-mini` (default), `gpt-4`, `deepseek-chat`, etc.
- **Temperature**: `0.1` (predictable) to `0.9` (creative).
- **Max Tokens**: `50–2000` (default: `500`).
- **Response Scope**: Reply to **all comments**, **WooCommerce reviews only**, or exclude specific products/categories/post types.
- **Custom Prompt**: Fully editable. Example:
  ```text
  You are a customer support agent for an online store...
  Product: {product_title}
  Customer said: "{customer_comment}"
  Previous manager replies: {previous_replies}
  Respond in the same language, matching the tone above.







Smart Tools
Live Preview: Type a sample comment and see the AI’s response instantly.
Scheduled Replies Dashboard: View and manage delayed responses.
Pending Human Tasks: Review comments flagged for manual intervention.
🔒 Security & Best Practices
✅ API keys never appear in code, version control, or debug logs.
✅ All user inputs are sanitized using WordPress’s sanitize_text_field and sanitize_textarea_field.
✅ Admin AJAX endpoints require manage_options capability + valid nonce.
✅ .gitignore prevents accidental commits of logs or config files.
✅ Debug mode must be explicitly enabled — logs are not written by default.
🌐 Multi-Language Support
Auto-detection: Uses character analysis to detect Persian vs. English.
Response language: Matches the detected comment language.
Admin UI: Currently in Persian, but fully internationalizable.
→ Language files (.pot) coming soon! Contribute translations via /languages/.
🧩 How It Works
A user submits a comment or product review.
If approved and not excluded, the system:
Checks for canned responses or forbidden keywords.
Fetches product/post context + recent manager replies.
Builds a rich prompt with dynamic placeholders.
Sends request to your chosen AI provider.
If auto-reply is on, the response is posted immediately (or scheduled).
If preview mode is on, you see the reply before publishing.
If the AI suspects high risk (e.g., complaint, legal issue), it:
Creates a pending task in your dashboard.
Sends a fallback message (e.g., “We’ll review your feedback shortly”).
⚡ Replies are processed asynchronously via WordPress cron (minute interval), so page load isn’t blocked.

🛑 Limitations
Requires internet access to reach AI APIs.
API costs apply — monitor usage (OneAPI is ~10x cheaper than OpenAI for GPT-4o).
Not designed for high-frequency sites without usage caps (future: add daily token limits).
Comments from logged-in admins are ignored (prevents self-dialogue).
🗑️ Uninstall
Deleting via Plugins → Delete will:

Remove all plugin settings (wc_ai_review_settings).
Drop the wp_wc_ai_review_logs table.
Delete scheduled replies, tasks, and transients.
Preserve replies (they’re regular WordPress comments).
💡 To keep settings, just deactivate — don’t delete.

🤝 Contributing
We welcome:

Bug fixes
New AI provider integrations (Claude, Gemini, Mistral, etc.)
UI/UX improvements (Tailwind-based)
Multi-language admin panels
PDF/Excel export for analytics
To contribute:

Fork the repo
Create your feature branch (git checkout -b feature/your-idea)
Commit your changes (git commit -am 'Add XYZ')
Push to the branch (git push origin feature/your-idea)
Open a Pull Request
✍️ Please write clear commit messages and test on a real WordPress instance.

📄 License
This project is licensed under the GNU General Public License v2.0 — the same license as WordPress.

You are free to:

Use commercially
Modify the code
Distribute derivatives
...as long as you share alike under GPL.

🙏 Acknowledgements
Built on the WordPress Plugin API
Powered by OpenAI, DeepSeek, and OneAPI.ir
Inspired by the need for smarter, kinder, and more responsive comment sections
Uses Chart.js for analytics visualizations
Persian font via Vazirmatn
📸 Screenshots
...


💡 Demo video coming soon on YouTube!

💝 Support the Project
This plugin is free and open-source — but maintaining it takes time and resources.

If you find it valuable, consider:

⭐ Starring this repo
🐦 Sharing it with fellow developers
☕ Buying me a coffee → [Link to your donation page]
❓ Need Help?
Contact me directly:

Instagram: @mahyardev2
Telegram: @mahyarrdev
Or open a GitHub Issue with:

WordPress version
PHP version
Steps to reproduce
Error logs (with sensitive data redacted)
Make your site more engaging — let AI handle the conversations, while you focus on what matters. 💬✨
