# ArcAlphabetIndexer

弧形索引条是一种弧形的、可按字母顺序排序进行快速定位的组件，可以与容器组件联动，按逻辑结构快速定位至容器显示区域。

> **说明：**

> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

## 子组件

无

## ArcAlphabetIndexer

```TypeScript
ArcAlphabetIndexer(info: ArcAlphabetIndexerInitInfo)
```

创建并初始化弧形索引条组件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ArcAlphabetIndexerInitInfo](arkts-arkui-arcalphabetindexer-comp-arcalphabetindexerinitinfo-i.md) | 是 | 定义弧形字母索引条的初始化参数，包含字母索引字符串数组和初始选中项索引值。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcAlphabetIndexerInitInfo](arkts-arkui-arcalphabetindexer-comp-arcalphabetindexerinitinfo-i.md) | 定义弧形字母索引条的初始化参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnSelectCallback](arkts-arkui-arcalphabetindexer-comp-onselectcallback-t.md) | 定义[onSelect](arkts-arkui-arcalphabetindexer-comp-attribute.md#onselect)中使用的回调类型。 |

## 示例

### 示例1（设置联动控制和定位）

该示例实现了弧形索引条和弧形列表联动控制和定位。



```TypeScript
// xxx.ets
import {
  LengthMetrics,
  ColorMetrics,
  ArcList,
  ArcListItem,
  ArcListAttribute,
  ArcListItemAttribute,
  ArcAlphabetIndexer,
  ArcAlphabetIndexerAttribute
} from '@kit.ArkUI';
// 本示例代码兼容API version 21及之前版本，因此手动导入了ArcListAttribute、ArcListItemAttribute、ArcAlphabetIndexerAttribute。从API version 22开始，无需手动导入这些Attribute类型。具体请参考ArcList、ArcListItem、ArcAlphabetIndexer的导入模块说明。

@Entry
@Component
struct ArcListAndIndexer {
  private fullValue: string[] = [
    '#', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'
  ];
  private arrName : string[] = [
    '1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17','18','19','20',
    '21','22','23','24','25','26','27','28','29','30','31','32','33','34','35','36','37','38',
    '39','40', '41','42',
  ];

  private scrollerForList: Scroller = new Scroller();
  @State indexerIndex: number = 0;

  private watchSize: string = '466px'; // 手表默认宽高：233*233
  private itemSize: number = 24;  // 索引项默认大小：24

  build() {
    Column() {
      Row() {
        Stack() {
          ArcList({ scroller: this.scrollerForList, initialIndex: 0 }) {
            ForEach(this.arrName, (itemName: string, index: number) => {
              ArcListItem() {
                Text(itemName)
                  .width('90%')
                  .height('92px')
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(index % 2 == 0 ? 0xAFEEEE : 0x00FFFF)
                  .borderRadius(23)
              }
            })
          }
          .scrollBar(BarState.Off)
          .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
            this.indexerIndex = centerIndex;
          })
          .borderWidth(1)
          .width(this.watchSize)
          .height(this.watchSize)
          .borderRadius(this.watchSize)
          .space(LengthMetrics.px(4))

          ArcAlphabetIndexer({ arrayValue: this.fullValue, selected: 0 })
            .autoCollapse(true)
            .width(this.watchSize)
            .height(this.watchSize)
            .usePopup(false)
            .selected(this.indexerIndex)
            .onSelect((index: number) => {
              this.indexerIndex = index;
              this.scrollerForList.scrollToIndex(this.indexerIndex);
            })
            .borderWidth(1)
            .hitTestBehavior(HitTestMode.Transparent)
            .selectedColor(ColorMetrics.resourceColor(0xFFFFFF))
            .selectedBackgroundColor(ColorMetrics.resourceColor(0x1F71FF))
            .color(ColorMetrics.resourceColor(0xFFFFFF))
            .itemSize(LengthMetrics.px(this.itemSize))
            .selectedFont({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })
            .font({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })

        }.width('100%').height('100%')
        .backgroundColor(Color.Pink)
      }.width('100%').height('100%')
    }
  }
}
```

### 示例2（设置弹窗显示）

该示例通过[popupColor](#popupcolor)和[popupBackground](#popupbackground)接口实现了提示弹窗的显示背景颜色和文字颜色。

从API version 18开始，支持popupColor和popupBackground接口。

```TypeScript
// xxx.ets
import {
  LengthMetrics,
  ColorMetrics,
  ArcList,
  ArcListItem,
  ArcListAttribute,
  ArcListItemAttribute,
  ArcAlphabetIndexer,
  ArcAlphabetIndexerAttribute
} from '@kit.ArkUI';
// 从API version 22开始，无需手动导入ArcListAttribute、ArcListItemAttribute、ArcAlphabetIndexerAttribute。具体请参考ArcList、ArcListItem、ArcAlphabetIndexer的导入模块说明。

@Entry
@Component
struct ArcListAndIndexer {
  private fullValue: string[] = [
    '#', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'
  ];
  private arrName : string[] = [
    '1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17','18','19','20',
    '21','22','23','24','25','26','27','28','29','30','31','32','33','34','35','36','37','38',
    '39','40', '41','42',
  ];

  private scrollerForList: Scroller = new Scroller();
  @State indexerIndex: number = 0;

  private watchSize: string = '466px'; // 手表默认宽高：233*233
  private itemSize: number = 24;  // 索引项默认大小：24

  build() {
    Column() {
      Row() {
        Stack() {
          ArcList({ scroller : this.scrollerForList, initialIndex: 0 }) {
            ForEach(this.arrName, (itemName: string, index: number) => {
              ArcListItem() {
                Text(itemName)
                  .width('90%')
                  .height('92px')
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(index % 2 == 0 ? 0xAFEEEE : 0x00FFFF)
                  .borderRadius(23)
              }
            })
          }
          .scrollBar(BarState.Off)
          .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
            this.indexerIndex = centerIndex;
          })
          .borderWidth(1)
          .width(this.watchSize)
          .height(this.watchSize)
          .borderRadius(this.watchSize)
          .space(LengthMetrics.px(4))

          ArcAlphabetIndexer({ arrayValue: this.fullValue, selected: 0 })
            .autoCollapse(true)
            .width(this.watchSize)
            .height(this.watchSize)
            .usePopup(true)
            .selected(this.indexerIndex)
            .onSelect((index: number) => {
              this.indexerIndex = index;
              this.scrollerForList.scrollToIndex(this.indexerIndex);
            })
            .selectedColor(ColorMetrics.resourceColor(0xFFFFFF))
            .selectedBackgroundColor(ColorMetrics.resourceColor(0x1F71FF))
            .color(ColorMetrics.resourceColor(0xFFFFFF))
            .popupColor(ColorMetrics.resourceColor(0xFFFFFF))
            .popupBackground(ColorMetrics.resourceColor(0xD8404040))
            .popupFont({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })

        }.width('100%').height('100%')
        .backgroundColor(Color.Pink)
      }.width('100%').height('100%')
    }
  }
}
```
