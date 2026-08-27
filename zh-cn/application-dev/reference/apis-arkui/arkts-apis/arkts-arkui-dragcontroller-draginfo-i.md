# DragInfo

发起拖拽所需要的属性和拖拽时携带的信息。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## autoHideComponentUniqueIds

```TypeScript
autoHideComponentUniqueIds?: number | number[]
```

设置在主动拖拽过程中由系统自动隐藏的组件uniqueId，支持传入单个uniqueId或数组。主动拖拽成功发起后，系统会在显示拖拽预览窗口前自动隐藏目标组件。若主动拖拽源本身也需要被隐藏，需要同时传入其uniqueId。组件的uniqueId可通过[UIContext.getFrameNodeById()](arkts-arkui-arkui-uicontext-uicontext-c.md#getframenodebyid) 配合[FrameNode.getUniqueId()](arkts-arkui-framenode-c.md#getuniqueid)获取。开发者需要在拖拽结束回调中按需恢复组件显示状态。

**类型：** number \| number[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## data

```TypeScript
data?: unifiedDataChannel.UnifiedData
```

设置拖拽过程中携带的数据。默认值：空

**类型：** unifiedDataChannel.UnifiedData

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dataLoadParams

```TypeScript
dataLoadParams?: unifiedDataChannel.DataLoadParams
```

设置拖起方延迟提供数据。调用此方法向系统提供数据加载参数，而非直接传入完整的数据对象。当用户将数据拖拽至目标应用程序并释放时，系统将使用此参数从起拖方请求实际数据。与data同时设置时，dataLoadParams生效。默认值：空

**类型：** unifiedDataChannel.DataLoadParams

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams?: string
```

设置拖拽事件额外信息，具体功能暂未实现。默认值：空

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pointerId

```TypeScript
pointerId: number
```

设置启动拖拽时屏幕上触摸点的Id。取值范围为[0, 9]的整数。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewOptions

```TypeScript
previewOptions?: DragPreviewOptions
```

设置拖拽过程中背板图处理模式及数量角标的显示。

**类型：** [DragPreviewOptions](../arkts-components/arkts-arkui-dragpreviewoptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## touchPoint

```TypeScript
touchPoint?: TouchPoint
```

配置跟手点坐标。不配置时，左右居中，顶部向下偏移20%。

**类型：** TouchPoint

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

从API版本26.0.0开始，DragInfo新增autoHideComponentUniqueIds属性。

```TypeScript
import { dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@Component
struct DragInfoAutoHideSample {
  @State sourceVisibility: Visibility = Visibility.Visible;
  @State badgeVisibility: Visibility = Visibility.Visible;
  @State statusText: string = '状态：等待主动拖拽';

  @Builder
  PreviewBuilder() {
    Text('Drag Preview')
      .width(140)
      .height(60)
      .backgroundColor('#3F51B5')
      .borderRadius(10)
      .fontColor(Color.White);
  }

  private buildData(content: string): unifiedDataChannel.UnifiedData {
    let plainText = new unifiedDataChannel.PlainText();
    plainText.textContent = content;
    plainText.abstract = content;
    return new unifiedDataChannel.UnifiedData(plainText);
  }

  private collectHideIds(): number[] {
    let hideIds: number[] = [];
    let sourceNode = this.getUIContext().getFrameNodeById('active_source');
    let badgeNode = this.getUIContext().getFrameNodeById('active_badge');
    if (sourceNode?.getUniqueId() !== undefined) {
      hideIds.push(sourceNode.getUniqueId());
    }
    if (badgeNode?.getUniqueId() !== undefined) {
      hideIds.push(badgeNode.getUniqueId());
    }
    return hideIds;
  }

  private hideTargets(): void {
    this.sourceVisibility = Visibility.Hidden;
    this.badgeVisibility = Visibility.Hidden;
    this.statusText = '状态：主动拖拽中，目标组件已隐藏';
  }

  private restoreTargets(): void {
    this.sourceVisibility = Visibility.Visible;
    this.badgeVisibility = Visibility.Visible;
    this.statusText = '状态：拖拽结束，组件已恢复显示';
  }

  build() {
    Column({ space: 12 }) {
      Text(this.statusText)
        .width('100%')
        .fontSize(14)
        .fontColor('#BF360C');

      Row({ space: 12 }) {
        Column() {
          Text('主动拖拽源')
            .fontColor(Color.White)
            .fontWeight(FontWeight.Medium);
          Text('id: active_source')
            .fontSize(10)
            .fontColor('#E8F5E9');
        }
          .id('active_source')
          .width(140)
          .height(90)
          .backgroundColor('#2E7D32')
          .borderRadius(12)
          .justifyContent(FlexAlign.Center)
          .visibility(this.sourceVisibility);

        Column() {
          Text('跟随隐藏组件')
            .fontColor(Color.White)
            .fontWeight(FontWeight.Medium);
          Text('id: active_badge')
            .fontSize(10)
            .fontColor('#E3F2FD');
        }
          .id('active_badge')
          .width(140)
          .height(90)
          .backgroundColor('#1565C0')
          .borderRadius(12)
          .justifyContent(FlexAlign.Center)
          .visibility(this.badgeVisibility);
      }

      Button('发起主动拖拽')
        .width('100%')
        .height(56)
        .backgroundColor('#FF8F00')
        .onTouch((touchEvent) => {
          if (!touchEvent || touchEvent.type !== TouchType.Down) {
            return;
          }
          let hideIds = this.collectHideIds();
          let dragInfo: dragController.DragInfo = {
            pointerId: 0,
            data: this.buildData('active drag data'),
            extraParams: '',
            autoHideComponentUniqueIds: hideIds
          };
          this.hideTargets();
          this.getUIContext().getDragController().executeDrag(() => {
            this.PreviewBuilder();
          }, dragInfo, () => {
            this.restoreTargets();
          });
        })
    }
    .width('100%')
    .padding(16)
  }
}
```
