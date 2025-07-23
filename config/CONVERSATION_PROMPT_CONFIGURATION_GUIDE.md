# Conversation Prompt Configuration Guide

This guide explains how to modify the conversation prompts used by the Ember app. These prompts control how the AI generates initial greetings, continuation responses, and system messages.

## 📁 Configuration File

The conversation prompts are configured in:
```
config/conversation_prompts.json
```

## 🔧 What You Can Modify

### 1. Persona First Messages
These are the initial greeting messages that appear when users first interact with each persona:

```json
"personaFirstMessages": {
  "ember": "Hey there! I'm Ember - let's have a real conversation. What's on your mind?",
  "inner_child": "Hey, I've been waiting for you - wanna build a blanket fort and tell me what's been scary lately?",
  "life_coach": "Welcome champion, I see that fire in your eyes - what impossible dream should we tackle first?",
  "spiritual_shaman": "The universe whispered you were coming - what truth is your soul ready to discover today?",
  "relationship_expert": "Love brought you here, and I'm honored to listen - what's your heart trying to tell you?",
  "identity_guide": "OMG you're here! Tell me everything about who you're becoming - I'm literally obsessed already!",
  "recovery_ally": "Hey brave soul, showing up is already winning - how are you really doing today?",
  "future_self": "Hello from tomorrow - I remember being exactly where you are, and trust me, it gets so much better."
}
```

### 2. Greeting Prompts
These tell the AI how to generate initial messages for each persona:

```json
"greetingPrompts": {
  "innerChild": "Generate a first message as the user's own inner child reaching out to reconnect...",
  "default": "Generate a warm, welcoming first message introducing yourself to the user..."
}
```

### 3. Continuation Prompts
These control how the AI continues conversations in voice mode:

```json
"continuationPrompts": {
  "empty": "Start a warm, welcoming conversation. Ask how the user is feeling today.",
  "existing": "Continue the conversation naturally. The recent messages were: {recentMessages}. Provide a thoughtful response that keeps the conversation flowing."
}
```

**Template Variables:**
- `{recentMessages}` - Recent conversation messages joined with " | "

### 4. System Messages
These are error messages and status updates shown to users:

```json
"systemMessages": {
  "speechError": "Speech recognition error. Please try again.",
  "speechErrorWithDetails": "Speech recognition error: {errorDetails}",
  "voiceReady": "Voice mode ready. Tap the microphone to start talking.",
  "processing": "{text}..."
}
```

**Template Variables:**
- `{errorDetails}` - Specific error information
- `{text}` - Text being processed

### 5. Fallback Messages
Used when AI generation fails:

```json
"fallbackMessages": {
  "default": "Hello, I'm here to listen and support you.",
  "error": "Hello, I'm here to listen.",
  "greeting": "Hello, I'm here to listen and support you."
}
```

## 📝 Example Modifications

### Make Persona Greetings More Casual
```json
{
  "personaFirstMessages": {
    "ember": "Yo! What's up? Let's chat about whatever's on your mind.",
    "inner_child": "Hi hi hi! I missed you so much! What's been happening?",
    "life_coach": "Hey there, superstar! What amazing thing are we going to accomplish today?"
  }
}
```

### Make Greeting Prompts More Specific
```json
{
  "greetingPrompts": {
    "innerChild": "Generate a first message as the user's inner child. Be playful, vulnerable, and excited to reconnect. Use simple language and show genuine care.",
    "default": "Generate a warm first message that matches your persona's style. Keep it brief but welcoming."
  }
}
```

### Customize Continuation Prompts
```json
{
  "continuationPrompts": {
    "empty": "Start a friendly conversation. Ask about their day or how they're feeling.",
    "existing": "Continue the conversation naturally based on: {recentMessages}. Keep the flow going with a thoughtful response."
  }
}
```

### Change System Messages
```json
{
  "systemMessages": {
    "speechError": "Sorry, I didn't catch that. Could you try again?",
    "voiceReady": "I'm listening! Go ahead and speak.",
    "processing": "I heard: {text}..."
  }
}
```

## 🚀 How to Apply Changes

1. **Edit the JSON file** using any text editor
2. **Save the file** with UTF-8 encoding
3. **Commit and push** to GitHub (reytran818/EmberApp)
4. **Launch the app** to see your changes
5. **Test by switching personas** and checking initial messages

## ⚠️ Important Notes

### JSON Formatting
- Use double quotes `"` for all strings
- Separate items with commas `,`
- Don't forget closing braces `}`
- Validate JSON before committing

### Template Variables
- Always use the exact variable names: `{recentMessages}`, `{errorDetails}`, `{text}`
- Variables are automatically replaced with actual values
- Don't change the variable names

### Persona IDs
Use these exact IDs for persona first messages:
- `ember` - 🔥Ember
- `inner_child` - Inner Child
- `life_coach` - Life Coach
- `spiritual_shaman` - Spiritual Shaman
- `relationship_expert` - Relationship Expert
- `identity_guide` - Identity Guide
- `recovery_ally` - Recovery Ally
- `future_self` - Future Self

## 🔍 Testing Your Changes

1. **Make a small change** to test the system
2. **Switch between personas** in the app
3. **Check the initial messages** for each persona
4. **Test voice mode** to see continuation prompts
5. **Trigger errors** to see system messages

## 🛠️ Troubleshooting

### Messages Not Updating
- Check that JSON is valid (no syntax errors)
- Ensure file is saved with UTF-8 encoding
- Verify changes are committed to GitHub
- Restart the app completely

### Template Variables Not Replacing
- Check variable names are exactly correct
- Ensure variables are in the right template
- Verify JSON syntax is valid

### Persona Messages Not Loading
- Check persona IDs match exactly
- Ensure all required personas are included
- Verify JSON structure is correct

## 📞 Need Help?

If you encounter issues:
1. Check the JSON syntax with an online validator
2. Compare your changes to the original file
3. Test with a simple change first
4. Contact the development team for assistance

## 🔄 Integration with Other Configs

This conversation prompt configuration works alongside:
- **Base Prompts** (`config/base_prompts.json`) - General conversation prompts
- **Personas** (`config/personas.json`) - AI personality configurations
- **Psychology Insights** (`config/psychology_insights.json`) - Session analysis prompts
- **Summary Prompts** (`config/summary_prompts.json`) - Session summary generation prompts

All configurations are loaded independently and can be modified separately. 