# @ohos.arkui.advanced.GridObjectSortComponent

## 子组件

无

## 事件

不建议设置通用事件，设置后可能不生效或不符合预期。

## 导入模块

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponent } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [GridObjectSortComponent](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponent-s.md) | 网格对象排序组件，用于网格对象的编辑、拖动排序、新增和删除。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md) | 网格对象排序组件的组件数据配置信息。 |
| [GridObjectSortComponentOptions](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentoptions-i.md) | 网格对象排序组件的组件配置信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GridObjectSortComponentType](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponenttype-e.md) | 配置网格对象排序组件节点的类型，配置名称 IMAGE_TEXT 为图片文字类型，TEXT 为文字类型。 |

## 示例

网格对象的编辑排序组件基础用法，涉及对组件配置信息初始化，数据初始化，保存、取消方法的使用。

```TypeScript
import { GridObjectSortComponent, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponentType, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // 组件数据初始化。
  @State dataList: GridObjectSortComponentItem[] = [
    {
      id: 0,
      url: $r('sys.media.ohos_save_button_filled'),
      text: '下载',
      selected: true,
      order: 3
    },
    {
      id: 1,
      url: $r('sys.media.ohos_ic_public_web'),
      text: '网络',
      selected: true,
      order: 9
    },
    {
      id: 2,
      url: $r('sys.media.ohos_ic_public_video'),
      text: '视频',
      selected: false,
      order: 1
    },
    {
      id: 3,
      symbolStyle: new SymbolGlyphModifier($r('sys.symbol.record_circle')),
      text: '录制',
      selected: false,
      order: 4
    }
  ]

  // 组件配置信息初始化。
  @State option: GridObjectSortComponentOptions = {
    type: GridObjectSortComponentType.IMAGE_TEXT,
    imageSize: 45,
    normalTitle: '菜单',
    editTitle: '编辑',
    showAreaTitle: '长按拖动排序',
    addAreaTitle: '点击添加'
  }

  build() {
    Column() {
      GridObjectSortComponent({
        options: this.option,
        dataList: this.dataList,
        // 保存编辑排序的回调函数，接收编辑后的选中数据和未选中数据。
        onSave: (
          select: Array<GridObjectSortComponentItem>,
          unselect: Array<GridObjectSortComponentItem>
        ) => {
          // save ToDo
        },
        // 取消保存数据的回调。
        onCancel: () =>{
          // cancel ToDo
        }
      })
    }
  }
}
```
