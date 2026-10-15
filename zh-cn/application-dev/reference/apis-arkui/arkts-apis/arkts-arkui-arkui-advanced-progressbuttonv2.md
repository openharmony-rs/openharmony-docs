# @ohos.arkui.advanced.ProgressButtonV2

文本下载按钮，可显示具体的下载进度。

该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制文本下载按钮的数据和状态，实现更高效的用户界面刷新。


## 导入模块

```TypeScript
import { ProgressButtonV2, ProgressButtonV2Color, ProgressButtonV2ColorOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ProgressButtonV2Color](arkts-arkui-arkui-advanced-progressbuttonv2-progressbuttonv2color-c.md) | 下载按钮颜色选项。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ProgressButtonV2](arkts-arkui-arkui-advanced-progressbuttonv2-progressbuttonv2-s.md) | 创建ProgressButtonV2组件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ProgressButtonV2ColorOptions](arkts-arkui-arkui-advanced-progressbuttonv2-progressbuttonv2coloroptions-i.md) | 下载按钮色彩信息选项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ClickCallback](arkts-arkui-clickcallback-t.md) | 下载按钮的点击回调。 |

## 示例

该示例实现了一个简单的带加载进度的文本下载按钮。

```TypeScript
import { LengthMetrics, ProgressButtonV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local progressIndex: number = 0;
  @Local textState: string = '下载';
  @Local buttonWidth: LengthMetrics = LengthMetrics.vp(200);
  @Local isRunning: boolean = false;
  @Local enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButtonV2({
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            isEnabled: this.enableState,
            onClicked: () => {
              if (this.textState && !this.isRunning && this.progressIndex < 100) {
                this.textState = '继续';
              }
              this.isRunning = !this.isRunning;
              let timer = setInterval(() => {
                if (this.isRunning) {
                  if (this.progressIndex === 100) {
                    clearInterval(timer);
                  } else {
                    this.progressIndex++;
                    if (this.progressIndex === 100) {
                      this.textState = '已完成';
                      this.enableState = false;
                    }
                  }
                } else {
                  clearInterval(timer);
                }
              }, 20);
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 });
      }
    }
  }
}
```
