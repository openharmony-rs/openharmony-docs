# SideBarContainer

提供侧边栏可以显示和隐藏的容器，通过子组件定义侧边栏和内容区，第一个子组件表示侧边栏，第二个子组件表示内容区。
> **说明：**

## 子组件

可以包含子组件。

> **说明：**
> 
> - 子组件类型：系统组件和自定义组件，不支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。
> 
> - 子组件个数：必须且仅包含2个子组件。
> 
> - 子组件个数异常时：3个或以上子组件，显示第一个和第二个。1个子组件，显示侧边栏，内容区为空白。
> 
> - SideBarContainer走焦时，先在内容区走焦，再在侧边栏走焦。

## SideBarContainer

```TypeScript
SideBarContainer(type?: SideBarContainerType)
```

创建侧边栏容器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SideBarContainerType](arkts-arkui-sidebarcontainertype-e.md) | 否 | 设置侧边栏的显示类型。 默认值：SideBarContainerType.Embed |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ButtonIconOptions](arkts-arkui-buttoniconoptions-i.md) | 设置侧边栏控制按钮的图标。 |
| [ButtonStyle](arkts-arkui-buttonstyle-i.md) | 设置侧边栏控制按钮的样式。 |
| [DividerStyle](arkts-arkui-dividerstyle-i.md) | 设置分割线的样式。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SideBarContainerType](arkts-arkui-sidebarcontainertype-e.md) | 容器内侧边栏样式枚举。 |
| [SideBarPosition](arkts-arkui-sidebarposition-e.md) | 侧边栏显示位置。 |

## 示例

该示例主要演示如何使用侧边栏组件及页面布局效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct SideBarContainerExample {
  // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
  normalIcon: Resource = $r('app.media.icon');
  selectedIcon: Resource = $r('app.media.icon');
  @State menuItems: number[] = [1, 2, 3];
  @State selectedItemId: number = 1;

  build() {
    SideBarContainer(SideBarContainerType.Embed) {
      Column() {
        ForEach(this.menuItems, (item: number) => {
          Column({ space: 5 }) {
            Image(this.selectedItemId === item ? this.selectedIcon : this.normalIcon).width(64).height(64)
            Text('Index0' + item)
              .fontSize(25)
              .fontColor(this.selectedItemId === item ? '#0A59F7' : '#999')
              .fontFamily('source-sans-pro,cursive,sans-serif')
          }
          .onClick(() => {
            this.selectedItemId = item;
          })
        }, (item: number) => item.toString())
      }.width('100%')
      .justifyContent(FlexAlign.SpaceEvenly)
      .backgroundColor('#19000000')

      Column() {
        Text('SideBarContainer content text1').fontSize(25)
        Text('SideBarContainer content text2').fontSize(25)
      }
      .margin({ top: 50, left: 20, right: 30 })
    }
    .controlButton({
      icons: {
        // $r('app.media.drawer')需要替换为开发者所需的图像资源文件。
        hidden: $r('app.media.drawer'),
        shown: $r('app.media.drawer'),
        switching: $r('app.media.drawer')
      }
    })
    .sideBarWidth(150)
    .minSideBarWidth(50)
    .maxSideBarWidth(300)
    .minContentWidth(0)
    .onChange((value: boolean) => {
      console.info('status:' + value);
    })
    .divider({ strokeWidth: '1vp', color: Color.Gray, startMargin: '4vp', endMargin: '4vp' })
  }
}
```
