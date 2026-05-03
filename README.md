📧 Gmail Auto-Responder Workflow for n8n

This n8n workflow automatically processes incoming Gmail emails, classifies them into categories (Order / Inquiry), and generates appropriate draft replies using OpenAI's GPT-4o-mini model.

🚀 Features
Gmail Integration
Triggers on new incoming emails (polling every minute)
Text Classification
Automatically categorizes emails as:
Order
Inquiry
AI-Powered Responses
Generates professional, context-aware draft replies
Draft Creation
Saves AI-generated responses as drafts in Gmail for review
📋 Prerequisites
n8n instance (self-hosted or cloud)
Gmail account with OAuth2 credentials
OpenAI API key (or n8n free OpenAI credits)
🔧 Required Credentials
Credential Type	Name in Workflow	Purpose
Gmail OAuth2	Gmail OAuth2 API	Access Gmail to read emails & create drafts
OpenAI API	n8n OpenAI credentials	Generate AI-powered responses
🔄 Workflow Overview
Gmail Trigger → Text Classifier → (Branch based on classification)
                                    ├─ Order → Message a model → Create draft
                                    └─ Inquiry → Message a model1 → Create draft1
📁 Nodes Explained
1. Gmail Trigger
Type: gmailTrigger
Function: Polls Gmail every minute for new emails
Output: Email snippet + metadata
2. Text Classifier
Type: textClassifier (LangChain)
Input: Email snippet from Gmail
Output: Category classification

Categories:

Order → Emails about purchases/orders
Inquiry → Questions or general inquiries
3. OpenAI Chat Model
Model: gpt-4o-mini
Purpose: Supports classification accuracy
4. Message a Model (Order Branch)
Model: gpt-4o-mini
Task: Generate replies for order-related emails

Output Format:

Subject: [Original Subject]
Body: [Generated response]
5. Message a Model1 (Inquiry Branch)
Same configuration as Order branch
Handles inquiry-based emails
6. Create a Draft / Create a Draft1
Type: Gmail (Draft)
Function: Saves AI-generated responses as drafts
⚙️ Configuration Options
Gmail Trigger

Modify polling frequency:

everyMinute (default)
everyHour
everyDay
Custom intervals
Text Classifier

Add new categories:

{
  "category": "Support",
  "description": "Technical support requests"
}
AI Response Customization

Edit prompts inside "Message a model" nodes:

Adjust tone (formal, casual, professional)
Add business-specific context
Change response format
🚦 Workflow Status

⚠️ The workflow is currently INACTIVE ("active": false)

To Activate:
Import workflow into n8n
Configure credentials
Enable using the "Active" toggle
📝 Usage Notes
Replies are saved as drafts only (not auto-sent)
Always review before sending
Uses branching logic based on classification
Both branches currently use similar prompts (customize recommended)
🛠️ Customization Ideas
➕ Add more categories (Support, Feedback, Spam)
🎯 Customize replies per category
📤 Enable auto-send (replace draft node with send node)
⚠️ Add fallback for unclassified emails
🔔 Integrate webhook notifications for important emails
⚠️ Limitations
Polling-based (not real-time)
Requires manual review before sending
OpenAI free credits may be limited
📄 License

This workflow is provided as-is for personal and commercial use.
