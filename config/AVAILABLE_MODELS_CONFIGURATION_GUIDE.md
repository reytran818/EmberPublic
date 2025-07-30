# Available Models Configuration Guide

This guide explains how to modify the available LLM models in the Ember app through JSON configuration files.

## Overview

The app now loads available models from a JSON configuration file stored on GitHub. This allows non-technical users to easily add, remove, or modify models without touching code.

## Configuration File Location

The configuration is stored at:
`https://raw.githubusercontent.com/reytran818/EmberPublic/main/config/available_models.json`

## File Structure

```json
{
  "version": "1.0.0",
  "lastUpdated": "2025-01-23T14:41:22.992185",
  "availableModels": [
    {
      "id": "kimi-k2",
      "title": "Kimi-K2",
      "description": "Moonshot AI's advanced reasoning model",
      "badge": "POWERFUL",
      "badgeColor": "#9333EA",
      "openRouterId": "moonshotai/kimi-k2",
      "isDefault": true,
      "isEnabled": true
    }
  ],
  "configuration": {
    "defaultModelId": "kimi-k2",
    "maxModelsToShow": 6,
    "allowModelSwitching": true,
    "showModelDescriptions": true,
    "showModelBadges": true
  }
}
```

## Model Properties

### Required Fields
- **id**: Unique identifier for the model (e.g., "kimi-k2")
- **title**: Display name shown in the app (e.g., "Kimi-K2")
- **description**: Brief description of the model
- **badge**: Short label shown next to the model (e.g., "POWERFUL")
- **badgeColor**: Hex color for the badge (e.g., "#9333EA")
- **openRouterId**: The OpenRouter model ID (e.g., "moonshotai/kimi-k2")

### Optional Fields
- **isDefault**: Set to `true` for the default model (only one should be true)
- **isEnabled**: Set to `false` to hide the model from the selection menu

## Configuration Settings

- **defaultModelId**: The ID of the model that should be selected by default
- **maxModelsToShow**: Maximum number of models to display in the menu
- **allowModelSwitching**: Whether users can switch between models
- **showModelDescriptions**: Whether to show model descriptions
- **showModelBadges**: Whether to show model badges

## How to Modify

### Adding a New Model

1. Add a new object to the `availableModels` array:
```json
{
  "id": "new-model",
  "title": "New Model",
  "description": "Description of the new model",
  "badge": "NEW",
  "badgeColor": "#FF6B6B",
  "openRouterId": "provider/new-model-id",
  "isDefault": false,
  "isEnabled": true
}
```

### Removing a Model

Set `isEnabled` to `false`:
```json
{
  "id": "old-model",
  "isEnabled": false
}
```

### Changing the Default Model

1. Set `isDefault: false` for the current default model
2. Set `isDefault: true` for the new default model
3. Update `defaultModelId` in the configuration section

### Updating Model Information

Simply modify the relevant fields:
- Change `title` to update the display name
- Change `description` to update the description
- Change `badge` and `badgeColor` to update the badge

## OpenRouter Model IDs

Common OpenRouter model IDs:
- `moonshotai/kimi-k2` - Kimi-K2
- `openai/gpt-4o-mini` - GPT-4o-mini
- `google/gemma-3-12b-it:free` - Gemma-3
- `google/gemma-3-27b-it:free` - Gemma-3N
- `deepseek/deepseek-r1` - DeepSeek-V3
- `x-ai/grok-2-1212` - Grok-3

## Color Codes

Use hex color codes for badges:
- Purple: `#9333EA`
- Blue: `#0EA5E9`
- Green: `#10B981`
- Dark Green: `#059669`
- Purple: `#8B5CF6`
- Red: `#EF4444`

## Best Practices

1. **Test Changes**: Always test configuration changes in a development environment first
2. **Backup**: Keep a backup of the current configuration before making changes
3. **Incremental Changes**: Make small, incremental changes rather than large modifications
4. **Documentation**: Update this guide when adding new model types or configurations
5. **Validation**: Ensure all required fields are present and valid

## Troubleshooting

### Model Not Appearing
- Check that `isEnabled` is set to `true`
- Verify the `openRouterId` is correct
- Ensure the model is within the `maxModelsToShow` limit

### Model Selection Not Working
- Verify the `defaultModelId` matches an existing model ID
- Check that only one model has `isDefault: true`

### Badge Not Displaying
- Ensure `badgeColor` is a valid hex color code
- Check that `showModelBadges` is `true` in configuration

## Support

For questions or issues with model configuration, contact the development team or refer to the OpenRouter documentation for available models. 