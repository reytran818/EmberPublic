# Persona Configuration Guide

This guide explains how to modify the AI personas in the Ember app. Your partner can easily customize personas by editing JSON files, and the changes will be reflected in the app.

## 🎯 How It Works

The app now supports external persona configuration through JSON files. When your partner modifies these files, the app will automatically load the updated personas.

### Configuration Sources (in order of priority):
1. **Local config file** - Stored on the device
2. **Remote config file** - Loaded from GitHub
3. **Hardcoded personas** - Fallback if external config fails

## 📝 How to Modify Personas

### Option 1: Edit the JSON File Directly

1. **Open the configuration file:**
   ```
   config/personas.json
   ```

2. **Modify any persona properties:**
   - `name` - Display name
   - `emoji` - Emoji icon
   - `greeting` - Initial greeting message
   - `description` - Persona description
   - `systemPrompt` - AI behavior instructions
   - `sampleResponses` - Example responses
   - `voiceConfig` - Voice settings

3. **Save the file and commit to GitHub**

### Option 2: Create a New Persona

Add a new persona to the `personas` array:

```json
{
  "id": "new_persona",
  "name": "New Persona",
  "emoji": "🌟",
  "greeting": "Hello! I'm your new persona.",
  "description": "A custom persona for specific needs",
  "type": "custom",
  "systemPrompt": "You are a custom persona...",
  "sampleResponses": [
    "Sample response 1",
    "Sample response 2"
  ],
  "voiceConfig": {
    "primaryVoice": "en-US-AvaNeural",
    "fallbackVoice": "en-US-JennyMultilingualNeural",
    "style": "friendly",
    "pitch": 1.0,
    "rate": 1.0
  }
}
```

## 🔧 Persona Properties Explained

### Basic Properties
- **`id`** - Unique identifier (required)
- **`name`** - Display name shown in the app
- **`emoji`** - Emoji icon for the persona
- **`greeting`** - Initial message when persona is selected
- **`description`** - Brief description of the persona's role

### AI Behavior
- **`systemPrompt`** - Instructions that define how the AI behaves
- **`sampleResponses`** - Example responses for when AI is not configured

### Voice Settings
- **`primaryVoice`** - Main Azure voice to use
- **`fallbackVoice`** - Backup voice if primary fails
- **`style`** - Voice style (friendly, calm, cheerful, etc.)
- **`pitch`** - Voice pitch (0.5 to 2.0)
- **`rate`** - Speaking speed (0.5 to 2.0)

## 🎨 Available Voice Options

### Female Voices
- `en-US-AvaNeural` - Natural, conversational
- `en-US-JennyMultilingualNeural` - Warm, multilingual
- `en-US-SaraNeural` - Calm, wise
- `en-US-AmberNeural` - Empathetic, understanding
- `en-US-AshleyNeural` - Supportive, encouraging
- `en-US-NancyNeural` - Warm, caring
- `en-US-JaneNeural` - Gentle, contemplative

### Male Voices
- `en-US-GuyNeural` - Energetic, confident
- `en-US-DavisNeural` - Strong, motivational
- `en-US-JasonNeural` - Supportive, steady
- `en-US-TonyNeural` - Confident, aspirational
- `en-US-ChristopherNeural` - Reliable, friendly

### Voice Styles
- `friendly` - Warm and approachable
- `calm` - Peaceful and contemplative
- `cheerful` - Energetic and positive
- `empathetic` - Understanding and caring
- `hopeful` - Encouraging and optimistic
- `confident` - Strong and assured

## 📋 Example Modifications

### Modify Inner Child's Greeting
```json
{
  "id": "inner_child",
  "name": "Inner Child",
  "emoji": "🧒",
  "greeting": "Hi there! I'm your inner child - the part of you that remembers how to play and dream. What's on your heart today?",
  // ... rest of properties
}
```

### Add a New Therapeutic Persona
```json
{
  "id": "anxiety_coach",
  "name": "Anxiety Coach",
  "emoji": "🫂",
  "greeting": "I understand anxiety can feel overwhelming. Let's work through this together, one breath at a time.",
  "description": "Your guide for managing anxiety and finding calm",
  "type": "anxiety_coach",
  "systemPrompt": "You are a compassionate anxiety coach who helps people manage their anxiety.\n\nGuidelines:\n- Be calming and grounding\n- Use breathing techniques and mindfulness\n- Validate feelings without amplifying them\n- Focus on practical coping strategies\n- Encourage self-compassion\n- Use gentle, reassuring language",
  "sampleResponses": [
    "Let's take a deep breath together. Inhale for 4, hold for 4, exhale for 6.",
    "Anxiety is trying to protect you, but it's being overprotective right now.",
    "You're safe in this moment. What's one small thing you can do to feel more grounded?",
    "It's okay to feel anxious. Let's work with it instead of fighting it.",
    "Remember, this feeling will pass. You've gotten through this before."
  ],
  "voiceConfig": {
    "primaryVoice": "en-US-SaraNeural",
    "fallbackVoice": "en-US-JaneNeural",
    "style": "calm",
    "pitch": 0.95,
    "rate": 0.9
  }
}
```

## 🔄 How Changes Are Applied

1. **Edit the JSON file** in the `config/` folder
2. **Commit and push** to GitHub (reytran818/EmberApp)
3. **The app will automatically**:
   - Check for updates when launched
   - Download the new configuration
   - Apply changes immediately
   - Fall back to hardcoded personas if needed

## 🛠️ Troubleshooting

### Changes Not Appearing?
1. Make sure the JSON is valid (use a JSON validator)
2. Check that the file is committed to GitHub
3. Restart the app to force a refresh
4. Check the app logs for configuration errors

### Adding New Persona Types
If you add a new `type` that's not in the hardcoded list, the app will:
1. Try to use the new type
2. Fall back to `ember` type if not recognized
3. Still work with custom system prompts and responses

### Voice Configuration Issues
- Ensure voice names are exactly as listed above
- Check that the style is one of the available options
- Pitch and rate should be between 0.5 and 2.0

## 📱 Testing Changes

1. **Make your changes** to the JSON file
2. **Commit and push** to GitHub (reytran818/EmberApp)
3. **Launch the app** on a device
4. **Check the persona selector** for your changes
5. **Test the conversation** to see the new behavior

## 🔒 Safety Features

- **Backup system**: If external config fails, app uses hardcoded personas
- **Validation**: Invalid JSON won't break the app
- **Version control**: All changes are tracked in Git
- **Rollback**: Can revert to previous versions if needed

## 📞 Support

If you need help modifying personas:
1. Check this guide first
2. Validate your JSON syntax
3. Test with a simple change first
4. Check the app logs for error messages

The system is designed to be robust and user-friendly, so your partner can confidently modify personas without breaking the app! 