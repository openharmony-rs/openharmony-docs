# @ohos.atomicservice.AtomicServiceSearch(This section describes the interfaces used by AtomicServiceSearch)

## 导入模块

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceSearch](arkts-arkui-atomicservice-atomicservicesearch-atomicservicesearch-s.md) | AtomicServiceSearch为开发者提供满足定制化需求的功能，内容包括默认显示的搜索区、可自定义的选择区和功能区（最多两个）。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [InputFilterParams](arkts-arkui-atomicservice-atomicservicesearch-inputfilterparams-i.md) | 搜索框过滤设置项。 |
| [MenuAlignParams](arkts-arkui-atomicservice-atomicservicesearch-menualignparams-i.md) | 下拉按钮与下拉菜单间的对齐方式设置项。 |
| [OperationParams](arkts-arkui-atomicservice-atomicservicesearch-operationparams-i.md) | AtomicServiceSearch中“功能区”的初始化参数。 |
| [SearchButtonParams](arkts-arkui-atomicservice-atomicservicesearch-searchbuttonparams-i.md) | 搜索框末尾搜索按钮设置项。 |
| [SearchParams](arkts-arkui-atomicservice-atomicservicesearch-searchparams-i.md) | AtomicServiceSearch中“搜索区”的可选属性。 |
| [SelectParams](arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md) | AtomicServiceSearch中“选择区”的可选属性。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | 文本内容滚动时，触发该回调。 |
| [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | 进行粘贴操作时，触发该回调。 |
| [OnSelectCallback](arkts-arkui-onselectcallback-t.md) | 下拉菜单选中某一项的回调。 |
| [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | 文本选择的位置发生变化或编辑状态下光标位置发生变化时，触发该回调。 |

## 示例

### 示例1（AtomicServiceSearch添加选择区）

该示例通过select参数为AtomicServiceSearch组件添加左侧选择区。



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 6 }) {
      Text('AtomicServiceSearch添加选择区').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        select: {
          options: [
            { value: 'Select1', icon: $r('app.media.sweep') }, // 自定义资源
            { value: 'Select2', icon: $r('app.media.sweep') }, // 自定义资源
            { value: 'Select3', icon: $r('app.media.sweep') }, // 自定义资源
            { value: 'Select4', icon: $r('app.media.sweep') } // 自定义资源
          ],
          selected: -1,
          selectValue: 'Select1',
          onSelect: (index: number, selectValue: string) => { // 自定义事件
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

### 示例2（AtomicServiceSearch添加功能位）

该示例通过operation参数为AtomicServiceSearch组件添加右侧功能位。



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 6 }) {
      Text('AtomicServiceSearch添加功能位').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })
      
      AtomicServiceSearch({
        operation: {
          // 附属于Search组件的功能位
          auxiliaryItem: {
            value: $r('app.media.sweep'), // 自定义资源
            action: () => {
              this.alert('扫一扫'); // 自定义事件
            }
          },
          // 独立于Search组件的功能位
          independentItem: {
            value: $r('app.media.dingding'), // 自定义资源
            action: () => {
              this.alert('通知'); // 自定义事件
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

### 示例3（AtomicServiceSearch添加选择区及功能位）

该示例中为AtomicServiceSearch组件同时添加左侧选择区和右侧功能位。



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 6 }) {
      Text('AtomicServiceSearch+选择区+功能位').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        select: {
          options: [
            { value: 'Select1', icon: $r('app.media.sweep') }, // 自定义资源
            { value: 'Select2', icon: $r('app.media.sweep') }, // 自定义资源
            { value: 'Select3', icon: $r('app.media.sweep') }, // 自定义资源
            { value: 'Select4', icon: $r('app.media.sweep') } // 自定义资源
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
            value: $r('app.media.sweep'), // 自定义资源
            action: () => {
              this.alert('扫一扫'); // 自定义事件
            }
          },
          independentItem: {
            value: $r('app.media.dingding'), // 自定义资源
            action: () => {
              this.alert('通知'); // 自定义事件
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

### 示例4（search回调事件）

该示例通过onWillInsert、onDidInsert、onWillDelete、onDidDelete接口实现了插入和删除的功能。

通过onSubmit接口实现了搜索区内容提交的功能。

通过onChange接口实现了监听搜索区内容变化的功能。



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
      Text('AtomicServiceSearch绑定事件').alignSelf(ItemAlign.Start).decoration({
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

### 示例5（AtomicServiceSearch修改样式）

该示例通过search、select、value、placeholder参数实现了AtomicServiceSearch组件样式的自定义。



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
      Text('AtomicServiceSearch修改样式').alignSelf(ItemAlign.Start).decoration({
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
              this.alert('通知');
            }
          }
        }
      })
      Button('修改placeholder')
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
      Button('修改defaultValue')
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
      Button('修改Select样式')
        .width('100%')
        .type(ButtonType.Normal)
        .borderRadius(20)
        .onClick(() => {
          this.select = {
            options: [
              { value: '选项1', icon: $r('app.media.dingding') },
              { value: '选项2', icon: $r('app.media.dingding') },
            ],
            selected: -1,
            selectValue: '选项1',
            onSelect: (index: number) => {
              if (index === 0) {
                this.alert('选项1');
              } else if (index === 1) {
                this.alert('选项2');
              }
            }
          };
        });

      Button('修改Search样式')
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

### 示例6（通过controller实现光标位置的设置）

该示例通过controller参数实现了光标位置的设置、选择指定区域中的内容及关闭编辑状态的功能。



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  controller: SearchController = new SearchController();

  build() {
    Column({ space : 10 }) {
      Text('通过controller实现光标位置的设置').alignSelf(ItemAlign.Start).decoration({
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

### 示例7（设置输入法回车键类型）

该示例通过enterKeyType属性实现了动态切换输入法回车键的效果。



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State enterTypes: Array<EnterKeyType> = [EnterKeyType.Go, EnterKeyType.Search, EnterKeyType.Send, EnterKeyType.Done, EnterKeyType.Next, EnterKeyType.PREVIOUS, EnterKeyType.NEW_LINE];
  @State index: number = 0;

  build() {
    Column({ space : 10 }) {
      Text('输入法回车键类型为搜索').alignSelf(ItemAlign.Start).decoration({
        type: TextDecorationType.Underline,
        color: Color.Black,
        style: TextDecorationStyle.SOLID
      }).margin({ top: 20, bottom: 20 })

      AtomicServiceSearch({
        placeholder: '输入法回车键类型为搜索',
        search: {
          enterKeyType: this.enterTypes[this.index]
        }
      })

      Button('改变EnterKeyType').onClick(() => {
        this.index = (this.index + 1) % this.enterTypes.length;
      }).width('100%')

    }.padding({ left: 16, right: 16 })
  }
}
```

### 示例8（设置文字特性效果）

该示例通过fontFeature属性实现了文本在不同文字特性下的展示效果。



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space : 10 }) {
      Text('设置文字特性效果').alignSelf(ItemAlign.Start).decoration({
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

### 示例9（设置文本自适应）

该示例通过minFontSize、maxFontSize属性展示了文本自适应字号的效果。



```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space : 10 }) {
      Text('设置文本自适应').alignSelf(ItemAlign.Start).decoration({
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

### 示例10（文本扩展自定义菜单）

该示例通过editMenuOptions接口实现了文本设置自定义菜单扩展项的文本内容、图标以及回调的功能。



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
      console.info('拦截 id: custom2 start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.COPY)) {
      console.info('拦截 COPY start:' + textRange.start + '; end:' + textRange.end);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
      console.info('不拦截 SELECT_ALL start:' + textRange.start + '; end:' + textRange.end);
      return false;
    }
    return false;
  }
  @State editMenuOptions: EditMenuOptions = {
    onCreateMenu: this.onCreateMenu, onMenuItemClick: this.onMenuItemClick
  };

  build() {
    Column({ space: 10 }) {
      Text('文本扩展自定义菜单').alignSelf(ItemAlign.Start).decoration({
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

### 示例11（设置文本水平对齐/光标样式/选中背景色）

该示例通过textAlign、caretStyle、selectedBackgroundColor属性展示如何设置文本的水平对齐、光标样式和选中背景色。



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
      Text('设置文本水平对齐/光标样式/选中背景色').alignSelf(ItemAlign.Start).decoration({
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

### 示例12（对输入的文本进行过滤）

该示例通过inputFilter属性展示如何对输入的文本进行内容的过滤，以限制输入内容。

```TypeScript
import { AtomicServiceSearch } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State filterValue: string = '';

  build() {
    Column() {
      Column({ space: 10 }) {
        Text('对输入的文本进行过滤').alignSelf(ItemAlign.Start).decoration({
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
