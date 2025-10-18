# Groq API Setup for AI Burnout Detector

## 🔧 Required Configuration

### 1. GitHub Secrets Setup
 
Go to your repository → Settings → Secrets and variables → Actions, then add:

#### Required Secrets:
- **`GROQ_API_KEY`** - Your Groq API key from https://console.groq.com/

#### Optional Secrets (for email notifications):
- **`EMAIL_SERVICE_API_KEY`** - If you want to send real emails (SendGrid, AWS SES, etc.)
- **`EMAIL_FROM_ADDRESS`** - Sender email address
 
### 2. Groq API Key Setup

1. Visit [Groq Console](https://console.groq.com/)
2. Sign up/Login to your account
3. Navigate to API Keys section
4. Create a new API key
5. Copy the key and add it to GitHub Secrets as `GROQ_API_KEY`

### 3. Repository Variables (Optional)

Go to Settings → Secrets and variables → Actions → Variables tab:

- **`DEFAULT_EMAIL_RECIPIENT`** - Default email for reports (e.g., `team-leads@yourcompany.com`)
- **`ANALYSIS_PERIOD_DAYS`** - Default analysis period (e.g., `7`)

### 4. Workflow Configuration

The workflow is now configured to:

- ✅ Run on every pull request (opened, synchronized, reopened)
- ✅ Use Groq API with Llama3-8B model (fast and cost-effective)
- ✅ Analyze team wellness patterns
- ✅ Create GitHub issues for alerts
- ✅ Generate email reports
- ✅ Upload analysis artifacts

### 5. Available Groq Models

The workflow uses `llama3-8b-8192` by default. You can change it in the workflow file:

```javascript
model: 'llama3-8b-8192',        // Fastest, good for analysis
// model: 'mixtral-8x7b-32768', // More capable
// model: 'gemma2-9b-it',        // Google's model on Groq
```

### 6. Testing the Setup

1. Create a test pull request
2. The workflow should automatically trigger
3. Check the Actions tab for execution logs
4. Look for created issues and uploaded artifacts

### 7. Cost Considerations

Groq API pricing (as of 2024):
- **Llama3-8B**: ~$0.27 per 1M tokens
- **Mixtral-8x7B**: ~$0.27 per 1M tokens  
- **Gemma2-9B**: ~$0.27 per 1M tokens

Typical analysis uses ~2-5K tokens per run, so cost is minimal.

### 8. Troubleshooting

#### Common Issues:

1. **"No Groq API key provided"**
   - Check that `GROQ_API_KEY` secret is properly set
   - Verify the secret name matches exactly

2. **"Analysis failed - using fallback"**
   - Check Groq API key validity
   - Verify network connectivity
   - Check Groq service status

3. **Workflow not triggering**
   - Ensure workflow file is in `.github/workflows/` directory
   - Check that pull request events are enabled
   - Verify repository permissions

### 9. Customization

#### Change Analysis Period:
```yaml
env:
  ANALYSIS_PERIOD: ${{ inputs.analysis_period || '14' }}  # Change default from 7 to 14 days
```

#### Change Email Recipients:
```yaml
env:
  EMAIL_RECIPIENT: ${{ inputs.email_recipient || 'your-team@company.com' }}
```

#### Modify AI Model:
Edit the model name in the Groq API call:
```javascript
model: 'mixtral-8x7b-32768',  // More capable model
```

---

## 🚀 Ready to Use!

Once you've set up the `GROQ_API_KEY` secret, the workflow will automatically:
- Analyze team wellness on every PR
- Generate AI-powered burnout risk assessments
- Create GitHub issues for alerts
- Send email notifications
- Upload detailed analysis reports

The system is now faster, more cost-effective, and ready for production use!
