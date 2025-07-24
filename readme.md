# 🚀 YouTube & Web Scrapers Collection

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Apify](https://img.shields.io/badge/Powered%20by-Apify-blue)](https://apify.com)
[![n8n](https://img.shields.io/badge/Built%20with-n8n-FF6D6D)](https://n8n.io)

> A comprehensive collection of web scrapers powered by Apify APIs for YouTube content extraction, financial data scraping, and website screenshots. Perfect for data analysts, content creators, and developers.

## 📋 Table of Contents

- [Features](#-features)
- [Prerequisites](#-prerequisites)
- [Quick Start](#-quick-start)
- [Available Scrapers](#-available-scrapers)
- [API Documentation](#-api-documentation)
- [Usage Examples](#-usage-examples)
- [cURL Commands](#-curl-commands)
- [n8n Workflow Setup](#-n8n-workflow-setup)
- [Rate Limits & Best Practices](#-rate-limits--best-practices)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

- **YouTube Video Comments** - Extract comments from any YouTube video
- **YouTube Channel Videos** - Scrape all videos from a YouTube channel
- **YouTube Transcripts** - Get accurate transcripts from YouTube videos
- **Indian Stock Data** - Fetch financial ratios and stock information
- **Website Screenshots** - Generate full-page screenshots of any website
- **Easy Integration** - Ready-to-use n8n workflow and REST API endpoints
- **High Performance** - Powered by Apify's robust scraping infrastructure

## 🔧 Prerequisites

Before you begin, ensure you have:

- [Apify API Key](https://apify.com?fpr=12vqj) (Free tier available)
- Basic understanding of REST APIs
- Optional: [n8n](https://n8n.partnerlinks.io/j9dphm7sk1hk) for workflow automation

### Getting Your Apify API Key

1. Visit [Apify.com](https://apify.com?fpr=12vqj)
2. Create a free account
3. Navigate to **Settings** → **Integrations** → **API tokens**
4. Copy your API token

## 🚀 Quick Start

Replace `<YOUR_APIFY_API_KEY>` with your actual Apify API key in all examples below.

### Basic Usage

```bash
# Test the YouTube comment scraper
curl -X POST "https://api.apify.com/v2/acts/akash9078~youtube-video-comment-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "maxComments": 10,
    "videoLink": "https://youtu.be/5kcaHAuGxmY"
  }'
```

## 🛠 Available Scrapers

### 1. YouTube Video Comment Scraper
Extract comments from any YouTube video with metadata.

**Endpoint:** `akash9078~youtube-video-comment-scraper`

**Parameters:**
- `videoLink` (string, required) - YouTube video URL
- `maxComments` (number, optional) - Maximum comments to extract (default: 10)

### 2. YouTube Channel Video Scraper
Get all videos from a YouTube channel with metadata.

**Endpoint:** `akash9078~youtube-channel-video-scraper`

**Parameters:**
- `channelUrl` (string, required) - YouTube channel URL
- `includeMetadata` (boolean, optional) - Include video metadata (default: true)

### 3. YouTube Transcript Scraper
Extract accurate transcripts from YouTube videos.

**Endpoint:** `akash9078~youtube-transcript-extractor-pro`

**Parameters:**
- `videoUrl` (string, required) - YouTube video URL

### 4. Indian Stock Financial Data Scraper
Fetch financial ratios and stock information for Indian stocks.

**Endpoint:** `akash9078~indian-stocks-financial-ratios-api`

**Parameters:**
- `symbol` (string, required) - Stock symbol (e.g., "reliance", "tcs")

### 5. Website Screenshot Generator
Generate full-page screenshots of any website.

**Endpoint:** `akash9078~full-website-screenshot-generator`

**Parameters:**
- `url` (string, required) - Website URL to screenshot
- `fullPage` (boolean, optional) - Capture full page (default: true)

## 📚 API Documentation

### Base URL
```
https://api.apify.com/v2/acts/{SCRAPER_ID}/run-sync-get-dataset-items?token={API_KEY}
```

### Response Format
All scrapers return JSON arrays with extracted data:

```json
[
  {
    "data": "extracted content",
    "metadata": {
      "timestamp": "2024-01-01T00:00:00Z",
      "source": "youtube.com"
    }
  }
]
```

## 💡 Usage Examples

### Extract YouTube Comments (Python)

```python
import requests
import json

def get_youtube_comments(video_url, max_comments=10, api_key="YOUR_API_KEY"):
    url = f"https://api.apify.com/v2/acts/akash9078~youtube-video-comment-scraper/run-sync-get-dataset-items?token={api_key}"
    
    payload = {
        "maxComments": max_comments,
        "videoLink": video_url
    }
    
    response = requests.post(url, json=payload)
    return response.json()

# Usage
comments = get_youtube_comments("https://youtu.be/5kcaHAuGxmY", max_comments=50)
print(json.dumps(comments, indent=2))
```

### Get Channel Videos (JavaScript/Node.js)

```javascript
const axios = require('axios');

async function getChannelVideos(channelUrl, apiKey) {
  const url = `https://api.apify.com/v2/acts/akash9078~youtube-channel-video-scraper/run-sync-get-dataset-items?token=${apiKey}`;
  
  const payload = {
    channelUrl: channelUrl,
    includeMetadata: true
  };
  
  try {
    const response = await axios.post(url, payload);
    return response.data;
  } catch (error) {
    console.error('Error:', error.response?.data || error.message);
  }
}

// Usage
getChannelVideos('https://www.youtube.com/@apify', 'YOUR_API_KEY')
  .then(videos => console.log(videos));
```

## 🔥 cURL Commands

### YouTube Comment Scraper
```bash
curl -X POST "https://api.apify.com/v2/acts/akash9078~youtube-video-comment-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "maxComments": 50,
    "videoLink": "https://youtu.be/dQw4w9WgXcQ"
  }'
```

### YouTube Channel Video Scraper
```bash
curl -X POST "https://api.apify.com/v2/acts/akash9078~youtube-channel-video-scraper/run-sync-get-dataset-items?token=<YOUR_APIFY_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "channelUrl": "https://www.youtube.com/@pewdiepie",
    "includeMetadata": true
  }'
```

### YouTube Transcript Scraper
```bash
curl -X POST "https://api.apify.com/v2/acts/akash9078~youtube-transcript-extractor-pro/run-sync-get-dataset-items?token=<YOUR_APIFY_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "videoUrl": "https://youtu.be/1z1IcvZ-pvA"
  }'
```

### Indian Stock Data Scraper
```bash
curl -X POST "https://api.apify.com/v2/acts/akash9078~indian-stocks-financial-ratios-api/run-sync-get-dataset-items?token=<YOUR_APIFY_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "symbol": "tcs"
  }'
```

### Website Screenshot Generator
```bash
curl -X POST "https://api.apify.com/v2/acts/akash9078~full-website-screenshot-generator/run-sync-get-dataset-items?token=<YOUR_APIFY_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "url": "https://github.com",
    "fullPage": true
  }'
```

## 🔄 n8n Workflow Setup

### Import the Workflow

1. Copy the provided n8n workflow JSON
2. Open your n8n instance
3. Click **Import from File** or **Import from Clipboard**
4. Paste the workflow configuration
5. Replace `<enter your apify api key here>` with your actual API key
6. Save and activate the workflow

### Workflow Structure

The n8n workflow includes:
- **5 HTTP Request nodes** for different scrapers
- **Pre-configured endpoints** and parameters
- **Sticky note** with API key instructions

### Customization

Modify the `jsonBody` parameters in each HTTP Request node:

```json
{
  "maxComments": 100,
  "videoLink": "YOUR_VIDEO_URL"
}
```

## ⚡ Rate Limits & Best Practices

### Apify Rate Limits
- **Free Plan:** 10,000 API calls/month
- **Personal Plan:** 100,000 API calls/month
- **Team Plan:** 1,000,000 API calls/month

### Best Practices

1. **Implement retry logic** for failed requests
2. **Cache results** when possible to avoid duplicate calls
3. **Use appropriate delays** between requests
4. **Monitor your usage** in the Apify dashboard
5. **Handle errors gracefully** in your applications

### Error Handling Example

```python
import time
import requests
from requests.adapters import HTTPAdapter
from urllib3.util.retry import Retry

def make_robust_request(url, payload, max_retries=3):
    session = requests.Session()
    retry_strategy = Retry(
        total=max_retries,
        backoff_factor=1,
        status_forcelist=[429, 500, 502, 503, 504],
    )
    adapter = HTTPAdapter(max_retries=retry_strategy)
    session.mount("http://", adapter)
    session.mount("https://", adapter)
    
    try:
        response = session.post(url, json=payload, timeout=30)
        response.raise_for_status()
        return response.json()
    except requests.exceptions.RequestException as e:
        print(f"Request failed: {e}")
        return None
```

## 🐛 Troubleshooting

### Common Issues

#### 1. Invalid API Key
**Error:** `401 Unauthorized`
**Solution:** Check your API key and ensure it's correctly formatted

#### 2. Rate Limit Exceeded
**Error:** `429 Too Many Requests`
**Solution:** Wait before making new requests or upgrade your Apify plan

#### 3. Invalid Video URL
**Error:** `400 Bad Request`
**Solution:** Ensure YouTube URLs are in the correct format:
- ✅ `https://youtu.be/VIDEO_ID`
- ✅ `https://www.youtube.com/watch?v=VIDEO_ID`
- ❌ `youtube.com/VIDEO_ID`

#### 4. Timeout Errors
**Error:** `408 Request Timeout`
**Solution:** Increase timeout values or retry the request

### Debug Mode

Enable debug mode by adding `debug: true` to your request payload:

```json
{
  "videoLink": "https://youtu.be/5kcaHAuGxmY",
  "maxComments": 10,
  "debug": true
}
```

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/youtube-scrapers-collection.git

# Navigate to directory
cd youtube-scrapers-collection

# Install dependencies (if any)
npm install

# Set up your API key
export APIFY_API_KEY="your_api_key_here"
```

## 📈 Use Cases

- **Content Analysis:** Analyze YouTube comments for sentiment analysis
- **Channel Research:** Monitor competitor channels and video performance
- **Academic Research:** Extract video transcripts for text analysis
- **Financial Analysis:** Track Indian stock market data
- **Web Monitoring:** Generate website screenshots for monitoring changes
- **SEO Research:** Analyze YouTube video performance and engagement

## 🔐 Security Notes

- **Never commit API keys** to version control
- **Use environment variables** for sensitive data
- **Implement proper authentication** in production applications
- **Monitor API usage** regularly to detect unusual activity

## 📊 Performance Tips

1. **Batch requests** when possible
2. **Use webhooks** for long-running scraping tasks
3. **Implement caching** to reduce API calls
4. **Optimize request parameters** to get only needed data
5. **Use Apify's dataset API** for large data processing

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



## 🌟 Acknowledgments

- [Apify](https://apify.com) for providing robust scraping infrastructure
- [n8n](https://n8n.io) for workflow automation capabilities
- The open-source community for continuous inspiration

---

<div align="center">

**⭐ Star this repository if you found it helpful!**

[Get Apify API Key](https://apify.com?fpr=12vqj) | [View Documentation](https://docs.apify.com) | [Report Issues](https://github.com/yourusername/youtube-scrapers-collection/issues)

</div>
