# Base Prompt Configuration Guide

This guide explains how to modify the base prompts in the Ember app. Your employee can easily customize the AI behavior by editing JSON files, and the changes will be reflected in the app.

## 🎯 How It Works

The app now supports external base prompt configuration through JSON files. When your employee modifies these files, the app will automatically load the updated prompts.

### Configuration Sources (in order of priority):
1. **Base prompt config file** - `config/base_prompts.json`
2. **Persona config file** - `config/personas.json` (also simplified for easy editing)
3. **Psychology insights config file** - `config/psychology_insights.json` (for session analysis)
4. **Hardcoded prompts** - Fallback if external config fails

## 📝 How to Modify Base Prompts

### ✅ Simple JSON Format - No Line Breaks

The JSON files are now formatted for maximum simplicity:
- **Proper indentation** for clear structure
- **Simple text content** without any `\n` characters
- **Clear sections** that are easy to identify and modify
- **No line breaks** in text content - use periods instead
- **Easy to read and edit** for non-technical users

### Option 1: Edit the Base Prompt Config File

1. **Open the configuration file:**
   ```
   config/base_prompts.json
   ```

2. **Modify any persona's system prompt:**
   - Find the persona you want to modify in the `basePrompts` section
   - Update the `systemPrompt` field with new instructions
   - **Write prompts as simple text without line breaks**
   - Use periods to separate ideas instead of bullet points
   - Save the file and commit to GitHub

### Option 2: Edit the Personas Config File

1. **Open the configuration file:**
   ```
   config/personas.json
   ```

2. **Modify any persona's properties:**
   - Find the persona you want to modify in the `personas` array
   - Update any of these fields:
     - `systemPrompt` - How the AI behaves
     - `greeting` - Initial message when selected
     - `description` - What this persona does
     - `sampleResponses` - Example responses
   - **Write prompts as simple text without line breaks**
   - Use periods to separate ideas instead of bullet points
   - Save the file and commit to GitHub

### Option 3: Edit the Psychology Insights Config File

1. **Open the configuration file:**
   ```
   config/psychology_insights.json
   ```

2. **Modify psychology insights:**
   - `systemPrompt` - How the AI analyzes therapy sessions
   - `fallbackInsights` - Default insights for each persona when AI analysis fails
   - `defaultInsight` - Generic insight template for unknown personas
   - **Write insights as simple text without line breaks**
   - Use periods to separate ideas instead of bullet points
   - Save the file and commit to GitHub

### Format Guidelines

- ✅ **Good**: "You are a helpful assistant. Always be kind and supportive. Keep responses short and friendly."
- ❌ **Avoid**: "You are a helpful assistant.\n- Always be kind\n- Keep responses short"

### Option 2: Modify Global Rules

The `globalRules` section contains formatting rules that apply to all personas:

- `criticalFormatting` - Rules that apply to all responses
- `voiceModeRules` - Additional rules for voice mode
- `keyboardModeRules` - Additional rules for keyboard mode

### Example: Modifying Ember's Base Prompt

```json
{
  "basePrompts": {
    "ember": {
      "name": "🔥Ember",
      "systemPrompt": "Your new system prompt here. This will change how Ember behaves in conversations."
    }
  }
}
```

### Example: Modifying a Persona in personas.json

```json
{
  "personas": [
    {
      "id": "ember",
      "name": "🔥Ember",
      "greeting": "Your new greeting message here.",
      "description": "Your new description here.",
      "systemPrompt": "Your new system prompt here. This will change how Ember behaves in conversations."
    }
  ]
}
```

### Example: Modifying Psychology Insights

```json
{
  "fallbackInsights": {
    "ember": {
      "name": "🔥Ember",
      "cognitivePatterns": "Your new cognitive patterns analysis here.",
      "emotionalThemes": "Your new emotional themes analysis here.",
      "behavioralInsights": "Your new behavioral insights here.",
      "growthOpportunities": "Your new growth opportunities here.",
      "therapeuticProgress": "Your new therapeutic progress assessment here.",
      "recommendations": "Your new recommendations here."
    }
  }
}
```

**Important**: Write your prompts as simple text without line breaks. Use periods to separate ideas instead of new lines.

## 🔧 Base Prompt Properties Explained

### Persona Prompts
Each persona has these properties:
- **`name`** - Display name (read-only)
- **`systemPrompt`** - The AI behavior instructions (editable)

### Global Rules
These rules apply to all personas:
- **`criticalFormatting`** - Basic formatting rules (no asterisks, etc.)
- **`voiceModeRules`** - Rules for voice conversations (character limits, etc.)
- **`keyboardModeRules`** - Rules for text conversations (longer responses allowed)

## 🚀 Available Personas

The following personas can be modified:

1. **ember** - 🔥Ember (default conversational friend)
2. **inner_child** - Inner Child (playful, vulnerable self)
3. **life_coach** - Life Coach (motivational guidance)
4. **spiritual_shaman** - Spiritual Shaman (wise spiritual guidance)
5. **relationship_expert** - Relationship Expert (compassionate relationship advice)
6. **identity_guide** - Identity Guide (self-discovery support)
7. **recovery_ally** - Recovery Ally (healing journey support)
8. **future_self** - Future Self (perspective from the future)

## 📋 Best Practices

### Writing Effective System Prompts

1. **Be Specific**: Clearly define the persona's role and communication style
2. **Include Guidelines**: Add specific behavioral instructions
3. **Consider Context**: Think about when this persona would be most helpful
4. **Test Changes**: Make small changes and test the behavior
5. **Keep It Simple**: Write in clear, simple sentences without complex formatting
6. **No Line Breaks**: Use periods to separate ideas instead of `\n` characters

### Example: Adding a New Persona

```json
{
  "basePrompts": {
    "new_persona": {
      "name": "New Persona",
      "systemPrompt": "You are a new persona with specific instructions..."
    }
  }
}
```

## 🔄 How Updates Work

1. **Employee edits** any of the config files:
   - `config/base_prompts.json` - Base AI behavior
   - `config/personas.json` - Persona settings and responses
   - `config/psychology_insights.json` - Session analysis insights
   - `config/summary_prompts.json` - Session summary generation prompts
   - `config/conversation_prompts.json` - Conversation flow and system messages
2. **Commits changes** to GitHub
3. **App automatically loads** the new configuration
4. **Changes take effect** immediately in the app

## 🛠️ Troubleshooting

### If Changes Don't Appear
1. Check that the JSON is valid (no syntax errors)
2. Ensure the file is committed to GitHub
3. Restart the app to clear any cached configurations

### If the App Crashes
1. Check the JSON syntax in the config file
2. Verify all required fields are present
3. Use the fallback hardcoded prompts if needed

## 📞 Support

If you need help modifying the base prompts:
1. Check the existing prompts for examples
2. Test changes with small modifications first
3. Ask for assistance if you're unsure about the format

## 🔍 Advanced Configuration

### Adding Custom Rules
You can add custom rules to any persona by modifying the `systemPrompt`:

```json
{
  "systemPrompt": "You are a helpful assistant. Always be kind and supportive. Never use asterisks for actions. Keep responses under 150 characters in voice mode."
}
```

**Tip**: Write prompts as flowing text. Use periods to separate ideas instead of line breaks or bullet points.

### Modifying Global Rules
The global rules affect all personas. Be careful when modifying these as they provide essential formatting guidelines.

---

**Note**: The app will automatically fall back to hardcoded prompts if there are any issues with the configuration files, ensuring the app always works even if there are configuration errors. 