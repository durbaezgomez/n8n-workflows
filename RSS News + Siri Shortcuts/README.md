# RSS Aggregator Webhook - n8n Workflow

Advanced n8n workflow for aggregating, filtering, and formatting news from multiple RSS feeds with webhook API response capability.

## 🚀 Features

- **Multi-source aggregation** - fetch articles from multiple RSS feeds stored in Data Table
- **Deduplication** - automatic removal of duplicates based on links
- **Filtering and sorting** - by date, title, or category
- **Data enrichment** - add metadata, extract images, generate summaries
- **Webhook API** - return formatted data via HTTP endpoint
- **Statistics** - article count, sources, categories, date range

## 📋 Requirements

- n8n (self-hosted or cloud)
- Data Table with `url` column containing RSS feed addresses
- Optional columns: `name`, `category`, `language`

## 🔧 Installation

1. Import workflow into n8n
2. Replace Data Table ID with your own ID
3. Add RSS sources to the table
4. Activate workflow
5. Copy webhook URL from "Webhook Trigger" node

## 🌐 API Usage

### Endpoint
```
GET /webhook/rss-aggregator
```

### Query Parameters (optional)

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `limit` | integer | 50 | Maximum number of articles to return |
| `sortBy` | string | date | Sort by: `date` or `title` |
| `category` | string | - | Filter by category |

### Examples
```bash
# Basic call
curl https://your-n8n.com/webhook/rss-aggregator

# With parameters
curl "https://your-n8n.com/webhook/rss-aggregator?limit=10&sortBy=date&category=tech"
```

### Sample Response
```json
{
  "success": true,
  "timestamp": "2026-01-19T10:30:00.000Z",
  "stats": {
    "totalArticles": 10,
    "totalFetched": 150,
    "sources": 5,
    "categories": ["tech", "AI", "programming"],
    "dateRange": {
      "oldest": "2026-01-18T08:00:00.000Z",
      "newest": "2026-01-19T10:00:00.000Z"
    }
  },
  "articles": [
    {
      "title": "Example Article",
      "link": "https://example.com/article",
      "description": "Article description...",
      "summary": "First 200 characters...",
      "pubDate": "2026-01-19T09:00:00.000Z",
      "creator": "John Doe",
      "categories": ["tech"],
      "imageUrl": "https://example.com/image.jpg",
      "source": {
        "name": "Tech Blog",
        "url": "https://techblog.com"
      }
    }
  ]
}
```

## 🏗️ Workflow Structure
```
Webhook Trigger → Get RSS Sources → Loop Over Sources → Read RSS Feed 
                                          ↓                    ↓
                                   Aggregate Point ← Enrich RSS Items
                                          ↓
                              Remove Duplicates
                                          ↓
                              Format & Enrich Data
                                          ↓
                                Return Response
```

## ⚙️ Data Table Configuration

Recommended columns in RSS sources table:

| Column | Type | Required | Description |
|--------|------|----------|-------------|
| `url` | string | ✅ | RSS feed URL |
| `name` | string | ❌ | Source name |
| `category` | string | ❌ | Category (e.g., tech, news, sport) |
| `language` | string | ❌ | Language (e.g., en, pl, es) |

## 🔒 Security

- Consider adding authentication to webhook (Header Auth)
- Set up rate limiting in n8n
- Validate input parameters
- Consider caching results for frequent queries

## 🛠️ Customization

### Add custom fields to articles

Edit the "Format & Enrich Data" code node to include additional fields:
```javascript
// Add custom field
wordCount: (data.content || '').split(' ').length,
readTime: Math.ceil((data.content || '').split(' ').length / 200)
```

### Filter by date range

Add to the "Format & Enrich Data" node:
```javascript
const daysAgo = $('Webhook Trigger').item.json.query?.days || 7;
const cutoffDate = Date.now() - (daysAgo * 24 * 60 * 60 * 1000);

filteredArticles = articles.filter(article => 
  article.timestamp > cutoffDate
);
```

## 📊 Use Cases

- News aggregation dashboard
- Content curation for newsletters
- Social media automation
- Market intelligence gathering
- Blog content discovery
- Research monitoring

## 🐛 Troubleshooting

**No articles returned:**
- Check if RSS feeds are accessible
- Verify Data Table contains valid URLs
- Check n8n execution logs for errors

**Duplicate articles:**
- Ensure "Remove Duplicates" node is properly configured
- Check if `link` field exists in RSS items

**Slow response:**
- Reduce number of RSS sources
- Decrease `limit` parameter
- Implement caching layer