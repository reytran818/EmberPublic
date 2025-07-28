# Character Limits GitHub Modification Guide

## Quick Start

You can now modify character limits for both keyboard and voice chat directly from GitHub without touching any code!

### How to Modify Character Limits:

1. **Go to your GitHub repository**
2. **Navigate to**: `config/character_limits.json`
3. **Click the edit button** (pencil icon)
4. **Modify the values** you want to change
5. **Commit the changes**

### Current Limits (Default):

```json
{
  "characterLimits": {
    "keyboard": {
      "maxCharacters": 1500,  // ← Change this for keyboard chat
      "warningThreshold": 100,
      "criticalThreshold": 50
    },
    "voice": {
      "maxCharacters": 250,    // ← Change this for voice chat
      "maxSentences": 3
    }
  }
}
```

### Example Changes:

#### Increase Keyboard Limit to 3000:
```json
"keyboard": {
  "maxCharacters": 3000,
  "warningThreshold": 200,
  "criticalThreshold": 100
}
```

#### Increase Voice Limit to 500:
```json
"voice": {
  "maxCharacters": 500,
  "maxSentences": 5
}
```

#### Disable Character Count Display:
```json
"display": {
  "showCharacterCount": false,
  "showWarningThreshold": false,
  "showCriticalThreshold": false,
  "colorCoding": false
}
```

### What Happens:

- **Changes take effect within 5 minutes** (cache duration)
- **No app restart required** - changes are loaded automatically
- **Fallback to defaults** if GitHub is unavailable
- **All users get the new limits** automatically

### Limits:

- **Keyboard**: 100 - 5000 characters
- **Voice**: 50 - 1000 characters
- **Sentences**: 1 - 10 sentences

### Testing Your Changes:

1. Make the change in GitHub
2. Wait 5 minutes for cache to expire
3. Test in the app
4. Character count display will show new limits
5. Text truncation will use new limits

### Troubleshooting:

- **Changes not appearing?** Wait 5 minutes for cache to expire
- **App crashes?** Check JSON syntax in GitHub
- **Still using old limits?** Force restart the app
- **GitHub unavailable?** App uses fallback defaults

### Advanced Configuration:

You can also modify:
- Warning thresholds (when count appears)
- Critical thresholds (when color changes)
- Display settings (show/hide counters)
- Truncation behavior (word/sentence boundaries)

The app will automatically pick up all changes from GitHub! 🚀 