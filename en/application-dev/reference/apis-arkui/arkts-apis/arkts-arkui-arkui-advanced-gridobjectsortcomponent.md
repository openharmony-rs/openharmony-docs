# @ohos.arkui.advanced.GridObjectSortComponent

## Child Components

Not supported

## Events

The [universal events](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponent } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [GridObjectSortComponent](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponent-s.md) | **GridObjectSortComponent** is a grid object organizer that you can use to edit, drag to sort, add, and delete grid objects. |

### Interfaces

| Name | Description |
| --- | --- |
| [GridObjectSortComponentItem](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentitem-i.md) | Provides data item configuration for the **GridObjectSortComponent** component. |
| [GridObjectSortComponentOptions](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponentoptions-i.md) | Provides configuration options for the **GridObjectSortComponent** component. |

### Enums

| Name | Description |
| --- | --- |
| [GridObjectSortComponentType](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponenttype-e.md) | Enumerates display types for nodes in the **GridObjectSortComponent** component. |

## Examples

This example illustrates the basic usage of the GridObjectSortComponent component, involving component configuration initialization, data initialization, and the use of the save and cancel APIs.

```TypeScript
import { GridObjectSortComponent, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponentType, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Initialize the component data.
  @State dataList: GridObjectSortComponentItem[] = [
    {
      id: 0,
      url: $r('sys.media.ohos_save_button_filled'),
      text: 'Download',
      selected: true,
      order: 3
    },
    {
      id: 1,
      url: $r('sys.media.ohos_ic_public_web'),
      text: 'Network',
      selected: true,
      order: 9
    },
    {
      id: 2,
      url: $r('sys.media.ohos_ic_public_video'),
      text: 'Video',
      selected: false,
      order: 1
    },
    {
      id: 3,
      symbolStyle: new SymbolGlyphModifier($r('sys.symbol.record_circle')),
      text: 'Record',
      selected: false,
      order: 4
    }
  ]

  // Initialize the component configuration information.
  @State option: GridObjectSortComponentOptions = {
    type: GridObjectSortComponentType.IMAGE_TEXT,
    imageSize: 45,
    normalTitle: 'Menu',
    editTitle: 'Edit',
    showAreaTitle: 'Drag to sort',
    addAreaTitle: 'Tap to add'
  }

  build() {
    Column() {
      GridObjectSortComponent({
        options: this.option,
        dataList: this.dataList,
        // Callback invoked when changes are saved. The data after the changes is returned.
        onSave: (
          select: Array<GridObjectSortComponentItem>,
          unselect: Array<GridObjectSortComponentItem>
        ) => {
          // save ToDo
        },
        // Callback invoked when changes are canceled.
        onCancel: () =>{
          // cancel ToDo
        }
      })
    }
  }
}
```
