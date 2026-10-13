# Epicollect5 Capacitor Theme Plugin

Native companion to the in-app Light / Dark / System theme: pins Android night
mode (`AppCompatDelegate.setDefaultNightMode`) and the iOS window interface
style + brand tint (`overrideUserInterfaceStyle`, `tintColor`) so OS-rendered
dialogs and pickers follow the in-app choice instead of the device theme.

Github-only distribution (never published to npm), same as the other
Epicollect5 forks. Install pinned:

```json
"@epicollect5/capacitor-plugin-theme": "github:epicollect5/capacitor-plugin-theme#v1.0.0"
```

## JS contract

No JS wrapper is shipped — call through `@capacitor/core` (native-only,
guard by platform):

```js
import {Capacitor, registerPlugin} from '@capacitor/core';

const themePlugin = registerPlugin('Theme');
if (platform === 'android' || platform === 'ios') {
    themePlugin.setTheme({theme: preference}); // 'light' | 'dark' | 'system'
}
```

Any other `theme` value rejects (`Invalid theme: ...`).
