# 自定义输入光标及选择手柄颜色
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @hwt00888022-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

从API 26.1.0开始，Stage模型应用可以通过Web组件的[caretColor](../reference/apis-arkweb/arkts-basic-components-web-attributes.md#caretcolor)属性设置网页输入光标、文本选择手柄外圈及连接线的颜色。

## 设置颜色与重置

| 应用设置 | 输入光标 | 选择手柄 |
| --- | --- | --- |
| 未调用caretColor | 使用网页CSS `caret-color`；CSS为auto或未设置时使用内核默认行为 | 使用当前主题颜色 |
| 非零API颜色 | 覆盖CSS显式颜色、transparent、auto及未声明的情况 | 外圈与连接线使用API颜色 |
| 精确零字符串`'#00000000'` | 恢复CSS及内核默认行为 | 外圈与连接线恢复主题 |

手柄内圈和文字选区背景不受本属性影响。重置应使用精确零字符串，数值`0`会按现有颜色规则补全透明度，不能等同重置。API颜色覆盖不修改网页的CSS声明，`getComputedStyle`得到的CSS `caret-color`不能作为API最终绘制色的判断依据。

## 应用自行适配深浅色

应用应根据网页背景选择适合的颜色；本属性不会自动选择深浅色颜色，也不保证对比度。可以在应用中配置对应模式的颜色资源，或监听实际模式变化后重新设置颜色。

下面的完整示例使用应用配置回调和AppStorage，在应用启用适配后主动下发浅色红、深色绿。颜色仅用于演示，产品应按实际配色选择。网页配色通过WebDarkMode.Auto跟随系统，相关背景适配参见[Web深色模式适配](web-set-dark-mode.md)。

## 完整示例

1. 在EntryAbility中读取实际颜色模式，将配置变化更新到AppStorage。未明确的配置先尝试资源管理器当前模式；读取失败时保留“未获取”状态。

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

2. 在`entry/src/main/ets/pages/Index.ets`中创建Web组件。按钮设置固定颜色或重置时退出应用自动适配，启用适配后监听真实模式变化并重新设置颜色。

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

3. 在`entry/src/main/resources/rawfile/caret_color.html`中创建网页。示例分别提供CSS蓝色、透明和auto的三种编辑区。

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

## 验证操作与预期

- 点击Red或Green，再点击网页编辑区，让输入光标出现。非零API颜色应覆盖三个编辑区原有的CSS光标色。
- 点击Reset，再点击编辑区：input恢复CSS蓝色；textarea的光标不可见；contenteditable恢复auto对应的内核默认行为。长按选择文字时，手柄外圈及连接线恢复当前主题。
- 点击Enable application theme adaptation，通过系统设置切换深浅色后回到同一页面。应用模式文字应更新；浅色下发红色，深色下发绿色。不要重新创建Web来替代同一组件的属性更新验证。
- 长按选择文本观察手柄外圈及连接线，内圈与选区背景不应被API颜色覆盖。设置颜色的按钮可能影响焦点或选区，应重新进入编辑/选择状态后观察。

最终形状、透明度和像素颜色还会受到光标形状及网页暗化处理影响。示例说明应用的设置方式，不承诺任意强制暗化环境中的原始ARGB像素保真。
