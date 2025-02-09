# Module :feature:settings

This module handles user preferences and app settings. It provides a UI for configuring app behavior
and managing user preferences.

## Features

- Theme Configuration (Light/Dark)
- Dynamic Color Toggle
- Open Source Licenses
- User Profile Settings
- Sign Out Option
- Preferences Persistence

## Dependencies Graph

```mermaid
graph TD
    A[feature:settings] --> B[core:ui]
    A --> C[data]
    A --> D[google.oss.licenses]
    B --> E[core:android]

    subgraph "Core Dependencies"
        B
        C
        E
    end

    style A fill: #4CAF50, stroke: #333, stroke-width: 2px
    style B fill: #64B5F6, stroke: #333, stroke-width: 2px
    style C fill: #64B5F6, stroke: #333, stroke-width: 2px
    style D fill: #FF7043, stroke: #333, stroke-width: 2px
    style E fill: #64B5F6, stroke: #333, stroke-width: 2px
```

## Usage

```kotlin
dependencies {
    implementation(project(":feature:settings"))
}
```

### Settings Dialog

```kotlin
@Composable
fun SettingsDialog(
    onDismiss: () -> Unit,
    onShowSnackbar: suspend (String, SnackbarAction, Throwable?) -> Boolean
)
```

### Key Features

1. **Theme Settings**:

	```kotlin
	@Composable
	fun ThemeSettings(
	   darkThemeConfig: DarkThemeConfig,
	   useDynamicColor: Boolean,
	   onDarkThemeConfigChange: (DarkThemeConfig) -> Unit,
	   onUseDynamicColorChange: (Boolean) -> Unit
	)
	```

2. **Profile Settings**:

	```kotlin
	@Composable
	fun ProfileSettings(
	   onSignOut: () -> Unit,
	   onShowLicenses: () -> Unit
	)
	```

The module uses DataStore Preferences for persistent storage of user settings.