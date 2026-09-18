# Infobip MCP

Cursor plugin for [Infobip's](https://www.infobip.com) remote MCP (Model Context Protocol) servers. Connect Cursor's AI agent directly to Infobip's messaging platform to send messages, manage verification flows, and query account data across channels, no custom integration code required.

Built from the specs published in [infobip/mcp](https://github.com/infobip/mcp). See [infobip.com/docs/mcp](https://www.infobip.com/docs/mcp) for full product documentation.

## Servers

| Server | Endpoint | Description |
|---|---|---|
| SMS | `/sms` | Send/preview messages, scheduling, bulk sending, multilingual support, delivery reports, message logs, URL tracking |
| WhatsApp | `/whatsapp` | Template messages, text/media sending, template management, delivery reports, SMS failover |
| WhatsApp Flow *(Early Access)* | `/whatsapp-flow` | Create/manage static & dynamic flows, interactive components, flow JSON management |
| Viber | `/viber` | Rich media messaging (images, videos, files), scheduling, SMS failover, URL tracking |
| RCS | `/rcs` | Rich messages with multimedia, suggested replies, carousels, barcodes, SMS/MMS failover |
| Email | `/email` | Send email messages, bulk sending, scheduling, email address validation |
| Voice | `/voice` | Single/multi-recipient calls, text-to-speech, pre-recorded audio, conference calls, call logs |
| Message *(Early Access)* | `/message` | Multi-channel (SMS, RCS, MMS, Viber) sending in a single tool call |
| 2FA | `/2fa` | Application management, PIN templates (SMS/Email/Voice), verification workflows |
| Account Management | `/account-management` | Account balance, free messages count, account details, audit logs |
| Infobip Documentation | `/search` | Documentation search, API reference, use cases, product guides |
| Infobip Deep Research | `/deep-research` | Deep search across API documentation, detailed content retrieval |
| Infobip Provision | `/provision` | Sender registration and number setup workflows |
| Infobip Observe | `/observe` | Understand traffic, performance, and cost by accessing metrics, billing ussage, error-code lookups, and cross-channel message logs. Read-only |

Base URL: `https://mcp.infobip.com`

## Prerequisites

- A valid Infobip account (a [free trial](https://infobip.com/signup?utm_source=infobip-mcp-github&utm_medium=referral&utm_campaign=mcp) is available)
- Cursor with MCP support enabled

## Authentication

This plugin's `mcp.json` uses **OAuth 2.1** by default, so no secrets are stored in the config. Cursor triggers the authorization flow automatically on first connection to each server.

If your setup requires an API key instead, add an `Authorization` header to the relevant server entry in `mcp.json`:

```json
{
  "type": "http",
  "url": "https://mcp.infobip.com/sms",
  "headers": {
    "Authorization": "App ${INFOBIP_API_KEY}"
  }
}
```

Set `INFOBIP_API_KEY` in your environment. See [API authentication](https://www.infobip.com/docs/essentials/api-essentials/api-authentication?utm_source=infobip-mcp-github&utm_medium=referral&utm_campaign=mcp#api-key-header) for details on generating a key.

## Links

- [Infobip MCP documentation](https://www.infobip.com/docs/mcp?utm_source=infobip-mcp-github&utm_medium=referral&utm_campaign=mcp)
- [infobip/mcp on GitHub](https://github.com/infobip/mcp) (source of truth for server specs)
- [Provisioning MCP docs](https://www.infobip.com/docs/mcp/provisioning-mcp)

## License

MIT, see [LICENSE](./LICENSE).
