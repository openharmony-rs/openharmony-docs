# 页面级像素取整

页面级像素取整的目标是将像素取整模式设为页面的上下文属性，以便在页面层面设置像素取整模式。

>  **说明：**
>
> - 本模块从API version 18开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。 
> - 若出现像素取整[问题](ts-universal-attributes-pixelRoundForComponent.md#常见问题)，且使用[组件级像素取整](./ts-universal-attributes-pixelRoundForComponent.md)无法解决时，建议尝试采用PIXEL_ROUND_AFTER_MEASURE模式。
> - 在PIXEL_ROUND_AFTER_MEASURE模式下，组件会在测量大小结束时进行取整，即最终大小相比于PIXEL_ROUND_ON_LAYOUT_FINISH模式可能扩大1px。
> - 页面级像素取整与组件级像素取整的区别在于：页面级像素取整调整整个页面的像素取整时机，而组件级像素取整调整特定组件在特定方向上的像素取整对齐方式。

## setPixelRoundMode

setPixelRoundMode(mode: PixelRoundMode): void

设置当前页面的像素取整模式。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型         | 必填   | 说明   |
| -------- | ---------- | ---- | ---- |
| mode | [PixelRoundMode](./ts-appendix-enums.md#pixelroundmode18)| 是    | 像素取整模式。<br />默认值：PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH |

**示例：**

```ts
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
   windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext :UIContext = windowStage.getMainWindowSync().getUIContext();
      uiContext.setPixelRoundMode(PixelRoundMode.PIXEL_ROUND_AFTER_MEASURE);
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
```

## getPixelRoundMode

getPixelRoundMode(): PixelRoundMode

获取当前页面的像素取整模式。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型         | 说明   |
| ---------- | ---- |
| [PixelRoundMode](./ts-appendix-enums.md#pixelroundmode18)| 当前页面的像素取整模式。|

**示例：**

```ts
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      console.info("pixelRoundMode : " + uiContext.getPixelRoundMode().valueOf());
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
```