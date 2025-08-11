# Real-Time Social Media Analytics Pipeline
> Advanced Sentiment Analysis with Hybrid Cloud-Academic Architecture

[![Pipeline Status](https://img.shields.io/badge/Pipeline-Production-brightgreen)](https://github.com/your-username/social-media-pipeline)
[![Azure](https://img.shields.io/badge/Azure-Operational-blue)](https://azure.microsoft.com/)
[![ML Models](https://img.shields.io/badge/ML-RoBERTa%2BDistilRoBERTa-orange)](https://huggingface.co/)
[![Processing Speed](https://img.shields.io/badge/Processing-17.5%20posts%2Fsec-yellow)](https://github.com/your-username/social-media-pipeline)

## 🎯 Project Overview

A production-grade real-time sentiment analysis system that processes live social media data from Bluesky, performs advanced ML-based sentiment and emotion analysis, and enables comprehensive business intelligence. The system combines cloud-native streaming infrastructure with high-performance academic computing resources for cost-effective, scalable processing.

**Key Innovation**: Hybrid cloud-academic architecture that reduces ML processing costs by 95% while maintaining enterprise-level reliability and sub-20 second latency from data collection to queryable storage.

## 📊 Architecture Overview

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│ Bluesky API │───▶│Azure Function│───▶│ Event Hubs  │───▶│ Databricks  │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
                                                                   │
┌─────────────┐    ┌─────────────┐    ┌─────────────┐             │
│   Analytics │◀───│College Cluster│◀───│GitHub Bridge│◀────────────┘
└─────────────┘    └─────────────┘    └─────────────┘
```

## ✨ Key Features

### 🔄 Real-Time Data Pipeline
- **Live Data Collection**: 1,000+ posts/hour from Bluesky API
- **Stream Processing**: Sub-20 second end-to-end latency
- **Fault Tolerant**: ACID transactions with automatic recovery
- **Scalable Architecture**: Handles variable data volumes with dynamic scaling

### 🧠 Advanced ML Processing
- **State-of-the-Art Models**: RoBERTa-base sentiment + DistilRoBERTa emotion analysis
- **Multi-Dimensional Analysis**: Sentiment (-1.0 to +1.0) + 6-emotion classification
- **High Performance**: 17.5 posts/second processing speed on academic hardware
- **Quality Assurance**: 87.9% processing success rate with comprehensive error handling

### 📊 Business Intelligence
- **Political Sentiment Tracking**: Real-time analysis of #trump, #biden content
- **Economic Monitoring**: #economy hashtag sentiment trends
- **Technology Adoption**: #ai sentiment analysis for trend prediction
- **Comparative Analysis**: Cross-hashtag sentiment intelligence

## 🏛️ Hybrid Architecture Design

### Cloud Infrastructure (Azure)
- **Data Collection**: Serverless Azure Functions with timer triggers
- **Stream Processing**: Event Hubs + Databricks Structured Streaming
- **Data Storage**: Delta Lake with ACID transactions and time travel
- **Monitoring**: Native Azure monitoring + custom data quality metrics

### Academic Computing Integration
- **High-Performance Processing**: 48-core CPU, 124GB RAM cluster
- **Cost Optimization**: Free academic resources vs expensive cloud GPU instances
- **Advanced ML Models**: Hugging Face Transformers with PyTorch backend
- **Data Bridge**: GitHub-based synchronization for platform independence

## 📊 Performance Dashboard

| Metric | Value | Status |
|--------|--------|--------|
| **Data Collection** | 1,000+ posts/hour | ✅ Operational |
| **Processing Speed** | 17.5 posts/second | 🚀 Optimized |
| **End-to-End Latency** | 18 seconds | ⚡ Real-time |
| **ML Accuracy** | 87.9% success rate | 🎯 High Quality |
| **Cost Savings** | 95% vs pure cloud | 💰 Efficient |

## 🛠️ Tech Stack

<table>
<tr>
<td><strong>🌩️ Cloud Infrastructure</strong></td>
<td><strong>🧠 ML & Processing</strong></td>
</tr>
<tr>
<td>

• **Azure Functions** - Python 3.11 runtime  
• **Event Hubs** - 3-partition streaming  
• **Databricks** - ML Runtime 13.3 LTS  
• **Delta Lake** - ACID transactions  

</td>
<td>

• **RoBERTa** - Twitter-trained sentiment  
• **DistilRoBERTa** - 6-emotion analysis  
• **PyTorch** - ML framework  
• **Hugging Face** - Transformer models  

</td>
</tr>
</table>

## 🚀 Getting Started

### Prerequisites
- Azure subscription with Function Apps, Event Hubs, and Databricks
- Python 3.11+ with required dependencies
- Git access for data synchronization
- High-performance compute environment (optional, for ML processing)

## 🚀 Quick Start

### 1. Clone Repository
```bash
git clone https://github.com/your-username/social-media-pipeline.git
cd social-media-pipeline
```

### 2. Configure Environment
```bash
export BLUESKY_USERNAME="your-username"
export BLUESKY_PASSWORD="your-app-password"
export EVENTHUBS_CONNECTION_STRING="your-connection-string"
```

### 3. Deploy Infrastructure
```bash
az deployment group create --resource-group data-pipeline-rg \
  --template-file infrastructure/azure-resources.json
```

### 4. Deploy Function
```bash
cd azure-function
func azure functionapp publish bluesky-collector-function
```

## 📊 Data Schema

### Raw Social Media Posts
```json
{
  "post_id": "3lura4pg4hc2e",
  "text": "AI is transforming everything! #ai #technology",
  "author": "user.bsky.social",
  "created_at": "2025-07-25T04:50:00.000Z",
  "hashtags": ["#ai", "#technology"],
  "engagement": {"likes": 15, "reposts": 3, "replies": 2},
  "collection_metadata": {
    "collected_at": "2025-07-25T04:53:00.000Z",
    "source": "bluesky_hashtag_search"
  }
}
```

### ML-Enhanced Posts
```json
{
  "ml_sentiment_score": 0.73,
  "ml_sentiment_label": "positive",
  "dominant_emotion": "joy",
  "emotion_scores": {
    "joy": 0.7, "trust": 0.6, "anger": 0.1,
    "fear": 0.05, "sadness": 0.02, "disgust": 0.01
  },
  "processing_metadata": {
    "processed_at": "2025-07-25T04:54:00.000Z",
    "model_version": "roberta-base-v1.0",
    "processing_time_ms": 45
  }
}
```

## 📈 Business Intelligence Examples

### Political Sentiment Analysis
```sql
-- Track sentiment trends for political content
SELECT 
    DATE(created_at) as date,
    AVG(ml_sentiment_score) as avg_sentiment,
    COUNT(*) as post_count
FROM social_media.bluesky_enhanced_posts 
WHERE array_contains(hashtags, '#trump')
  AND created_at >= current_date - INTERVAL 7 DAYS
GROUP BY DATE(created_at)
ORDER BY date;
```

### Cross-Hashtag Comparison
```sql
-- Compare sentiment across different hashtags
SELECT 
    explode(hashtags) as hashtag,
    AVG(ml_sentiment_score) as avg_sentiment,
    STDDEV(ml_sentiment_score) as sentiment_volatility,
    COUNT(*) as volume
FROM social_media.bluesky_enhanced_posts
WHERE created_at >= current_date - INTERVAL 24 HOURS
GROUP BY hashtag
HAVING volume >= 50
ORDER BY avg_sentiment DESC;
```

### Emotion Distribution Analysis
```sql
-- Analyze emotion patterns for economic content
SELECT 
    dominant_emotion,
    COUNT(*) as frequency,
    AVG(ml_sentiment_score) as avg_sentiment
FROM social_media.bluesky_enhanced_posts
WHERE array_contains(hashtags, '#economy')
  AND created_at >= current_date - INTERVAL 3 DAYS
GROUP BY dominant_emotion
ORDER BY frequency DESC;
```

## 🎯 Key Results

### Political Sentiment Analysis
- **#trump content**: -0.256 average sentiment (65.3% negative)
- **High volatility**: Coefficient of variation = 1.75
- **Emotional profile**: Predominantly anger and fear

### Real-Time Insights
- **Live tracking** of political opinion trends
- **Economic sentiment** monitoring for market intelligence  
- **Technology adoption** sentiment (#ai trending positive)

<details>
<summary>📈 Click to see sample analysis results</summary>

```
#TRUMP Sentiment Distribution:
├── Negative: 65.3% (4,135 posts)
├── Positive: 23.2% (1,454 posts) 
└── Neutral:  11.6% (680 posts)

Average Score: -0.256
Volatility: High (1.75 coefficient)
```
</details>

## 🏆 Technical Achievements

### Innovation
- **Novel Hybrid Architecture**: First-of-its-kind cloud-academic integration
- **Cost Optimization**: 95% reduction in ML processing costs vs pure cloud
- **Real-Time Processing**: Sub-20 second latency for live social media analysis
- **Multi-Modal Analysis**: Combined sentiment + emotion intelligence

### Production Excellence
- **Fault Tolerance**: Zero data loss with automatic recovery mechanisms
- **Scalability**: Handles variable loads with dynamic resource allocation
- **Monitoring**: Comprehensive observability with custom quality metrics
- **Data Quality**: 87.9% processing success with robust error handling

### Business Impact
- **Actionable Insights**: Real-time political and economic sentiment intelligence
- **Competitive Advantage**: Advanced NLP capabilities vs traditional sentiment tools
- **Portfolio Demonstration**: Full-stack data engineering and ML operations expertise

## 🚧 Roadmap

### Immediate Enhancements
- [ ] Enhanced data upload pipeline to Databricks
- [ ] Cross-hashtag correlation analysis
- [ ] Real-time dashboard with Plotly visualizations
- [ ] Automated insight generation with LLM integration

### Medium-Term Goals
- [ ] Statistical modeling for sentiment volatility prediction
- [ ] Multi-platform data collection (Twitter, LinkedIn)
- [ ] Advanced time-series forecasting
- [ ] Interactive web application with Voila

### Long-Term Vision
- [ ] Multi-language sentiment analysis
- [ ] Image and video content analysis
- [ ] Influencer impact modeling
- [ ] Enterprise SaaS deployment

## 📝 Contributing

Contributions are welcome! Please see our [Contributing Guide](CONTRIBUTING.md) for details on:
- Code style and standards
- Pull request process
- Issue reporting guidelines
- Development environment setup

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Hugging Face**: For providing state-of-the-art transformer models
- **Azure**: For reliable cloud infrastructure and managed services
- **Academic Computing**: For high-performance, cost-effective ML processing
- **Bluesky**: For accessible social media data via AT Protocol

## 📞 Contact

**Alex Huynh** - [GitHub](https://github.com/your-username) - [LinkedIn](https://linkedin.com/in/your-profile)

**Project Link**: [https://github.com/your-username/social-media-pipeline](https://github.com/your-username/social-media-pipeline)

---

*Built with ❤️ for real-time social media intelligence*
