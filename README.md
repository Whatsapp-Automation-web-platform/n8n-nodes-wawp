## Quick Start (Wawp for N8N)

1) Navigate to N8N Settings > Community nodes.  
2) Install @wawp/n8n-nodes-wawp by added to npm Package Name input.
3) Create a **free Wawp account**.  
4) Connect your WhatsApp number using a **QR code** on wawp site or by N8N.  
5) Insert the **instance id and access token** into the Credential to connect with.  
6) Customize your selected **notification messages**.

> **Important:** When entering phone numbers, always include the country code (e.g., 966 for Saudi Arabia). Do not include the `+` symbol or `00` prefix.

> A Wawp account is required to access all plugin features.  
> **Free plan:** Create a new account and send **50 WhatsApp messages/month**.  
[> **👉 Try Wawp for FREE (250 Messages/Month)** – *Promo landing*](https://wawp.net/)
[> **📌 Facebook Community** – Join other users for support, advice, and tips.  ](https://www.facebook.com/groups/wawpcommunity)
> **📚 Getting started** – Step-by-step guides, FAQs, and tutorials.  

---

## Installation

Follow the official guide to install community nodes:  
https://docs.n8n.io/integrations/community-nodes/installation/
=======
Before you begin, install the following on your development machine:

### Required

- **[Node.js](https://nodejs.org/)** (v22 or higher) and npm
  - Linux/Mac/WSL: Install via [nvm](https://github.com/nvm-sh/nvm)
  - Windows: Follow [Microsoft's NodeJS guide](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-windows)
- **[git](https://git-scm.com/downloads)**

### Recommended

- Follow n8n's [development environment setup guide](https://docs.n8n.io/integrations/creating-nodes/build/node-development-environment/)

> [!NOTE]
> The `@n8n/node-cli` is included as a dev dependency and will be installed automatically when you run `npm install`. The CLI includes n8n for local development, so you don't need to install n8n globally.

## Getting Started with this Starter

Follow these steps to create your own n8n community node package:

### 1. Create Your Repository

[Generate a new repository](https://github.com/n8n-io/n8n-nodes-starter/generate) from this template, then clone it:

```bash
git clone https://github.com/<your-organization>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Install Dependencies

```bash
npm install
```

This installs all required dependencies including the `@n8n/node-cli`.

### 3. Explore the Examples

Browse the example nodes in [nodes/](nodes/) and [credentials/](credentials/) to understand the structure:

- Start with [nodes/Example/](nodes/Example/) for a basic node
- Study [nodes/GithubIssues/](nodes/GithubIssues/) for a real-world implementation

### 4. Build Your Node

Edit the example nodes to fit your use case, or create new node files by copying the structure from [nodes/Example/](nodes/Example/).

> [!TIP]
> If you want to scaffold a completely new node package, use `npm create @n8n/node` to start fresh with the CLI's interactive generator.

### 5. Configure Your Package

Update `package.json` with your details:

- `name` - Your package name (must start with `n8n-nodes-`)
- `author` - Your name and email
- `repository` - Your repository URL
- `description` - What your node does

Make sure your node is registered in the `n8n.nodes` array.

### 6. Develop and Test Locally

Start n8n with your node loaded:

```bash
npm run dev
```

This command runs `n8n-node dev` which:

- Builds your node with watch mode
- Starts n8n with your node available
- Automatically rebuilds when you make changes
- Opens n8n in your browser (usually http://localhost:5678)

You can now test your node in n8n workflows!

> [!NOTE]
> Learn more about CLI commands in the [@n8n/node-cli documentation](https://www.npmjs.com/package/@n8n/node-cli).

### 7. Lint Your Code

Check for errors:

```bash
npm run lint
```

Auto-fix issues when possible:

```bash
npm run lint:fix
```

### 8. Build for Production

When ready to publish:

```bash
npm run build
```

This compiles your TypeScript code to the `dist/` folder.

### 9. Prepare for Publishing

Before publishing:

1. **Update documentation**: Replace this README with your node's documentation. Use [README_TEMPLATE.md](README_TEMPLATE.md) as a starting point.
2. **Update the LICENSE**: Add your details to the [LICENSE](LICENSE.md) file.
3. **Test thoroughly**: Ensure your node works in different scenarios.

### 10. Publish to npm

Publishing is handled automatically by the included GitHub Actions workflow ([.github/workflows/publish.yml](.github/workflows/publish.yml)). It runs on every version tag push and publishes to npm with a provenance attestation — a requirement for n8n community nodes starting May 1, 2026.

#### One-time setup

Configure npm to trust this repository's GitHub Actions workflow so it can publish on your behalf. Log in to [npmjs.com](https://npmjs.com), open your package settings, and under **Publish access → Trusted Publishers** add a publisher with:

- **Repository owner**: your GitHub username or org
- **Repository name**: your repo name
- **Workflow name**: `publish.yml`

No token or secret needs to be stored in GitHub — the workflow uses GitHub's OIDC token instead.

> [!NOTE]
> If you prefer a traditional npm token, create a Granular Access Token on npmjs.com and store it as `NPM_TOKEN` in your repository's Actions secrets. See the comments at the top of `.github/workflows/publish.yml` for details.

#### Releasing a new version

```bash
npm run release
```

This lints, builds, prompts for a version bump, updates the changelog, commits, tags, and pushes — which triggers the workflow to publish to npm.

### 11. Submit for Verification (Optional)

Get your node verified for n8n Cloud:

1. Ensure your node meets the [requirements](https://docs.n8n.io/integrations/creating-nodes/deploy/submit-community-nodes/):
   - Uses MIT license ✅ (included in this starter)
   - No external package dependencies
   - Follows n8n's design guidelines
   - Passes quality and security review

2. Submit through the [n8n Creator Portal](https://creators.n8n.io/nodes)

**Benefits of verification:**

- Available directly in n8n Cloud
- Discoverable in the n8n nodes panel
- Verified badge for quality assurance
- Increased visibility in the n8n community

## Available Scripts

This starter includes several npm scripts to streamline development:

| Script                | Description                                                                 |
| --------------------- | --------------------------------------------------------------------------- |
| `npm run dev`         | Start n8n with your node and watch for changes (runs `n8n-node dev`)        |
| `npm run build`       | Compile TypeScript to JavaScript for production (runs `n8n-node build`)     |
| `npm run build:watch` | Build in watch mode (auto-rebuild on changes)                               |
| `npm run lint`        | Check your code for errors and style issues (runs `n8n-node lint`)          |
| `npm run lint:fix`    | Automatically fix linting issues when possible (runs `n8n-node lint --fix`) |
| `npm run release`     | Create a new release (runs `n8n-node release`)                              |

> [!TIP]
> These scripts use the [@n8n/node-cli](https://www.npmjs.com/package/@n8n/node-cli) under the hood. You can also run CLI commands directly, e.g., `npx n8n-node dev`.

## Troubleshooting

### My node doesn't appear in n8n

1. Make sure you ran `npm install` to install dependencies
2. Check that your node is listed in `package.json` under `n8n.nodes`
3. Restart the dev server with `npm run dev`
4. Check the console for any error messages

### Linting errors

Run `npm run lint:fix` to automatically fix most common issues. For remaining errors, check the [n8n node development guidelines](https://docs.n8n.io/integrations/creating-nodes/).

### TypeScript errors

Make sure you're using Node.js v22 or higher and have run `npm install` to get all type definitions.

## Resources

- **[n8n Node Documentation](https://docs.n8n.io/integrations/creating-nodes/)** - Complete guide to building nodes
- **[n8n Community Forum](https://community.n8n.io/)** - Get help and share your nodes
- **[@n8n/node-cli Documentation](https://www.npmjs.com/package/@n8n/node-cli)** - CLI tool reference
- **[n8n Creator Portal](https://creators.n8n.io/nodes)** - Submit your node for verification
- **[Submit Community Nodes Guide](https://docs.n8n.io/integrations/creating-nodes/deploy/submit-community-nodes/)** - Verification requirements and process

## Contributing

Have suggestions for improving this starter? [Open an issue](https://github.com/n8n-io/n8n-nodes-starter/issues) or submit a pull request!
>>>>>>> 68fe6eb157b50be26c308968119b2d87dd191d1b

Then install this package on your n8n instance (via UI “Community nodes” or CLI):

```bash
# in your n8n container / host
npm install @wawp/n8n-nodes-wawp
```

---

**Nodes Included**

![Banner image](https://wawp.net/wp-content/uploads/2025/09/Wawpsend.png)

**1) Wawp Trigger (webhook)**

**Receives events from Wawp (e.g. message, message.reaction, message.ack, group.v2.join, presence.update, etc.).**

Has a switch-like multi-output: one “any” output + one output per specific event.

Use Test URL (/webhook-test/<path>) while designing, and Production URL (/webhook/<path>) when deployed.

Icon support: place wawp.png/wawp.svg in nodes/WawpTrigger/ (bundled to dist via gulp build:icons).
    
**2) Wawp (main action node)**

**A single node with Categories to keep the UI tidy. Each category exposes only the operations it needs.**
    
⛓️‍💥 Session – Instances: Create / Start / Stop / Restart / Delete / Logout / Get Info / Me

📲 Authentication – Login: Get QR (raw & image), Request Code

📤 Send Messages: Send Text / Image / PDF / Voice / Video / Location / Poll / Contact Vcard, Mark Seen, Start/Stop Typing, Reaction, Star

🟢 Presence information: Set presence, Get presence by chatId

🏷️ Labels: List / Create / Update / Delete, Labels for a Chat (get/save), Chats with a Label

ℹ️ WhatsApp Profile info: Get profile, Set display name, Set “About” status, Upload/Delete picture

📢 Channels Control: List / Create / Get / Delete, Preview messages, Follow/Unfollow, Mute/Unmute, Search (view/text), Metadata (views/countries/categories)

💬 Chats: List / Overview, Delete chat, Picture, Messages (list/clear/read/byId/delete/edit/pin/unpin), Archive/Unarchive, Mark unread

🔊 24 Hour Status: Text / Image / Voice / Video / Delete

🪪 Contacts: List all, Get, Check phone exists, About, Profile picture, Block/Unblock, Upsert contact

🪪 LIDs: List, Count

👥 Groups: List / Create, Join info / Join, Count / Refresh, Get / Delete / Leave, Picture get/set/delete, Description / Subject,
Security (info-admin-only & messages-admin-only) get/set, Invite code get/revoke, Participants get/add/remove, Admin promote/demote

---

## 🏗️ What is a Webhook?

A webhook is an HTTP POST request sent from Wawp to your n8n instance whenever an event occurs on WhatsApp.

- **Push-Based:** You don't ask for updates; Wawp sends them automatically.
- **Real-Time:** Events arrive within milliseconds of occurring.
- **Selective:** You choose which event types to receive in your Wawp dashboard.

**Webhooks vs. Polling:** Polling wastes API quota and introduces latency. Webhooks are delivered instantly, making your workflows much more responsive and efficient.

### 🚀 Quick Webhook Setup for n8n

1.  Use the **Wawp Trigger** node in your n8n workflow.
2.  While designing, use the **Test URL**. For production, use the **Production URL**.
3.  Configure the URL in your [Wawp Dashboard](https://wawp.net/account/connect) under the **Webhook** section of your instance.
4.  If testing locally, use a tool like **ngrok** to expose your local n8n instance to the internet.

---

## 🆔 WhatsApp ID (JID) Reference

In the Wawp ecosystem, every entity is identified by a unique string called a **JID**. Understanding these suffixes is critical for routing messages correctly.

| Suffix | Identity Type | Description |
| :--- | :--- | :--- |
| `@c.us` | Individual / Contact | Standard personal or business account. Used for 1-on-1 chats. |
| `@g.us` | Group | Identifies a multi-user group conversation. |
| `@newsletter` | Channel | Represents a public Broadcast Channel or Newsletter. |
| `@lid` | Lookup ID | Privacy-preserving identifier used to mask real phone numbers. |
| `@broadcast` | Broadcast List | Identifiers for legacy broadcast lists or status. |

> **💡 Pro Tip:** When storing IDs in your database/CRM, always store the **full JID** (e.g., `447441429009@c.us`) to ensure compatibility and prevent collisions.

---

## 🔐 Security & Best Practices

1.  **Idempotency:** Wawp may send the same event multiple times if your server is slow to respond. Always check the `event.id` to prevent duplicate processing.
2.  **Immediate Response:** Always ensure your webhook endpoint responds with `200 OK` as quickly as possible. n8n does this automatically, but avoid long-running nodes before the response if possible.
3.  **Validate Source:** For higher security, add a secret query parameter to your webhook URL (e.g., `?secret=my_token`) and validate it within your workflow.

---

## 🛠️ Common Event Types

| Event | Description |
| :--- | :--- |
| `message` | New message received (text, image, video, etc.) |
| `message.reaction` | User reacted to a message with an emoji |
| `message.revoked` | User deleted/recalled a message |
| `message.ack` | Message status changed (sent → delivered → read) |
| `group.participants.update` | User joined or left a group |
| `presence.update` | User's online status or typing state changed |
| `status.update` | User posted a new WhatsApp Status (Story) |

For more detailed documentation, visit the [Wawp API Docs](https://api.wawp.net/en/docs/v2/webhooks-overview).
