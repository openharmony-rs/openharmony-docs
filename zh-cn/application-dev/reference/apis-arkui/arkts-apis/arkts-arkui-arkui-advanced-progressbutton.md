# @ohos.arkui.advanced.ProgressButton

## 导入模块

```TypeScript
import { ProgressButton } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ProgressButton](arkts-arkui-arkui-advanced-progressbutton-progressbutton-s.md) | 文本下载按钮，可显示具体下载进度。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ProgressButtonColorOptions](arkts-arkui-arkui-advanced-progressbutton-progressbuttoncoloroptions-i.md) | 下载按钮颜色选项 |

## 示例

### 示例1（进度条下载按钮）

该示例实现了一个简单的带加载进度的文本下载按钮。



```TypeScript
import { ProgressButton } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State progressIndex: number = 0;
  @State textState: string = '下载';
  @State buttonWidth: number = 200;
  @State isRunning: boolean = false;
  @State enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButton({
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            enable: this.enableState,
            clickCallback: () => {
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
              }, 20)
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 })
      }
    }
  }
}
```

### 示例2（自定义颜色按钮）

该示例实现了一个简单的自定义颜色的文本下载按钮。



```TypeScript
import { ProgressButton } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State progressIndex: number = 0;
  @State textState: string = '下载';
  @State buttonWidth: number = 200;
  @State isRunning: boolean = false;
  @State enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButton({
            // 设置下载按钮颜色
            colorOptions: {
              progressColor: Color.Orange,
              borderColor: Color.Black,
              textColor: Color.Blue,
              backgroundColor: Color.Pink
            },
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            enable: this.enableState,
            clickCallback: () => {
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
              }, 20)
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 })
      }
    }
  }
}
```

### 示例3（自定义圆角按钮）

该示例实现了一个简单的自定义圆角的文本下载按钮。

```TypeScript
import { ProgressButton, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State progressIndex: number = 0;
  @State textState: string = '下载';
  @State buttonWidth: number = 200;
  @State isRunning: boolean = false;
  @State enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButton({
            progressButtonRadius: LengthMetrics.vp(8), // 自定义圆角值为8vp
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            enable: this.enableState,
            clickCallback: () => {
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
              }, 20)
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 })
      }
    }
  }
}
```
