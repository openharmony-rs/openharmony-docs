# @ohos.atomicservice.AtomicServiceSearch(This section describes the interfaces used by AtomicServiceSearch)

## Modules to Import

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [AtomicServiceSearch](arkts-arkui-atomicservice-atomicservicesearch-atomicservicesearch-s.md) | **AtomicServiceSearch** allows you to customize the default search area, customizable selection area, and function area (a maximum of two). |

### Interfaces

| Name | Description |
| --- | --- |
| [InputFilterParams](arkts-arkui-atomicservice-atomicservicesearch-inputfilterparams-i.md) | Sets regular expression for input filtering. |
| [MenuAlignParams](arkts-arkui-atomicservice-atomicservicesearch-menualignparams-i.md) | Sets the alignment between the drop-down list button and the drop-down list box. |
| [OperationParams](arkts-arkui-atomicservice-atomicservicesearch-operationparams-i.md) | Sets initialization parameters of the function area. |
| [SearchButtonParams](arkts-arkui-atomicservice-atomicservicesearch-searchbuttonparams-i.md) | Sets the search button located next to the search text box. |
| [SearchParams](arkts-arkui-atomicservice-atomicservicesearch-searchparams-i.md) | Provides optional attributes for the search area. |
| [SelectParams](arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md) | Provides optional attributes for the selection area. |

### Types

| Name | Description |
| --- | --- |
| [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | Called when the text content is scrolled. |
| [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | Called when a paste operation is performed. |
| [OnSelectCallback](arkts-arkui-onselectcallback-t.md) | Called when an item in the drop-down list box is selected. |
| [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | Called when the position of the text selection changes or when the cursor position changes during the editing state. |

## Examples

### Example 1: Adding a Selection Area to AtomicServiceSearch

This example demonstrates how to use the select parameter to add a selection area on the left to the AtomicServiceSearch component.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 6 }) {
      Text('AtomicServiceSearch + selection area').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        select: {
          options: [
            { value: 'Select1', icon: $r('app.media.sweep') }, // Custom resource
            { value: 'Select2', icon: $r('app.media.sweep') }, // Custom resource
            { value: 'Select3', icon: $r('app.media.sweep') }, // Custom resource
            { value: 'Select4', icon: $r('app.media.sweep') } // Custom resource
          ],
          selected: -1,
          selectValue: 'Select1',
          onSelect: (index: number, selectValue: string) => { // Custom event
            if (index === 0) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            } else if (index === 1) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            } else if (index === 2) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            } else if (index === 3) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            }
          },
        }
      })
    }.padding({ left: 16, right: 16 })
  }

  private alert(message: string): void {
    this.getUIContext().showAlertDialog({ message: message });
  }
}
```

### Example 2: Adding a Function Item to AtomicServiceSearch

This example demonstrates how to use the operation parameter to add a function item on the right to the AtomicServiceSearch component.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 6 }) {
      Text('AtomicServiceSearch + function items').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })
      
      AtomicServiceSearch({
        operation: {
          // Auxiliary item of the Search component.
          auxiliaryItem: {
            value: $r('app.media.sweep'), // Custom resource.
            action: () => {
              this.alert('Scan'); // Custom event
            }
          },
          // Independent item of the Search component.
          independentItem: {
            value: $r('app.media.dingding'), // Custom resource.
            action: () => {
              this.alert('Notifications'); // Custom event
            }
          }
        }
      })
    }.padding({ left: 16, right: 16 })
  }

  private alert(message: string): void {
    this.getUIContext().showAlertDialog({ message: message });
  }
}
```

### Example 3: Adding a Selection Area and Function Item to AtomicServiceSearch

This example demonstrates how to add the selection area and function items on the left and right to the AtomicServiceSearch component.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 6 }) {
      Text('AtomicServiceSearch + selection area + function items').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        select: {
          options: [
            { value: 'Select1', icon: $r('app.media.sweep') }, // Custom resource.
            { value: 'Select2', icon: $r('app.media.sweep') }, // Custom resource.
            { value: 'Select3', icon: $r('app.media.sweep') }, // Custom resource.
            { value: 'Select4', icon: $r('app.media.sweep') } // Custom resource.
          ],
          selected: -1,
          selectValue: 'Select1',
          onSelect: (index: number, selectValue:string) => {
            if (index === 0) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            } else if (index === 1) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            } else if (index === 2) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            } else if (index === 3) {
              this.alert(`index: ${index}, selectValue: ${selectValue}`);
            }
          },
        },
        operation: {
          auxiliaryItem: {
            value: $r('app.media.sweep'), // Custom resource.
            action: () => {
              this.alert('Scan'); // Custom event
            }
          },
          independentItem: {
            value: $r('app.media.dingding'), // Custom resource.
            action: () => {
              this.alert('Notifications'); // Custom event
            }
          }
        }
      })
    }.padding({ left: 16, right: 16 })
  }

  private alert(message: string): void {
    this.getUIContext().showAlertDialog({ message: message });
  }
}
```

### Example 4: Binding the Search Callback Events to AtomicServiceSearch

This example demonstrates how to use the onWillInsert, onDidInsert, onWillDelete, and onDidDelete APIs to implement insert and delete operations.

The onSubmit API is used to submit content in the search area.

The onChange API is used to listen for the content changes in the search area.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State insertValue: string = '';
  @State deleteValue: string = '';
  @State insertOffset: number = 0;
  @State deleteOffset: number = 0;
  @State deleteDirection: number = 0;
  @State startIndex: number = 0;
  @State endIndex: number = 0;
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State changeValue: string = '';
  @State editingState: string = 'false';
  @State submitValue: string = '';

  build() {
    Column({ space: 6 }) {
      Text('Binding events to AtomicServiceSearch').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      Column({ space: 6 }) {
        Text('editing: ' + this.editingState).width('100%').height(25).borderRadius(15).padding({ left: 15 })
          .backgroundColor('rgba(0, 0, 0, 0.1)').maxLines(1).textOverflow({ overflow: TextOverflow.MARQUEE });
        Text('onSubmit:' + this.submitValue).width('100%').height(25).borderRadius(15).padding({ left: 15 })
          .backgroundColor('rgba(0, 0, 0, 0.1)').maxLines(1).textOverflow({ overflow: TextOverflow.MARQUEE });
        Text('onChange:' + this.changeValue).width('100%').height(25).borderRadius(15).padding({ left: 15 })
          .backgroundColor('rgba(0, 0, 0, 0.1)').maxLines(1).textOverflow({ overflow: TextOverflow.MARQUEE });
        Text('offset x:' + this.offsetX + ' y:' + this.offsetY).width('100%').height(25).borderRadius(15).padding({ left: 15 })
          .backgroundColor('rgba(0, 0, 0, 0.1)').maxLines(1).textOverflow({ overflow: TextOverflow.MARQUEE });
        Text('insertValue:' + this.insertValue + '  insertOffset:' + this.insertOffset).width('100%').height(25)
          .borderRadius(15).padding({ left: 15 }).backgroundColor('rgba(0, 0, 0, 0.1)').maxLines(1)
          .textOverflow({ overflow: TextOverflow.MARQUEE });
        Text('deleteValue:' + this.deleteValue + '  deleteOffset:' + this.deleteOffset).width('100%').height(25)
          .borderRadius(15).padding({ left: 15 }).backgroundColor('rgba(0, 0, 0, 0.1)').maxLines(1)
          .textOverflow({ overflow: TextOverflow.MARQUEE });
        Text('deleteDirection:' + (this.deleteDirection == 0 ? 'BACKWARD' : 'FORWARD')).width('100%').height(25)
          .borderRadius(15).padding({ left: 15 }).backgroundColor('rgba(0, 0, 0, 0.1)').maxLines(1)
          .textOverflow({ overflow: TextOverflow.MARQUEE });
        AtomicServiceSearch({
          select: {
            options: [
              { value: 'Select1', icon: $r('app.media.sweep') },
              { value: 'Select2', icon: $r('app.media.sweep') },
              { value: 'Select3', icon: $r('app.media.sweep') },
              { value: 'Select4', icon: $r('app.media.sweep') }
            ],
            selected: -1,
            selectValue: 'Select1',
            onSelect: (index: number) => {
              if (index === 0) {
                this.alert('Select1');
              } else if (index === 1) {
                this.alert('Select2');
              } else if (index === 2) {
                this.alert('Select3');
              } else if (index === 3) {
                this.alert('Select4');
              }
            },
          },
          search: {
            onSubmit: (value: string) => {
              this.submitValue = value;
            },
            onChange: (value: string) => {
              this.changeValue = value;
            },
            onCopy: () => {
              this.alert('onCopy');
            },
            onCut: () => {
              this.alert('onCut');
            },
            onPaste: () => {
              this.alert('onPaste');
            },
            onTextSelectionChange: (selectionStart: number, selectionEnd: number) => {
              this.startIndex = selectionStart;
              this.endIndex = selectionEnd;
            },
            onContentScroll: (totalOffsetX: number, totalOffsetY: number) => {
              this.offsetX = totalOffsetX;
              this.offsetY = totalOffsetY;
            },
            onEditChange: (data: boolean) => {
              this.editingState = data ? 'true' : 'false';
            },
            onWillInsert: (info: InsertValue) => {
              this.insertValue = info.insertValue;
              return true;
            },
            onDidInsert: (info: InsertValue) => {
              this.insertOffset = info.insertOffset;
            },
            onWillDelete: (info: DeleteValue) => {
              this.deleteValue = info.deleteValue;
              return true;
            },
            onDidDelete: (info: DeleteValue) => {
              this.deleteOffset = info.deleteOffset;
              this.deleteDirection = info.direction;
            }
          }
        })
      }
    }.padding({ left: 16, right: 16 })
  }

  private alert(message: string): void {
    this.getUIContext().showAlertDialog({ message: message });
  }
}
```

### Example 5: Customizing the Style of AtomicServiceSearch

This example demonstrates how to use the search, select, value, and placeholder parameters to customize the style of the AtomicServiceSearch component.



```TypeScript
import { AtomicServiceSearch, SearchParams, SelectParams } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State private placeholder: string = 'Type to Search...';
  @State private defaultValue: string = 'default';
  @State private search?: SearchParams = {};
  @State private select?: SelectParams = {
    options: [
      { value: 'Select1', icon: $r('app.media.sweep') },
      { value: 'Select2', icon: $r('app.media.sweep') },
      { value: 'Select3', icon: $r('app.media.sweep') },
      { value: 'Select4', icon: $r('app.media.sweep') }
    ],
    selected: -1,
    selectValue: 'Select1',
    onSelect: (index: number) => {
      if (index === 0) {
        this.alert('Select1');
      } else if (index === 1) {
        this.alert('Select2');
      } else if (index === 2) {
        this.alert('Select3');
      } else if (index === 3) {
        this.alert('Select4');
      }
    }
  };

  build() {
    Column({ space: 8 }) {
      Text('Customizing styles').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        value: this.defaultValue,
        placeholder: this.placeholder,
        select: this.select,
        search: this.search,
        operation: {
          independentItem: {
            value: $r('app.media.dingding'),
            action: () => {
              this.alert('Notification');
            }
          }
        }
      })
      Button('Change placeholder')
        .width('100%')
        .type(ButtonType.Normal)
        .borderRadius(20)
        .onClick(() => {
          if (this.placeholder === 'Search...') {
            this.placeholder = 'Type to Search...';
          } else {
            this.placeholder = 'Search...';
          }
        });
      Button('Change defaultValue')
        .width('100%')
        .type(ButtonType.Normal)
        .borderRadius(20)
        .onClick(() => {
          if (this.defaultValue === 'value') {
            this.defaultValue = 'defaultValue';
          } else {
            this.defaultValue = 'value';
          }
        });
      Button('Change selection area style')
        .width('100%')
        .type(ButtonType.Normal)
        .borderRadius(20)
        .onClick(() => {
          this.select = {
            options: [
              { value: 'Option 1', icon: $r('app.media.dingding') },
              { value: 'Option 2', icon: $r('app.media.dingding') },
            ],
            selected: -1,
            selectValue: 'Option 1',
            onSelect: (index: number) => {
              if (index === 0) {
                this.alert('Option 1');
              } else if (index === 1) {
                this.alert('Option 2');
              }
            }
          };
        });

      Button('Change search area Style')
        .width('100%')
        .type(ButtonType.Normal)
        .borderRadius(20)
        .onClick(() => {
          this.search = {
            componentBackgroundColor: '#e0eee8'
          }
        });
    }.padding({ left: 16, right: 16 })
  }

  private alert(message: string): void {
    this.getUIContext().showAlertDialog({ message: message });
  }
}
```

### Example 6: Setting the Caret Position Using controller

This example demonstrates how to use the controller parameter to set the caret position, select the content in the specified area, and disable the editing state.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  controller: SearchController = new SearchController();

  build() {
    Column({ space : 10 }) {
      Text('Setting the caret position using controller').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
          value: 'Default Value',
          placeholder: 'Type to Search...',
          controller: this.controller,
          search: {
            searchButton: {
              searchButtonValue: 'SEARCH',
              options: { fontSize: '12fp', fontColor: '#ff0e1216' }
            }
          }
        },
      );
      Button('caretPosition to 1').onClick(() => {
        this.controller.caretPosition(1);
      }).width('100%')
      Button('stopEditing').onClick(() => {
        this.controller.stopEditing();
      }).width('100%')
      Button('Selection [0,3]').onClick(() => {
        this.controller.setTextSelection(0, 3);
      }).width('100%')
    }.padding({ left: 16, right: 16 })
  }
}
```

### Example 7: Setting the Enter Key Type

This example demonstrates how to use the enterKeyType attribute to dynamically change the effect of the Enter key on the soft keyboard.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State enterTypes: Array<EnterKeyType> = [EnterKeyType.Go, EnterKeyType.Search, EnterKeyType.Send, EnterKeyType.Done, EnterKeyType.Next, EnterKeyType.PREVIOUS, EnterKeyType.NEW_LINE];
  @State index: number = 0;

  build() {
    Column({ space : 10 }) {
      Text('Enter key type as search').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        placeholder: 'Enter key type as search',
        search: {
          enterKeyType: this.enterTypes[this.index]
        }
      })

      Button('Change EnterKeyType').onClick(() => {
        this.index = (this.index + 1) % this.enterTypes.length;
      }).width('100%')

    }.padding({ left: 16, right: 16 })
  }
}
```

### Example 8: Setting Text Feature Effects

This example demonstrates how to use the fontFeature attribute to display text with various typographic features.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space : 10 }) {
      Text('Setting text feature effects').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        value: 'This is ss01 on : 0123456789',
        search: {
          fontFeature: '"ss01" on'
        }
      });

      AtomicServiceSearch({
        value: 'This is ss01 off : 0123456789',
        search: {
          fontFeature: '"ss01" off'
        }
      });

      AtomicServiceSearch({
        value: 'fiabc1234567DEFGHIJKLMN',
        search: {
          fontFeature: '"frac" on'
        }
      });

      AtomicServiceSearch({
        value: 'fiabc1234567DEFGHIJKLMN',
        search: {
          fontFeature: '"frac" off'
        }
      });
    }.padding({ left: 16, right: 16 })
  }
}
```

### Example 9: Setting Text Auto-Adaptation

This example demonstrates how to use the minFontSize and maxFontSize attributes to implement the text auto-adaptation features.



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space : 10 }) {
      Text('Setting text auto-adaptation').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        value: 'This is the text without the adaptive font',
      }).width('80%').height(40).borderWidth(1).borderRadius(20)

      AtomicServiceSearch({
        value: 'This is the text without the adaptive font',
        search: {
          minFontSize: 4,
          maxFontSize: 40
        }
      }).width('80%').height(40).borderWidth(1).borderRadius(20)
    }.padding({ left: 16, right: 16 })
  }
}
```

### Example 10: Setting Custom Menu Extensions

This example demonstrates how to use the editMenuOptions API to create custom menu extensions for text settings. It includes customizing text content, icons, and callbacks for these extensions.



```TypeScript
import { AtomicServiceSearch, TextMenuController } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    TextMenuController.disableMenuItems([TextMenuItemId.AI_WRITER]);
  }

  onCreateMenu = (menuItems: Array<TextMenuItem>) => {
    let item1: TextMenuItem = {
      content: 'custom1',
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('custom1'),
    };
    let item2: TextMenuItem = {
      content: 'custom2',
      id: TextMenuItemId.of('custom2'),
      icon: $r('app.media.startIcon'),
    };
    menuItems.push(item1);
    menuItems.unshift(item2);
    return menuItems;
  }
  onMenuItemClick = (menuItem: TextMenuItem, textRange: TextRange) => {
    if (menuItem.id.equals(TextMenuItemId.of('custom2'))) {
      console.info('Intercept id: custom2 start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.COPY)) {
      console.info('Intercept COPY start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
      console.info('Do not intercept SELECT_ALL start:' + textRange.start + '; end:' + textRange.end);
      return false;
    }
    return false;
  }
  @State editMenuOptions: EditMenuOptions = {
    onCreateMenu: this.onCreateMenu, onMenuItemClick: this.onMenuItemClick
  };

  build() {
    Column({ space: 10 }) {
      Text('Setting custom menu extensions').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        value: 'Default input',
        search: {
          editMenuOptions: this.editMenuOptions
        }
      })
    }.padding({ left: 16, right: 16 })
  }
}
```

### Example 11: Setting the Horizontal Alignment, Caret Style, and Background Color of the Selected Text

This example shows how to set the horizontal alignment, caret style, and background color of the selected text using textAlign, caretStyle, and selectedBackgroundColor.



```TypeScript
import { AtomicServiceSearch, TextMenuController } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    TextMenuController.disableMenuItems([TextMenuItemId.AI_WRITER]);
  }

  build() {
    Column() {
      Text('Setting horizontal alignment/caret style/background color of selected text').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        value: 'Search textAlign sample',
        search: {
          textAlign: TextAlign.Center,
          caretStyle: { width: 3, color: Color.Green },
          selectedBackgroundColor: Color.Gray
        }
      })
    }.padding({ left: 16, right: 16 })
  }
}
```

### Example 12: Setting Input Filtering

This example shows how to set input filtering using inputFilter.

```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State filterValue: string = '';

  build() {
    Column() {
      Column({ space: 10 }) {
        Text('Setting input filtering').alignSelf(ItemAlign.Start).decoration({
          type: TextDecorationType.Underline,
          color: Color.Black,
          style: TextDecorationStyle.SOLID
        }).margin({ top: 20, bottom: 20 })
        AtomicServiceSearch({
          placeholder: 'please enter...',
          search: {
            inputFilter: {
              inputFilterValue : '[a-z]',
              error: (filterValue: string) => {this.filterValue = filterValue;}
            }
          }
        })
        Text('Filter:' + this.filterValue).alignSelf(ItemAlign.Start)

      }
    }.padding({ left: 16, right: 16 })
  }
}
```
