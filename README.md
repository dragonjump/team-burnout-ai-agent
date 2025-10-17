# AI Burnout Detector - Team Wellness Analysis

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)

🤖 **Automated AI-powered team wellness monitoring** that analyzes developer activity patterns to detect early signs of burnout and team stress.

## 🎯 What It Does

The AI Burnout Detector is a GitHub Actions workflow that automatically:

- 📊 **Analyzes commit patterns** (late-night work, weekend activity)
- 🔍 **Tracks workflow failures** and development velocity
- 🧠 **Uses AI** (Groq API) to assess team wellness and burnout risk
- 📧 **Sends alerts** via GitHub issues and email reports
- 📈 **Provides actionable recommendations** for team health

## 🚀 How It Works

### 1. **Automatic Triggering**
- Runs on every **pull request** (opened, synchronized, reopened)
- Can be manually triggered via `workflow_dispatch`

### 2. **Data Collection**
- Fetches GitHub API data (commits, PRs, workflow runs)
- Analyzes patterns over configurable time periods (default: 7 days)

### 3. **AI Analysis**
- Uses **Groq API** with Llama3-8B model for fast, cost-effective analysis
- Generates burnout risk assessment (Low/Medium/High)
- Provides team health score (0-100)
- Identifies specific risk indicators

### 4. **Automated Actions**
- Creates GitHub issues with wellness alerts
- Sends email reports to team leads
- Uploads detailed analysis artifacts

## ⚡ Quick Setup

### 1. **Get Groq API Key**
```bash
# Visit https://console.groq.com/
# Sign up and create an API key
```

### 2. **Add GitHub Secret**
```bash
# Go to: Repository Settings → Secrets and variables → Actions
# Add secret: GROQ_API_KEY = your_groq_api_key
```

### 3. **Configure Email (Optional)**
```bash
# Add secret: EMAIL_RECIPIENT = team-leads@yourcompany.com
```

### 4. **Test It**
- Create a test pull request
- Check the Actions tab for execution
- Look for created issues and reports

## 🔧 Configuration

### Environment Variables
```yaml
ANALYSIS_PERIOD: 7          # Days to analyze (default: 7)
EMAIL_RECIPIENT: team@...   # Email for reports
GROQ_API_KEY: gsk_...       # Your Groq API key
```

### Available Groq Models
```javascript
model: 'llama3-8b-8192',        // Fastest (default)
model: 'mixtral-8x7b-32768',    // More capable
model: 'gemma2-9b-it',          // Google's model
```

## 📊 Sample Output

### GitHub Issue Alert
```
🚨 CRITICAL: Team Wellness Alert - your-org/repo

Team Health Score: 45/100
Burnout Risk: High
Confidence: 85%

Key Metrics:
- Late Night Work: 23 commits (67%)
- Weekend Work: 15 commits (44%)
- Failed Workflows: 8 (25%)

Risk Indicators:
- Excessive late-night coding patterns
- High weekend work frequency
- Increased workflow failures

Recommendations:
- Implement flexible work hours
- Schedule team wellness check-ins
- Consider workload redistribution
```

## 💰 Cost Analysis

**Groq API Pricing:**
- ~$0.27 per 1M tokens
- Typical analysis: 2-5K tokens per run
- **Cost per analysis: ~$0.001** (less than 1 cent!)

## 🛠️ Technical Details

### Workflow Structure
```yaml
on:
  pull_request: [opened, synchronize, reopened]
  workflow_dispatch:  # Manual trigger
```

### Key Steps
1. **Fetch GitHub Data** - Commits, PRs, workflows
2. **Pattern Analysis** - Calculate metrics and rates
3. **AI Analysis** - Groq-powered wellness assessment
4. **Create Alerts** - GitHub issues and email reports
5. **Upload Artifacts** - Detailed analysis files

### Dependencies
- `axios` - HTTP requests
- `groq-sdk` - AI analysis
- GitHub Actions built-in tools

## 📁 Repository Structure

This repository also contains ADK sample agents for reference:

```bash
├── .github/workflows/
│   └── devex-ai-burnout-detector.yml  # Main workflow
├── python/agents/                     # ADK Python samples
├── java/agents/                       # ADK Java samples
└── GROQ_SETUP.md                      # Detailed setup guide
```

> **Note**: This repository includes samples from the [Agent Development Kit (ADK)](https://google.github.io/adk-docs/), but the main focus is the AI Burnout Detector workflow.

## 🔍 Monitoring & Alerts

### Health Score Ranges
- **🟢 70-100**: Healthy team patterns
- **🟡 50-69**: Warning signs detected
- **🔴 0-49**: Critical burnout risk

### Alert Types
- **INFO**: Regular wellness updates
- **WARNING**: Moderate risk indicators
- **CRITICAL**: High burnout risk detected

## 🤝 Contributing

Found a bug or want to improve the detector? 

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

Apache 2.0 License - see [LICENSE](LICENSE) for details.

## ⚠️ Disclaimer

This tool is designed to help teams monitor wellness patterns, not to make personal judgments about individual developers. Always use the insights responsibly and focus on systemic improvements rather than individual performance reviews.

---

**Ready to protect your team's wellness?** 🚀 Set up the AI Burnout Detector in minutes and start getting automated insights into your team's health patterns!