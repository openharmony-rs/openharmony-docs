# Customizing Caret and Selection Handle Colors
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @hwt00888022-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

Since API 26.1.0, stage model applications can use [caretColor](../reference/apis-arkweb/arkts-basic-components-web-attributes.md#caretcolor) to set the web input caret color, the outer ring of the text selection handles, and their connecting lines.

## Setting and Resetting Colors

| Application setting | Input caret | Selection handles |
| --- | --- | --- |
| caretColor not called | Uses CSS `caret-color`, or the engine default when CSS is auto or not set | Uses current theme colors |
| Non-zero API color | Overrides explicit CSS colors, transparent, auto, and an unset CSS value | Uses the API color for the outer ring and connecting lines |
| Exact zero string `'#00000000'` | Restores CSS and engine default behavior | Restores theme colors for the outer ring and connecting lines |

The inner ring and text selection background are unaffected. Use the exact zero string to reset the attribute. Numeric `0` has its alpha component filled during color parsing and is not equivalent to this reset. The API override does not change the CSS declaration; the CSS `caret-color` returned by `getComputedStyle` does not indicate the final API-rendered color.

## Application-Managed Light and Dark Colors

Applications must select suitable colors for the page background. This attribute does not automatically choose colors for light/dark modes or guarantee contrast. Applications can provide mode-specific color resources or listen for mode changes and set a new color.

The complete example below uses configuration callbacks and AppStorage. Once adaptation is enabled, the application sets red in light mode and green in dark mode. These colors are demonstrations; choose colors appropriate for your product. The page follows the system mode through WebDarkMode.Auto. For background adaptation, see [Setting Dark Mode](web-set-dark-mode.md).

## Complete Example

1. In EntryAbility, obtain the actual color mode and publish configuration changes to AppStorage. If the configuration mode is unset, query the resource manager; retain the unknown state if reading the mode fails.

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import { Configuration } from '@ohos.app.ability.Configuration';
import ConfigurationConstant from '@ohos.app.ability.ConfigurationConstant';
import resourceManager from '@ohos.resourceManager';
import window from '@ohos.window';

export default class EntryAbility extends UIAbility {
  private publishMode(mode?: ConfigurationConstant.ColorMode): void {
    let resolved: number = mode === undefined ? ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET : mode;
    if (resolved === ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET) {
      try {
        const resourceMode = this.context.resourceManager.getConfigurationSync().colorMode;
        resolved = resourceMode === resourceManager.ColorMode.DARK ?
          ConfigurationConstant.ColorMode.COLOR_MODE_DARK : ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT;
      } catch (error) {
        resolved = ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET;
      }
    }
    AppStorage.setOrCreate('caretColorMode', resolved);
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    this.publishMode(this.context.config.colorMode);
    windowStage.loadContent('pages/Index', (error) => {
      if (error.code !== 0) { console.error('Page load failed: ' + error.code.toString()); }
    });
  }

  onConfigurationUpdate(newConfig: Configuration): void {
    this.publishMode(newConfig.colorMode);
  }

  onForeground(): void {
    this.publishMode(this.context.config.colorMode);
  }
}
```

2. Create the Web component in `entry/src/main/ets/pages/Index.ets`. Selecting a fixed color or resetting disables application adaptation. When adaptation is enabled, the page listens for actual mode changes and updates the color.

```ts
// entry/src/main/ets/pages/Index.ets
import webview from '@ohos.web.webview';
import ConfigurationConstant from '@ohos.app.ability.ConfigurationConstant';

@Entry
@Component
struct CaretColorExample {
  private controller: webview.WebviewController = new webview.WebviewController();
  @StorageProp('caretColorMode') @Watch('onColorModeChange') private colorMode: number = -1;
  @State private color: ResourceColor = '#FFFF0000';
  @State private followSystem: boolean = false;

  private onColorModeChange(): void {
    if (this.followSystem) { this.updateThemeColor(); }
  }

  private updateThemeColor(): void {
    if (this.colorMode === ConfigurationConstant.ColorMode.COLOR_MODE_DARK) {
      this.color = '#FF00FF00';
    } else if (this.colorMode === ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT) {
      this.color = '#FFFF0000';
    }
  }

  private modeName(): string {
    if (this.colorMode === ConfigurationConstant.ColorMode.COLOR_MODE_DARK) { return 'Dark'; }
    if (this.colorMode === ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT) { return 'Light'; }
    return 'Unknown';
  }

  build() {
    Column({ space: 8 }) {
      Text('Application mode: ' + this.modeName())
      Row({ space: 8 }) {
        Button('Red').onClick(() => {
          this.followSystem = false;
          this.color = '#FFFF0000';
        })
        Button('Green').onClick(() => {
          this.followSystem = false;
          this.color = '#FF00FF00';
        })
        Button('Reset').onClick(() => {
          this.followSystem = false;
          this.color = '#00000000';
        })
      }
      Button('Enable application theme adaptation').onClick(() => {
        this.followSystem = true;
        this.updateThemeColor();
      })
      Web({ src: $rawfile('caret_color.html'), controller: this.controller })
        .caretColor(this.color)
        .darkMode(WebDarkMode.Auto)
        .width('100%')
        .layoutWeight(1)
    }.width('100%').height('100%')
  }
}
```

3. Create `entry/src/main/resources/rawfile/caret_color.html`. This page contains editable elements with blue, transparent, and auto CSS caret colors.

```html
<!-- entry/src/main/resources/rawfile/caret_color.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    :root { color-scheme: light dark; }
    body { font-family: sans-serif; padding: 12px; }
    input, textarea, [contenteditable] {
      box-sizing: border-box;
      width: 100%;
      min-height: 64px;
      margin-bottom: 16px;
      padding: 10px;
      font-size: 22px;
      border: 1px solid gray;
    }
    input { caret-color: blue; }
    textarea { caret-color: transparent; }
    [contenteditable] { caret-color: auto; }
  </style>
</head>
<body>
  <p>input: CSS blue</p>
  <input value="Tap to edit, or select this text">
  <p>textarea: CSS transparent</p>
  <textarea>API colors override this transparent CSS caret.</textarea>
  <p>contenteditable: CSS auto</p>
  <div contenteditable="true">Edit or select this text to inspect the caret and handles.</div>
</body>
</html>
```

## Verification Steps and Expected Behavior

- Select Red or Green, then tap an editable element to display its caret. The non-zero API color overrides the original CSS caret color in all three elements.
- Select Reset, then tap an editable element. The input returns to CSS blue, the textarea caret becomes invisible, and contenteditable returns to the engine behavior for auto. When text is selected, the handle outer ring and connecting lines return to theme colors.
- Select Enable application theme adaptation, change the system light/dark setting, and return to the same page. The displayed application mode updates; the application sets red in light mode and green in dark mode. Do not recreate the Web component as a substitute for testing an update on the same component.
- Select text to inspect the outer ring and connecting lines. The API color does not override the inner ring or selection background. A color button may affect focus or selection; re-enter the editing/selection state before inspecting the result.

Caret shape and page darkening can affect the final shape, alpha, and pixel color. This example demonstrates application settings and does not guarantee unchanged ARGB pixels under arbitrary forced darkening.
