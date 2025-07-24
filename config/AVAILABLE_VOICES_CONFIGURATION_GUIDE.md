# Available Voices Configuration Guide

This guide explains how to modify the available voice types and speeds in the Ember app through JSON configuration files.

## Overview

The app now loads available voice options from a JSON configuration file stored on GitHub. This allows non-technical users to easily add, remove, or modify voice types and speeds without touching code.

## Configuration File Location

The configuration is stored at:
`https://raw.githubusercontent.com/reytran818/EmberPublic/main/config/available_voices.json`

## File Structure

```json
{
  "version": "1.0.0",
  "lastUpdated": "2025-01-23T14:41:22.992185",
  "availableVoiceTypes": [
    {
      "id": "azure-jenny",
      "name": "Jenny",
      "description": "Warm and friendly female voice",
      "provider": "azure",
      "azureVoiceName": "en-US-JennyNeural",
      "gender": "female",
      "isDefault": true,
      "isEnabled": true,
      "order": 1
    }
  ],
  "availableVoiceSpeeds": [
    {
      "id": "default",
      "name": "Default",
      "description": "Natural speaking pace",
      "rate": 1.0,
      "isDefault": true,
      "isEnabled": true,
      "order": 2
    }
  ],
  "configuration": {
    "defaultVoiceTypeId": "azure-jenny",
    "defaultVoiceSpeedId": "default",
    "maxVoiceTypesToShow": 6,
    "maxVoiceSpeedsToShow": 3,
    "allowVoiceSwitching": true,
    "showVoiceDescriptions": true,
    "showVoiceGender": true,
    "enableReadAloud": true,
    "enableVoiceSpeedControl": true,
    "defaultReadAloudEnabled": true
  }
}
```

## Voice Type Properties

### Required Fields
- **id**: Unique identifier for the voice type (e.g., "azure-jenny")
- **name**: Display name shown in the app (e.g., "Jenny")
- **description**: Brief description of the voice characteristics
- **provider**: Voice provider (currently "azure")
- **azureVoiceName**: The Azure Speech Service voice name (e.g., "en-US-JennyNeural")
- **gender**: Voice gender ("male" or "female")
- **order**: Display order in the selection menu (1, 2, 3, etc.)

### Optional Fields
- **isDefault**: Set to `true` for the default voice type (only one should be true)
- **isEnabled**: Set to `false` to hide the voice type from the selection menu

## Voice Speed Properties

### Required Fields
- **id**: Unique identifier for the voice speed (e.g., "default")
- **name**: Display name shown in the app (e.g., "Default")
- **description**: Brief description of the speed characteristics
- **rate**: Speech rate multiplier (0.5 = half speed, 1.0 = normal, 2.0 = double speed)
- **order**: Display order in the selection menu (1, 2, 3, etc.)

### Optional Fields
- **isDefault**: Set to `true` for the default voice speed (only one should be true)
- **isEnabled**: Set to `false` to hide the voice speed from the selection menu

## Configuration Settings

- **defaultVoiceTypeId**: The ID of the voice type that should be selected by default
- **defaultVoiceSpeedId**: The ID of the voice speed that should be selected by default
- **maxVoiceTypesToShow**: Maximum number of voice types to display in the menu
- **maxVoiceSpeedsToShow**: Maximum number of voice speeds to display in the menu
- **allowVoiceSwitching**: Whether users can switch between voice types
- **showVoiceDescriptions**: Whether to show voice descriptions
- **showVoiceGender**: Whether to show voice gender information
- **enableReadAloud**: Whether the read aloud feature is available
- **enableVoiceSpeedControl**: Whether voice speed control is available
- **defaultReadAloudEnabled**: Whether read aloud is enabled by default

## How to Modify

### Adding a New Voice Type

1. Add a new object to the `availableVoiceTypes` array:
```json
{
  "id": "azure-new-voice",
  "name": "New Voice",
  "description": "Description of the new voice",
  "provider": "azure",
  "azureVoiceName": "en-US-NewVoiceNeural",
  "gender": "female",
  "isDefault": false,
  "isEnabled": true,
  "order": 7
}
```

### Adding a New Voice Speed

1. Add a new object to the `availableVoiceSpeeds` array:
```json
{
  "id": "very-slow",
  "name": "Very Slow",
  "description": "Very relaxed pace for meditation",
  "rate": 0.6,
  "isDefault": false,
  "isEnabled": true,
  "order": 1
}
```

### Removing a Voice Type or Speed

Set `isEnabled` to `false`:
```json
{
  "id": "old-voice",
  "isEnabled": false
}
```

### Changing the Default Voice Type

1. Set `isDefault: false` for the current default voice type
2. Set `isDefault: true` for the new default voice type
3. Update `defaultVoiceTypeId` in the configuration section

### Changing the Default Voice Speed

1. Set `isDefault: false` for the current default voice speed
2. Set `isDefault: true` for the new default voice speed
3. Update `defaultVoiceSpeedId` in the configuration section

### Updating Voice Information

Simply modify the relevant fields:
- Change `name` to update the display name
- Change `description` to update the description
- Change `azureVoiceName` to update the Azure voice name
- Change `order` to change the display order

## Azure Voice Names

Common Azure Neural voice names:
- `en-US-JennyNeural` - Jenny (female)
- `en-US-GuyNeural` - Guy (male)
- `en-US-AriaNeural` - Aria (female)
- `en-US-DavisNeural` - Davis (male)
- `en-US-SaraNeural` - Sara (female)
- `en-US-TonyNeural` - Tony (male)

## Voice Speed Guidelines

Recommended rate values:
- **Very Slow**: 0.5-0.7 (for meditation, relaxation)
- **Slow**: 0.8-0.9 (for easy listening)
- **Default**: 1.0 (natural speaking pace)
- **Fast**: 1.1-1.3 (for efficient communication)
- **Very Fast**: 1.4-1.6 (for quick summaries)

## Best Practices

1. **Test Changes**: Always test voice changes in a development environment first
2. **Backup**: Keep a backup of the current configuration before making changes
3. **Incremental Changes**: Make small, incremental changes rather than large modifications
4. **Consistent Ordering**: Use sequential order numbers (1, 2, 3, etc.) for easy management
5. **Meaningful Descriptions**: Write clear, concise descriptions that explain the voice characteristics
6. **Appropriate Rates**: Use speech rates that feel natural and comfortable for users
7. **Gender Balance**: Provide a good mix of male and female voices
8. **Azure Compatibility**: Ensure all Azure voice names are valid and available

## Troubleshooting

### Voice Type Not Appearing
- Check that `isEnabled` is set to `true`
- Verify the `azureVoiceName` is a valid Azure voice name
- Ensure the voice type is within the `maxVoiceTypesToShow` limit

### Voice Speed Not Appearing
- Check that `isEnabled` is set to `true`
- Verify the `rate` value is reasonable (0.5 to 2.0)
- Ensure the voice speed is within the `maxVoiceSpeedsToShow` limit

### Voice Selection Not Working
- Verify the `defaultVoiceTypeId` matches an existing voice type ID
- Check that only one voice type has `isDefault: true`
- Verify the `defaultVoiceSpeedId` matches an existing voice speed ID
- Check that only one voice speed has `isDefault: true`

### Read Aloud Not Working
- Ensure `enableReadAloud` is `true` in configuration
- Check that `defaultReadAloudEnabled` is set appropriately

### Voice Speed Control Not Working
- Ensure `enableVoiceSpeedControl` is `true` in configuration
- Verify that voice speeds have valid `rate` values

## Azure Voice Considerations

When adding new Azure voices:
1. **Verify Availability**: Ensure the voice name exists in Azure Speech Service
2. **Test Quality**: Test the voice quality and naturalness
3. **Check Language**: Ensure voices are English (en-US) for consistency
4. **Neural Voices**: Prefer neural voices (ending in "Neural") for better quality
5. **Gender Balance**: Maintain a good balance between male and female voices

## Support

For questions or issues with voice configuration, contact the development team or refer to the Azure Speech Service documentation for available voices. 