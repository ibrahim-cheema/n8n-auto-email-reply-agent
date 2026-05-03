Gmail Auto-Responder Workflow for n8n
This n8n workflow automatically processes incoming Gmail emails, classifies them into categories (Order/Inquiry), and generates appropriate draft replies using OpenAI's GPT-4o-mini model.

🚀 Features
Gmail Integration: Triggers on new incoming emails (polling every minute)

Text Classification: Automatically categorizes emails as "Order" or "Inquiry"

AI-Powered Responses: Generates professional, context-aware draft replies

Draft Creation: Saves AI-generated responses as drafts in Gmail for review

📋 Prerequisites
n8n instance (self-hosted or cloud)

Gmail account with OAuth2 credentials

OpenAI API key (the workflow uses n8n's free OpenAI credits by default)

🔧 Required Credentials
Credential Type	Name in Workflow	Purpose
Gmail OAuth2	Gmail OAuth2 API	Access Gmail to read emails and create drafts
OpenAI API	n8n free OpenAI API credits	Generate AI-powered email responses
🔄 Workflow Overview
text
Gmail Trigger → Text Classifier → (Branch based on classification)
                                    ├─ Order → Message a model → Create draft
                                    └─ Inquiry → Message a model1 → Create draft1
📁 Nodes Explained
1. Gmail Trigger
Type: gmailTrigger

Function: Polls Gmail every minute for new emails

Output: Email snippet and metadata

2. Text Classifier
Type: textClassifier (LangChain)

Categories:

Order - Emails about new orders or purchases

Inquiry - Customer questions or general inquiries

Input: Email snippet from Gmail trigger

Output: Category classification

3. OpenAI Chat Model
Model: gpt-4o-mini

Purpose: Supports the text classifier for accurate categorization

4. Message a model (Order branch)
Model: gpt-4o-mini

Task: Generate professional reply for order-related emails

Output Format:

text
Subject: [Original Subject]
Body: [Generated response]
5. Message a model1 (Inquiry branch)
Model: gpt-4o-mini

Task: Generate professional reply for inquiry emails

Output Format: Same as order branch

6. Create a draft / Create a draft1
Type: gmail (draft resource)

Function: Creates email drafts using AI-generated responses

⚙️ Configuration Options
Gmail Trigger
Modify pollTimes to change checking frequency:

everyMinute (default)

everyHour

everyDay

Custom intervals

Text Classifier
Add or modify categories in the categories array:

json
{
  "category": "Support",
  "description": "Technical support requests"
}
AI Response Guidelines
Edit the prompt template in each "Message a model" node:

Adjust tone (professional, casual, formal)

Add specific business context

Modify output format requirements

🚦 Workflow Status
The workflow is currently INACTIVE ("active": false). To activate:

Import the workflow into n8n

Configure the required credentials

Click the "Active" toggle in the n8n UI

📝 Usage Notes
All generated replies are saved as drafts, not sent automatically

Review drafts in Gmail before sending

The workflow uses branch splitting based on classification results

Both classification paths currently use identical AI prompts (customize as needed)

🛠️ Customization Ideas
Add more categories: Extend the text classifier for support, feedback, spam, etc.

Different response strategies: Customize prompts per category

Auto-send option: Modify the Gmail node from "draft" to "send"

Add fallback branch: Handle unclassified emails differently

Webhook notification: Alert someone when high-priority emails arrive

⚠️ Limitations
Polling-based (not real-time webhook)

Requires manual draft review before sending

Free OpenAI credits may have usage limits

📄 License
This workflow configuration is provided as-is for personal or commercial use.

