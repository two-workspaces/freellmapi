# Deploy and Host FreeLLMAPI on Railway

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/new/template/freellmapi-server?referralCode=sLjDXb&utm_medium=integration&utm_source=button&utm_campaign=freellmapi-server)

FreeLLMAPI puts the free tiers of many LLM providers behind one OpenAI-compatible `/v1` endpoint. You add your own provider keys, and its router picks an available model for each request and falls over to the next one when a provider hits its limit. This template runs it on Railway with your login created in advance and a volume that keeps your data across redeploys.

This is a community template, not made or supported by the FreeLLMAPI project.

## About Hosting FreeLLMAPI

A new FreeLLMAPI install normally lets whoever reaches it first start creating the account, with a setup code from the logs. This template creates your account from `ADMIN_EMAIL` and `ADMIN_PASSWORD` before the server starts listening, so that window never opens. Your database and encrypted keys sit on a volume at `/app/server/data`, so a redeploy or a new variable doesn't wipe them.

After deploying, open the service's domain and sign in. Add provider keys on the **Keys** page, then copy the unified API key from that page's header. Point any OpenAI-compatible client at `https://<your-domain>/v1` with that key.

**Please read before relying on it.** Upstream describes the project as single-user and "for personal experimentation and learning, not production". Free tiers can change or vanish, so answers can slow down or stop. Use your own keys, and check each provider's terms; upstream publishes a [provider-by-provider review](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/architecture/00-high-level-index.md#terms-of-service-review). This deploy has a public address, so keep the password and unified key private. Some providers may also treat traffic from a cloud host differently from a home connection.

## Common Use Cases

- Prototype an app against an OpenAI-style API without paying for tokens
- Keep one always-on endpoint for your own editor, CLI and coding-agent tools
- Try many models and providers through a single key and base URL

## Dependencies for FreeLLMAPI Hosting

- Free API keys from the LLM providers you want to use

### Deployment Dependencies

- [FreeLLMAPI on GitHub](https://github.com/tashfeenahmed/freellmapi)
- [Install and deploy guide](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/install/01-install.md)
- [API reference](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/api/01-rest-api.md)

### Implementation Details

- **Keep `ENCRYPTION_KEY`:** it decrypts your stored provider keys. If it changes, you have to add them all again.
- **Login variables:** `ADMIN_EMAIL` and `ADMIN_PASSWORD` apply only while no account exists. Later edits to them do nothing, and the log says so on each boot. Change your password in the dashboard, or use the one-time reset code it prints to the deploy logs.
- **Same image as upstream:** the Dockerfile is one pinned `FROM` line on upstream's image, with no changes.
- **Premium is optional:** upstream sells a live model catalog. Free installs get a monthly snapshot of it and need nothing else.

## Why Deploy FreeLLMAPI on Railway?

Railway is a singular platform to deploy your infrastructure stack. Railway will host your infrastructure so you don't have to deal with configuration, while allowing you to vertically and horizontally scale it.

By deploying FreeLLMAPI on Railway, you are one step closer to supporting a complete full-stack application with minimal burden. Host your servers, databases, AI agents, and more on Railway.
