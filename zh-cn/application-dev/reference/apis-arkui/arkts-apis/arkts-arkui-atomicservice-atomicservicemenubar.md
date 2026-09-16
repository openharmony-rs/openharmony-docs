# @ohos.atomicservice.AtomicServiceMenuBar(系统接口)

## 子组件

无。

## 属性

不支持通用属性。

## 导入模块

```TypeScript
import { AtomicServiceMenuBar } from '@kit.ArkUI';
```

## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceMenuBar](arkts-arkui-atomicservice-atomicservicemenubar-atomicservicemenubar-c-sys.md) | 依赖当前原子化服务的UI上下文，创建AtomicServiceMenuBar对象，用于操控右上角菜单功能胶囊的显隐状态。 |
<!--DelEnd-->

## 示例

```TypeScript
import { AtomicServiceMenuBar } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private menuBar: AtomicServiceMenuBar = new AtomicServiceMenuBar(this.getUIContext());

  @Builder
  private menuCapsuleShow(title: string, text: string, event?: () => void) {
    Column() {
      if (typeof event === 'function') {
        Button(title)
          .width(300)
          .height(50)
          .fontSize(16)
          .borderRadius(25)
          .onClick(() => {
            event();
          })
      }
      Text(`预期现象：${text}`)
        .width(300)
        .textAlign(TextAlign.Start)
        .fontSize(12)
        .margin({ top: 5, bottom: 15})
    }
  }

  build() {
    Column() {
      this.menuCapsuleShow('显示菜单功能胶囊', '点击后菜单功能胶囊显示', () => {
        this.menuBar.setVisible(true);
      });
      this.menuCapsuleShow('隐藏菜单功能胶囊', '点击后菜单功能胶囊隐藏', () => {
        this.menuBar.setVisible(false);
      });
    }
    .width('100%')
    .height('100%')
    .padding({ top: 100 })
  }
}
```
