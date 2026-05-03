# Gmail-Auto-Responder-Workflow-n8n

This project is an automated email response system built using n8n. It monitors incoming Gmail messages, classifies them into categories such as Order or Inquiry, and generates professional draft replies using the GPT-4o-mini model. The workflow helps streamline email handling while keeping human review in control.

## Project Focus

The goal of this project is to demonstrate how AI and automation can be combined to handle repetitive communication tasks. It focuses on workflow automation, text classification, and AI-generated responses while maintaining a simple and scalable structure inside n8n.

## Requirements

1. **Email Monitoring**: Use Gmail Trigger node to detect new incoming emails  
2. **Text Classification**: Classify emails into categories like Order and Inquiry  
3. **AI Response Generation**: Use GPT-4o-mini to generate context-aware replies  
4. **Draft Creation**: Save responses as Gmail drafts instead of sending automatically  
5. **Branching Logic**: Implement conditional paths based on classification results  
6. **Custom Prompts**: Allow modification of response tone and format  
7. **Scalability**: Support adding more categories such as Support or Feedback  

## Workflow Overview


## Nodes Description

### Gmail Trigger
- Polls Gmail every minute  
- Captures email snippet and metadata  

### Text Classifier
- Categorizes emails into predefined types  
- Uses AI-assisted classification  

### OpenAI Model
- Model: GPT-4o-mini  
- Generates responses based on email content  

### Message Nodes
- Create structured replies with subject and body  

### Draft Nodes
- Save generated replies as Gmail drafts  

## Configuration

### Gmail Setup
- Configure Gmail OAuth2 credentials  
- Connect Gmail account to n8n  

### OpenAI Setup
- Use API key or n8n built-in credits  

### Customization
- Modify prompts inside message nodes  
- Adjust tone (formal, casual, business)  
- Add new classification categories  

## Usage

1. Import the workflow into n8n  
2. Configure credentials (Gmail + OpenAI)  
3. Activate the workflow  
4. New emails will be processed automatically  
5. Review generated drafts in Gmail before sending  

## Output Format


## Customization Ideas

- Add more categories (Support, Complaints, Feedback)  
- Enable auto-send instead of drafts  
- Add notifications for high-priority emails  
- Improve classification with more detailed prompts  
- Integrate with CRM or databases  

## Limitations

- Uses polling instead of real-time triggers  
- Requires manual review before sending  
- AI responses depend on prompt quality  
- Free API credits may have limits  

## Installation

Make sure you have the following:

- n8n (self-hosted or cloud)  
- Gmail account with OAuth2 setup  
- OpenAI API key or n8n credits  

## License

This project is provided as-is for personal and commercial use.
