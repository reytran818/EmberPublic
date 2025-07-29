# Available Models Configuration Guide

This guide explains how to modify the available LLM models in the Ember app through JSON configuration files.

## Overview

The app now uses hardcoded model configuration. Model settings are defined directly in the code and no longer pull from external sources.

## Configuration Location

The configuration is hardcoded in:
`lib/config/available_models_config_service.dart`

## Code Structure

The model configuration is now hardcoded in the `_getHardcodedModels()` method:

```dart
static List<ModelConfig> _getHardcodedModels() {
  return [
    const ModelConfig(
      id: 'gemma-3n',
      title: 'Gemma-3 27B',
      description: 'Google\'s 27B parameter model (Paid)',
      badge: 'PREMIUM',
      badgeColor: '#059669',
      openRouterId: 'google/gemma-3-27b-it',
      isDefault: true,
      isEnabled: true,
    ),
  ];
}
```

## Model Properties

### Required Fields
- **id**: Unique identifier for the model (e.g., "gemma-3n")
- **title**: Display name shown in the app (e.g., "Gemma-3 27B")
- **description**: Brief description of the model
- **badge**: Short label shown next to the model (e.g., "PREMIUM")
- **badgeColor**: Hex color for the badge (e.g., "#059669")
- **openRouterId**: The OpenRouter model ID (e.g., "google/gemma-3-27b-it")

### Optional Fields
- **isDefault**: Set to `true` for the default model (only one should be true)
- **isEnabled**: Set to `false` to hide the model from the selection menu

## Configuration Settings

The configuration is hardcoded in the `_getHardcodedConfiguration()` method:

```dart
static ModelConfiguration _getHardcodedConfiguration() {
  return const ModelConfiguration(
    defaultModelId: 'gemma-3n',
    maxModelsToShow: 1,
    allowModelSwitching: false,
    showModelDescriptions: false,
    showModelBadges: false,
  );
}
```

## How to Modify

### Adding a New Model

1. Add a new `ModelConfig` object to the `_getHardcodedModels()` method:
```dart
const ModelConfig(
  id: 'new-model',
  title: 'New Model',
  description: 'Description of the new model',
  badge: 'NEW',
  badgeColor: '#FF6B6B',
  openRouterId: 'provider/new-model-id',
  isDefault: false,
  isEnabled: true,
),
```

### Removing a Model

Remove the `ModelConfig` object from the `_getHardcodedModels()` method or set `isEnabled: false`.

### Changing the Default Model

1. Set `isDefault: false` for the current default model
2. Set `isDefault: true` for the new default model
3. Update `defaultModelId` in the `_getHardcodedConfiguration()` method

### Updating Model Information

Simply modify the relevant fields in the `ModelConfig` object:
- Change `title` to update the display name
- Change `description` to update the description
- Change `badge` and `badgeColor` to update the badge

## OpenRouter Model IDs

Common OpenRouter model IDs:
- `google/gemma-3-27b-it` - Gemma-3 27B (Paid)
- `google/gemma-3-27b-it:free` - Gemma-3 27B (Free)
- `moonshotai/kimi-k2` - Kimi-K2
- `openai/gpt-4o-mini` - GPT-4o-mini
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
2. **Backup**: Keep a backup of the current code before making changes
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

## Benefits of Hardcoded Configuration

1. **No External Dependencies**: Works offline without internet connection
2. **Faster Startup**: No network requests during app initialization
3. **More Reliable**: No dependency on GitHub availability
4. **Self-Contained**: All configuration is within the app
5. **Version Controlled**: Changes are tracked in your code repository

## Support

For questions or issues with model configuration, contact the development team or refer to the OpenRouter documentation for available models. 