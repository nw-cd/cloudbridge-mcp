# CloudBridge MCP Server

Hosted MCP server for [CloudBridge](https://cloud-bridge.ru) — a SaaS that
transfers and syncs files between 19 cloud storages: Yandex Disk, Google
Drive, VK Cloud (Mail.ru), Dropbox, OneDrive, Telegram channels, MEGA,
pCloud, TeraBox, S3-compatible, WebDAV (Nextcloud/ownCloud/Koofr),
FTP/FTPS, Google Photos, Kinescope.

- **Endpoint:** `https://cloud-bridge.ru/api/mcp` (Streamable HTTP,
  JSON-RPC over POST)
- **Registry:** [`ru.cloud-bridge/cloudbridge`](https://registry.modelcontextprotocol.io)
- **Docs:** https://cloud-bridge.ru/mcp
- **Auth:** `X-API-Key: cb_live_…` header — create a key in your
  CloudBridge dashboard → API (requires the API-access add-on)

## Client config

```json
{
  "mcpServers": {
    "cloudbridge": {
      "url": "https://cloud-bridge.ru/api/mcp",
      "headers": { "X-API-Key": "cb_live_YOUR_KEY" }
    }
  }
}
```

## Tools

**Read:** `list_clouds`, `list_files`, `list_transfers`, `get_transfer`,
`get_usage`, `list_share_links`, `get_download_url`, `read_text_file`

**Mutating (30/hour cap):** `create_transfer`, `remote_upload`,
`create_share_link`, `cancel_transfer`, `revoke_share_link`

Introspection (`initialize`, `ping`, `tools/list`) answers without a key —
`tools/call` is key-gated.
