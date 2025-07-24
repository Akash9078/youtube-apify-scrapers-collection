# 🚀 YouTube & Web Scrapers Collection

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Apify](https://img.shields.io/badge/Powered%20by-Apify-blue)](https://www.apify.com?fpr=12vqj)
[![n8n](https://img.shields.io/badge/Built%20with-n8n-FF6D6D)](https://n8n.partnerlinks.io/j9dphm7sk1hk)

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

1. Download the workflow JSON from [n8n-workflow.json](https://drive.google.com/file/d/1Y8_QJdG_GtViUeOMrCDyhw9YCoZCgORo/view?usp=drive_link)
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

## 📈 Use Cases

- **Content Analysis:** Analyze YouTube comments for sentiment analysis
- **Channel Research:** Monitor competitor channels and video performance
- **Academic Research:** Extract video transcripts for text analysis
- **Financial Analysis:** Track Indian stock market data
- **Web Monitoring:** Generate website screenshots for monitoring changes
- **SEO Research:** Analyze YouTube video performance and engagement

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



## 🌟 Acknowledgments

- [Apify](https://www.apify.com?fpr=12vqj) for providing robust scraping infrastructure
- [n8n](https://n8n.partnerlinks.io/j9dphm7sk1hk) for workflow automation capabilities
- The open-source community for continuous inspiration

---

<div align="center">

**⭐ Star this repository if you found it helpful!**

[Get Apify API Key](https://apify.com?fpr=12vqj) | [View Documentation](https://docs.apify.com) | [Report Issues](https://github.com/yourusername/youtube-scrapers-collection/issues)

</div>
