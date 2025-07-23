# Summary Prompt Configuration Guide

This guide explains how to modify the summary prompts used by the Ember app to generate session summaries. These prompts control how the AI creates summaries of therapy sessions.

## 📁 Configuration File

The summary prompts are configured in:
```
config/summary_prompts.json
```

## 🔧 What You Can Modify

### 1. System Prompt
This tells the AI how to behave when creating summaries:
```json
"systemPrompt": "You are a helpful assistant that creates comprehensive therapy session summaries. Focus on key themes and insights discussed. Do not use asterisks (*) anywhere in your response. Provide detailed analysis without character limits."
```

### 2. User Prompt Template
This is the instruction given to the AI for each summary:
```json
"userPromptTemplate": "Generate a comprehensive summary of this therapy session. Session details: {messageCount} messages over {duration} minutes. User messages: {userMessages}. Requirements: Focus on key themes and insights discussed. Do not mention the AI assistant or persona name. Do not use asterisks (*) anywhere in your response. Provide detailed analysis without character limits."
```

**Template Variables:**
- `{messageCount}` - Number of messages in the session
- `{duration}` - Session duration in minutes
- `{userMessages}` - Recent user messages from the session

### 3. Fallback Summary Template
Used when AI summary generation fails:
```json
"fallbackSummaryTemplate": "Session: {messageCount} messages over {duration} minutes. {recentMessages}"
```

### 4. AI Parameters
Control how the AI generates summaries:
```json
"parameters": {
  "temperature": 0.7,
  "maxTokens": 1000,
  "topP": 0.9
}
```

- **temperature**: Controls creativity (0.0 = very focused, 1.0 = very creative)
- **maxTokens**: Maximum length of the summary
- **topP**: Controls response diversity (0.0 = very focused, 1.0 = very diverse)

## 📝 Example Modifications

### Make Summaries More Concise
```json
{
  "summaryPrompts": {
    "systemPrompt": "You are a concise assistant that creates brief therapy session summaries. Focus on the most important themes and insights. Keep summaries under 200 words.",
    "userPromptTemplate": "Create a brief summary of this therapy session. Session details: {messageCount} messages over {duration} minutes. User messages: {userMessages}. Focus on key themes only. Keep it concise.",
    "parameters": {
      "temperature": 0.5,
      "maxTokens": 300,
      "topP": 0.8
    }
  }
}
```

### Make Summaries More Detailed
```json
{
  "summaryPrompts": {
    "systemPrompt": "You are a detailed assistant that creates comprehensive therapy session summaries. Include emotional themes, cognitive patterns, behavioral insights, and growth opportunities. Provide thorough analysis.",
    "userPromptTemplate": "Create a detailed summary of this therapy session. Session details: {messageCount} messages over {duration} minutes. User messages: {userMessages}. Include emotional themes, cognitive patterns, behavioral insights, and growth opportunities. Provide comprehensive analysis.",
    "parameters": {
      "temperature": 0.8,
      "maxTokens": 2000,
      "topP": 0.95
    }
  }
}
```

### Focus on Specific Themes
```json
{
  "summaryPrompts": {
    "systemPrompt": "You are a therapy session analyst focused on emotional processing and personal growth. Create summaries that highlight emotional themes, coping strategies, and progress made.",
    "userPromptTemplate": "Analyze this therapy session focusing on emotional processing and personal growth. Session details: {messageCount} messages over {duration} minutes. User messages: {userMessages}. Highlight emotional themes, coping strategies used, and progress made.",
    "parameters": {
      "temperature": 0.6,
      "maxTokens": 1500,
      "topP": 0.9
    }
  }
}
```

## 🚀 How to Apply Changes

1. **Edit the JSON file** using any text editor
2. **Save the file** with UTF-8 encoding
3. **Commit and push** to GitHub (reytran818/EmberApp)
4. **Launch the app** to see your changes
5. **Test by creating a session** and checking the summary

## ⚠️ Important Notes

### JSON Formatting
- Use double quotes `"` for all strings
- Separate items with commas `,`
- Don't forget closing braces `}`
- Validate JSON before committing

### Template Variables
- Always use the exact variable names: `{messageCount}`, `{duration}`, `{userMessages}`, `{recentMessages}`
- Variables are automatically replaced with actual values
- Don't change the variable names

### AI Parameters
- **temperature**: 0.0 to 1.0 (recommended: 0.5-0.8)
- **maxTokens**: 100 to 4000 (recommended: 500-2000)
- **topP**: 0.0 to 1.0 (recommended: 0.8-0.95)

## 🔍 Testing Your Changes

1. **Make a small change** to test the system
2. **Create a therapy session** in the app
3. **Check the session summary** in the Journey page
4. **Verify the changes** appear as expected

## 🛠️ Troubleshooting

### Summary Not Updating
- Check that JSON is valid (no syntax errors)
- Ensure file is saved with UTF-8 encoding
- Verify changes are committed to GitHub
- Restart the app completely

### AI Parameters Not Working
- Ensure parameter values are numbers (not strings)
- Check that values are within recommended ranges
- Verify JSON structure is correct

### Template Variables Not Replacing
- Check variable names are exactly correct
- Ensure variables are in the right template
- Verify JSON syntax is valid

## 📞 Need Help?

If you encounter issues:
1. Check the JSON syntax with an online validator
2. Compare your changes to the original file
3. Test with a simple change first
4. Contact the development team for assistance

## 🔄 Integration with Other Configs

This summary prompt configuration works alongside:
- **Base Prompts** (`config/base_prompts.json`) - General conversation prompts
- **Personas** (`config/personas.json`) - AI personality configurations
- **Psychology Insights** (`config/psychology_insights.json`) - Session analysis prompts

All configurations are loaded independently and can be modified separately. 