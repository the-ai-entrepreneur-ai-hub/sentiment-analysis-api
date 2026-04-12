# Sentiment Analysis API

Analyze text sentiment instantly. Returns positive, negative, or neutral with a confidence score. No external AI costs. Runs entirely on a built in word lexicon.

## What you get

- Sentiment label: positive, negative, or neutral
- Score from -1 (very negative) to +1 (very positive)
- Confidence score (0 to 1)
- List of positive and negative words found
- Negation detection ("not good" correctly scores as negative)

## Who uses this

- Brand monitoring teams analyzing thousands of mentions
- Review analysis pipelines processing customer feedback
- Social media monitoring checking sentiment trends
- Content teams auditing tone before publishing
- Research projects analyzing public discourse

## API (Standby Mode)

Instant response, no cold start.

### Analyze text (GET)

```
GET /analyze?text=I love this product it is amazing
```

### Analyze text (POST, for longer text)

```
POST /analyze
Content-Type: application/json

{"text": "The customer service was terrible and nobody helped me resolve the issue"}
```

### Response

```json
{
  "text": "I love this product it is amazing",
  "sentiment": "positive",
  "score": 0.7,
  "confidence": 0.85,
  "details": {
    "wordCount": 8,
    "matchedWords": 2,
    "positiveWords": ["love", "amazing"],
    "negativeWords": [],
    "totalScore": 7,
    "averageScore": 3.5
  },
  "analyzedAt": "2026-04-12T15:00:00Z"
}
```

### Health check

```
GET /health
```

## How it works

Uses a lexicon of 200+ sentiment scored words (based on the AFINN word list, public domain). Each word has a score from -5 (strongly negative) to +5 (strongly positive). The analyzer tokenizes your text, looks up each word, handles negation ("not good" flips the score), and returns an aggregate result.

No external API calls. No LLM costs. Pure algorithmic analysis. This means every request costs fractions of a cent to run.

## Pricing

$0.003 per text analyzed. No subscriptions.

1,000 analyses = $3.00. Run it on your entire review database for less than a cup of coffee.

## Pairs well with

- [Reddit Brand Monitor](https://apify.com/george.the.developer/reddit-scraper-pro) for analyzing Reddit comment sentiment
- [Google News Alert](https://apify.com/george.the.developer/google-news-monitor) for news sentiment tracking
- [Telegram Channel Monitor](https://apify.com/george.the.developer/telegram-channel-scraper) for community sentiment analysis

## Built by George Kioko

50 actors on Apify, 869+ users. More at https://apify.com/george.the.developer
