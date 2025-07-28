# Character Limits Configuration Guide

This guide explains how to modify character limits for voice chat and keyboard chat through GitHub configuration files.

## Overview

The app now supports dynamic character limits that can be modified through GitHub configuration files without requiring code changes. This allows non-technical users to easily adjust limits based on user feedback or requirements.

## Configuration File Location

The character limits configuration is stored at:
`https://raw.githubusercontent.com/reytran818/EmberPublic/main/config/character_limits.json`

## Current Default Limits

### Keyboard Chat
- **Max Characters**: 1500
- **Warning Threshold**: 100 characters remaining
- **Critical Threshold**: 50 characters remaining

### Voice Chat
- **Max Characters**: 250
- **Max Sentences**: 3
- **Requires Follow-up Question**: Yes

## How to Modify Character Limits

### Step 1: Access the Configuration File

1. Go to your GitHub repository
2. Navigate to `config/character_limits.json`
3. Click the edit button (pencil icon)

### Step 2: Modify the Limits

#### To Increase Keyboard Chat Limit:
```json
{
  "characterLimits": {
    "keyboard": {
      "maxCharacters": 3000,  // Changed from 1500
      "warningThreshold": 200, // Adjusted proportionally
      "criticalThreshold": 100 // Adjusted proportionally
    }
  }
}
```

#### To Increase Voice Chat Limit:
```json
{
  "characterLimits": {
    "voice": {
      "maxCharacters": 500,   // Changed from 250
      "maxSentences": 5,      // Changed from 3
      "enforceConciseMode": true,
      "requireFollowUpQuestion": true
    }
  }
}
```

#### To Disable Character Count Display:
```json
{
  "characterLimits": {
    "display": {
      "showCharacterCount": false,
      "showWarningThreshold": false,
      "showCriticalThreshold": false,
      "colorCoding": false
    }
  }
}
```

### Step 3: Save and Commit

1. Add a commit message describing your changes
2. Commit the changes to the main branch
3. The app will automatically pick up the new limits within 5 minutes

## Configuration Options

### Keyboard Chat Settings

| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| `maxCharacters` | int | 1500 | Maximum characters allowed |
| `warningThreshold` | int | 100 | Characters remaining before warning |
| `criticalThreshold` | int | 50 | Characters remaining before critical warning |
| `enforceWordBoundaries` | bool | true | Truncate at word boundaries |
| `enforceSentenceBoundaries` | bool | true | Truncate at sentence boundaries |

### Voice Chat Settings

| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| `maxCharacters` | int | 250 | Maximum characters allowed |
| `maxSentences` | int | 3 | Maximum sentences allowed |
| `enforceConciseMode` | bool | true | Enforce concise responses |
| `requireFollowUpQuestion` | bool | true | Require follow-up questions |

### Display Settings

| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| `showCharacterCount` | bool | true | Show character count display |
| `showWarningThreshold` | bool | true | Show warning threshold |
| `showCriticalThreshold` | bool | true | Show critical threshold |
| `colorCoding` | bool | true | Enable color coding for thresholds |

### Configuration Limits

| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| `maxKeyboardLimit` | int | 5000 | Maximum allowed keyboard limit |
| `maxVoiceLimit` | int | 1000 | Maximum allowed voice limit |
| `minKeyboardLimit` | int | 100 | Minimum allowed keyboard limit |
| `minVoiceLimit` | int | 50 | Minimum allowed voice limit |

## Example Configurations

### For Long-form Conversations
```json
{
  "characterLimits": {
    "keyboard": {
      "maxCharacters": 3000,
      "warningThreshold": 300,
      "criticalThreshold": 150
    },
    "voice": {
      "maxCharacters": 500,
      "maxSentences": 5
    }
  }
}
```

### For Quick Conversations
```json
{
  "characterLimits": {
    "keyboard": {
      "maxCharacters": 800,
      "warningThreshold": 100,
      "criticalThreshold": 50
    },
    "voice": {
      "maxCharacters": 150,
      "maxSentences": 2
    }
  }
}
```

### For Disabled Limits (Not Recommended)
```json
{
  "characterLimits": {
    "keyboard": {
      "maxCharacters": 10000,
      "warningThreshold": 1000,
      "criticalThreshold": 500
    },
    "voice": {
      "maxCharacters": 1000,
      "maxSentences": 10
    }
  }
}
```

## Best Practices

### 1. Gradual Changes
- Start with small increases (e.g., 1500 → 2000)
- Monitor user feedback and app performance
- Adjust thresholds proportionally

### 2. Consider User Experience
- Very long responses may overwhelm users
- Voice responses should remain concise for natural conversation
- Balance between detail and readability

### 3. Performance Considerations
- Higher limits may impact response times
- Consider API rate limits and costs
- Monitor memory usage with longer texts

### 4. Testing Changes
- Test with different personas and conversation types
- Verify truncation still works properly
- Check that UI elements scale appropriately

## Troubleshooting

### Changes Not Taking Effect
1. **Check Cache**: The app caches config for 5 minutes
2. **Verify URL**: Ensure the GitHub URL is correct
3. **Check JSON Format**: Validate JSON syntax
4. **Restart App**: Force app restart to clear cache

### Performance Issues
1. **Reduce Limits**: Lower character limits if app becomes slow
2. **Check Network**: Ensure stable internet connection
3. **Monitor Memory**: Watch for memory leaks with very long texts

### UI Issues
1. **Adjust Thresholds**: Modify warning/critical thresholds
2. **Check Display Settings**: Verify display options are correct
3. **Test Truncation**: Ensure text truncation works properly

## API Integration

The character limits are automatically applied to:
- **Text Input Fields**: Max length enforcement
- **AI Responses**: Truncation and formatting
- **Voice Responses**: Concise mode enforcement
- **UI Elements**: Character count displays

## Monitoring Changes

After making changes:
1. **Wait 5 minutes** for cache to expire
2. **Test the app** with different conversation lengths
3. **Monitor user feedback** for any issues
4. **Adjust as needed** based on usage patterns

## Support

For questions or issues with character limit configuration:
1. Check this guide first
2. Review the JSON schema
3. Test with small changes first
4. Monitor app performance after changes 