# AIGen-Replies

AI-powered auto-replies for WordPress comments and WooCommerce reviews — intelligent, secure, and fully controllable.

---

## ✨ Features

- ✅ **Dual Support**: Handles both **standard WordPress comments** (`comment_type = ''`) and **WooCommerce product reviews** (`comment_type = 'review'`).
- 🤖 **Multi-Provider AI**: Works with **OpenAI**, **DeepSeek**, or **[OneAPI.ir](https://one-api.ir/)** (low-cost, Iran-friendly API gateway).
- ⚙️ **Smart Prompt Engine**: Use dynamic placeholders like `{product_title}`, `{customer_comment}`, `{short_description}`, `{attributes}`, and `{previous_replies}`.
- 🧠 **Style Mimicry**: AI learns from your last 1–10 manual replies to match your brand’s tone.
- ⏰ **Smart Scheduling**:  
  - Set a **default delay** (e.g., 60 minutes).  
  - Create **keyword-triggered rules**: if comment contains “warranty”, wait 2 hours or reply only during 09:00–17:00.
- 🚫 **Spam & Keyword Filters**:  
  - Block duplicate comments.  
  - Define **forbidden keywords** (e.g., profanity).  
  - Auto-send a **custom fallback message** instead of AI reply.
- 💬 **Canned Responses**: Predefine answers to FAQs like “What’s your return policy?” — no API call needed.
- 👤 **Dedicated AI User**: Auto-created admin user named `🤖 هوش مصنوعی`.
- 📊 **AI-Powered Analysis**:  
  - Persian-language report on customer sentiment.  
  - Detects promoters (“I’ll buy again!”), strengths, and weaknesses.  
  - Includes **rating distribution chart** (via Chart.js).
- 🤔 **Human Intervention Detection**: AI self-flags risky comments → creates **admin task** + sends fallback reply.
- 🔒 **Secure API Handling**: Keys stored only in `wp_options` — never in code, logs, or version control.
- 🌐 **Multi-Language Ready**: Auto-detects Persian/English and replies in the same language.
- 🧹 **Clean Uninstall**: Removes all settings, logs, and DB tables on plugin deletion.

---

## 📥 Installation

**Option 1: Manual Upload**  
1. Upload the `aigen-replies` folder to `/wp-content/plugins/`.  
2. Go to **Plugins → Installed Plugins** and activate **AIGen-Replies**.  
3. Navigate to **Smart Replies → Settings** to configure your API key.

**Option 2: ZIP Upload**  
1. Download the plugin ZIP from GitHub.  
2. In WordPress Admin: **Plugins → Add New → Upload Plugin**.  
3. Choose ZIP → **Install Now** → **Activate**.

> 💡 **WooCommerce is optional**. Without it, the plugin works on standard post/page comments only.

---

## ⚙️ Configuration

After activation, go to **Smart Replies → Settings**.

### Required Settings
- **API Provider**: OneAPI (recommended), OpenAI, or DeepSeek  
- **API Key**: Get from your provider ([one-api.ir](https://one-api.ir/) for low-cost access)  
- **Auto-Reply**: Enable to auto-respond to approved comments

### Advanced Settings
- **Model**: `gpt-4o-mini` (default), `gpt-4`, `deepseek-chat`  
- **Temperature**: `0.1` (deterministic) to `0.9` (creative)  
- **Max Tokens**: `50–2000`  
- **Response Scope**: Reply to all comments, WooCommerce only, or exclude specific products/categories  
- **Custom Prompt**: Fully editable. Example:
  ```text
  You are a support agent...
  Product: {product_title}
  Customer said: "{customer_comment}"
  Previous replies: {previous_replies}
  Respond in the same language and tone.

  
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
- ☕ Buy me a coffee → <a href="buymeacoffee.com/Mahyarrdev">click me</a>

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
