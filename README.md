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
