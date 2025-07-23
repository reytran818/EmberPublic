# Psychology Insight Configuration Guide

This guide explains how to modify the psychology insights in the Ember app. Your employee can easily customize how the AI analyzes therapy sessions by editing JSON files.

## 🎯 How It Works

The app now supports external psychology insight configuration through JSON files. When your employee modifies these files, the app will automatically load the updated insights for session analysis.

### Configuration Sources (in order of priority):
1. **Psychology insights config file** - `config/psychology_insights.json`
2. **Hardcoded insights** - Fallback if external config fails

## 📝 How to Modify Psychology Insights

### Option 1: Edit the Psychology Insights Config File

1. **Open the configuration file:**
   ```
   config/psychology_insights.json
   ```

2. **Modify any section:**
   - `systemPrompt` - How the AI analyzes therapy sessions
   - `fallbackInsights` - Default insights for each persona
   - `defaultInsight` - Generic insight template
   - **Write insights as simple text without line breaks**
   - Use periods to separate ideas instead of bullet points
   - Save the file and commit to GitHub

### Option 2: Modify System Prompt

The `systemPrompt` controls how the AI analyzes therapy sessions:

```json
{
  "systemPrompt": "Your new system prompt here. This will change how the AI analyzes therapy sessions."
}
```

### Option 3: Modify Fallback Insights

The `fallbackInsights` section contains default insights for each persona when AI analysis fails:

```json
{
  "fallbackInsights": {
    "ember": {
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

## 🔧 Psychology Insight Properties Explained

### System Prompt
- **`systemPrompt`** - Instructions for how the AI should analyze therapy sessions (editable)

### Fallback Insights
Each persona has these properties:
- **`name`** - Display name (read-only)
- **`cognitivePatterns`** - Analysis of thought processes
- **`emotionalThemes`** - Key emotional content and processing
- **`behavioralInsights`** - Engagement patterns and therapeutic progress
- **`growthOpportunities`** - Areas for personal development
- **`therapeuticProgress`** - Assessment of session effectiveness
- **`recommendations`** - Actionable next steps

### Default Insight
- **`defaultInsight`** - Generic template used when persona-specific insight is not found

## 🚀 Available Personas

The following personas have customizable psychology insights:

1. **ember** - 🔥Ember (default conversational friend)
2. **inner_child** - Inner Child (playful, vulnerable self)
3. **life_coach** - Life Coach (motivational guidance)
4. **spiritual_shaman** - Spiritual Shaman (wise spiritual guidance)
5. **relationship_expert** - Relationship Expert (compassionate relationship advice)
6. **identity_guide** - Identity Guide (self-discovery support)
7. **recovery_ally** - Recovery Ally (healing journey support)
8. **future_self** - Future Self (perspective from the future)

## 📋 Best Practices

### Writing Effective Psychology Insights

1. **Be Specific**: Focus on psychological patterns and therapeutic insights
2. **Use Professional Language**: Maintain clinical accuracy while being accessible
3. **Include Actionable Content**: Provide concrete recommendations
4. **Consider Context**: Think about what each persona specializes in

### Example: Modifying Ember's Psychology Insight

```json
{
  "fallbackInsights": {
    "ember": {
      "name": "🔥Ember",
      "cognitivePatterns": "You demonstrated clear self-awareness and reflective thinking throughout the session. Your ability to process thoughts and feelings shows strong cognitive engagement.",
      "emotionalThemes": "You worked through various emotions with openness and vulnerability. The session showed healthy emotional processing and self-compassion.",
      "behavioralInsights": "Your active participation with {messageCount} messages over {durationMinutes} minutes indicates strong therapeutic engagement and commitment to growth.",
      "growthOpportunities": "Continue building on the insights gained today. Focus on implementing the strategies discussed and maintaining momentum in your personal development.",
      "therapeuticProgress": "This session demonstrates meaningful therapeutic work with strong engagement and positive therapeutic alliance.",
      "recommendations": "Journal your key insights from today. Practice the self-compassion techniques discussed. Set small, achievable goals for the week ahead."
    }
  }
}
```

## 🔄 How Updates Work

1. **Employee edits** `config/psychology_insights.json`
2. **Commits changes** to GitHub
3. **App automatically loads** the new configuration
4. **Changes take effect** immediately in session analysis

## 🛠️ Troubleshooting

### If Changes Don't Appear
1. Check that the JSON is valid (no syntax errors)
2. Ensure the file is committed to GitHub
3. Restart the app to clear any cached configurations

### If the App Crashes
1. Check the JSON syntax in the config file
2. Verify all required fields are present
3. Use the fallback hardcoded insights if needed

## 📞 Support

If you need help modifying the psychology insights:
1. Check the existing insights for examples
2. Test changes with small modifications first
3. Ask for assistance if you're unsure about the format

## 🔍 Advanced Configuration

### Adding Custom Analysis Sections
You can modify the system prompt to include different analysis sections:

```json
{
  "systemPrompt": "You are a professional psychologist analyzing therapy sessions. Focus on cognitive patterns, emotional themes, behavioral insights, growth opportunities, therapeutic progress, and recommendations. Use clear, structured sections with descriptive headings."
}
```

### Modifying Insight Templates
The fallback insights provide templates for when AI analysis fails. Be careful when modifying these as they provide essential psychological analysis.

### Using Variables
The insights support these variables that get replaced with actual data:
- `{messageCount}` - Number of messages in the session
- `{durationMinutes}` - Duration of the session in minutes

---

**Note**: The app will automatically fall back to hardcoded insights if there are any issues with the configuration files, ensuring the app always works even if there are configuration errors. 