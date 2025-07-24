# Available Personas Configuration Guide

This guide explains how to modify the available personas in the Ember app through JSON configuration files.

## Overview

The app now loads available personas from a JSON configuration file stored on GitHub. This allows non-technical users to easily add, remove, or modify personas without touching code.

## Configuration File Location

The configuration is stored at:
`https://raw.githubusercontent.com/reytran818/EmberPublic/main/config/available_personas.json`

## File Structure

```json
{
  "version": "1.0.0",
  "lastUpdated": "2025-01-23T14:41:22.992185",
  "availablePersonas": [
    {
      "id": "ember",
      "name": "🔥Ember",
      "emoji": "🔥",
      "greeting": "Hey there! I'm Ember - let's have a real conversation. What's on your mind?",
      "description": "Your conversational friend for natural, relaxed chat",
      "type": "ember",
      "isDefault": true,
      "isEnabled": true,
      "order": 1
    }
  ],
  "configuration": {
    "defaultPersonaId": "ember",
    "maxPersonasToShow": 8,
    "allowPersonaSwitching": true,
    "showPersonaDescriptions": true,
    "showPersonaEmojis": true,
    "enablePersonaGreetings": true
  }
}
```

## Persona Properties

### Required Fields
- **id**: Unique identifier for the persona (e.g., "ember")
- **name**: Display name shown in the app (e.g., "🔥Ember")
- **emoji**: Emoji icon for the persona (e.g., "🔥")
- **greeting**: Initial greeting message when persona is selected
- **description**: Brief description of the persona's role
- **type**: Persona type for system prompts (e.g., "ember")
- **order**: Display order in the selection menu (1, 2, 3, etc.)

### Optional Fields
- **isDefault**: Set to `true` for the default persona (only one should be true)
- **isEnabled**: Set to `false` to hide the persona from the selection menu

## Configuration Settings

- **defaultPersonaId**: The ID of the persona that should be selected by default
- **maxPersonasToShow**: Maximum number of personas to display in the menu
- **allowPersonaSwitching**: Whether users can switch between personas
- **showPersonaDescriptions**: Whether to show persona descriptions
- **showPersonaEmojis**: Whether to show persona emojis
- **enablePersonaGreetings**: Whether to show greeting messages

## How to Modify

### Adding a New Persona

1. Add a new object to the `availablePersonas` array:
```json
{
  "id": "new-persona",
  "name": "New Persona",
  "emoji": "🌟",
  "greeting": "Hello! I'm your new guide. How can I help you today?",
  "description": "Description of what this persona does",
  "type": "new_type",
  "isDefault": false,
  "isEnabled": true,
  "order": 9
}
```

### Removing a Persona

Set `isEnabled` to `false`:
```json
{
  "id": "old-persona",
  "isEnabled": false
}
```

### Changing the Default Persona

1. Set `isDefault: false` for the current default persona
2. Set `isDefault: true` for the new default persona
3. Update `defaultPersonaId` in the configuration section

### Updating Persona Information

Simply modify the relevant fields:
- Change `name` to update the display name
- Change `emoji` to update the emoji icon
- Change `greeting` to update the greeting message
- Change `description` to update the description
- Change `order` to change the display order

### Reordering Personas

Update the `order` field for each persona:
- Lower numbers appear first (1, 2, 3, etc.)
- Higher numbers appear last (8, 9, 10, etc.)

## Persona Types

Common persona types and their purposes:
- **ember**: General conversational assistant
- **inner_child**: Playful, vulnerable, child-like responses
- **life_coach**: Motivational, goal-oriented guidance
- **spiritual_shaman**: Spiritual, wisdom-focused responses
- **relationship_expert**: Relationship and emotional guidance
- **identity_guide**: Self-discovery and identity exploration
- **recovery_ally**: Supportive healing and recovery guidance
- **future_self**: Wise, future perspective guidance

## Emoji Guidelines

Use appropriate emojis for each persona:
- 🔥 Ember (fire/energy)
- 🧒 Inner Child (child/innocence)
- 💪 Life Coach (strength/motivation)
- 🌟 Spiritual Shaman (spirituality/wisdom)
- 💕 Relationship Expert (love/relationships)
- 🎭 Identity Guide (identity/self)
- 🔄 Recovery Ally (recovery/healing)
- 🔮 Future Self (future/wisdom)

## Best Practices

1. **Test Changes**: Always test configuration changes in a development environment first
2. **Backup**: Keep a backup of the current configuration before making changes
3. **Incremental Changes**: Make small, incremental changes rather than large modifications
4. **Consistent Ordering**: Use sequential order numbers (1, 2, 3, etc.) for easy management
5. **Meaningful Descriptions**: Write clear, concise descriptions that explain the persona's role
6. **Appropriate Greetings**: Create welcoming, in-character greeting messages

## Troubleshooting

### Persona Not Appearing
- Check that `isEnabled` is set to `true`
- Verify the `type` matches existing system prompts
- Ensure the persona is within the `maxPersonasToShow` limit

### Persona Selection Not Working
- Verify the `defaultPersonaId` matches an existing persona ID
- Check that only one persona has `isDefault: true`

### Greeting Not Showing
- Ensure `enablePersonaGreetings` is `true` in configuration
- Verify the `greeting` field is not empty

### Emoji Not Displaying
- Check that `showPersonaEmojis` is `true` in configuration
- Ensure the emoji is a valid Unicode emoji character

## Support

For questions or issues with persona configuration, contact the development team or refer to the existing persona definitions for guidance. 