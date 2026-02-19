# Scout Skills

Skills for OpenClaw agents to interact with Scout data platform.

## Overview

This project provides OpenClaw skills for working with Scout's data capabilities - collections, tables, documents, agents, drive storage, syncs, and usage monitoring.

## Skills

### `scout` - Scout API Integration

Interact with Scout data platform API. Use when working with Scout collections, tables, documents, agents, drive storage, syncs, or usage.

**Capabilities:**

| Feature | Description |
|---------|-------------|
| **Collections** | Create, list, update, delete top-level data containers |
| **Tables** | Manage structured data with custom schemas (text, number, select, datetime, etc.) |
| **Documents** | CRUD operations on table records with bulk insert support |
| **Agents** | Manage AI assistants that interact with your Scout data |
| **Drive** | Upload and download files to Scout storage |
| **Syncs** | Sync data from external sources (websites, Notion, Google Drive, etc.) |
| **Usage** | Monitor API usage and costs |

**Sync Sources Supported:**

- Website crawler (`com.scoutos.website`)
- Sitemap (`com.scoutos.sitemap`)
- Notion (`com.notion.notion`)
- Google Drive (`com.google.drive`)
- Microsoft 365 (`com.microsoft.365`)
- Laserfiche (`com.laserfiche.repository`)
- Guided Crawl - AI browser automation (`com.scoutos.guided_crawl`)

**Example Usage:**

```bash
# List collections
curl -H "Authorization: Bearer $SCOUT_API_KEY" \
  "https://api.scoutos.com/v2/collections"

# Create a table
curl -X POST \
  -H "Authorization: Bearer $SCOUT_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"table_display_name": "Tasks", "schema": [...]}' \
  "https://api.scoutos.com/v2/collections/{collection_id}/tables"

# Add documents
curl -X POST \
  -H "Authorization: Bearer $SCOUT_API_KEY" \
  -H "Content-Type: application/json" \
  -d '[{"title": "Task 1"}, {"title": "Task 2"}]' \
  "https://api.scoutos.com/v2/collections/{col_id}/tables/{tbl_id}/documents"
```

## Installation

Copy the skill directory to your OpenClaw skills folder:

```bash
cp -r scout-skills ~/.openclaw/workspace/skills/
```

Or use the packaged `scout.skill` file.

## Authentication

All Scout API endpoints require a Bearer token:

1. Log in to [Scout](https://scoutos.com)
2. Navigate to Settings → API Keys
3. Create or copy your API key
4. Set environment variable: `SCOUT_API_KEY=your-api-key`

## Resources

- **Official Docs**: https://docs.scoutos.com
- **API Reference**: https://docs.scoutos.com/api-sdk
- **Status Page**: https://status.scoutos.com
- **Support**: support@scoutos.com

## License

MIT