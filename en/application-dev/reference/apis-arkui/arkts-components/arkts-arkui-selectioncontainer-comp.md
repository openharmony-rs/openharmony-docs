# SelectionContainer

Defines SelectionContainer component.

## SelectionContainer

```TypeScript
SelectionContainer(value?: SelectionContainerOptions)
```

Defines the constructor of SelectionContainer.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectionContainerOptions](arkts-arkui-selectioncontainer-comp-selectioncontaineroptions-i.md) | No | Initialization options of the component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [SelectionContainerEditMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainereditmenuoptions-i.md) | Defines custom edit menu options for SelectionContainer. |
| [SelectionContainerMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainermenuoptions-i.md) | Defines selection menu options for SelectionContainer. |
| [SelectionContainerOptions](arkts-arkui-selectioncontainer-comp-selectioncontaineroptions-i.md) | Describes the initialization options of the SelectionContainer component. |

### Types

| Name | Description |
| --- | --- |
| [OnMenuItemClickWithTextCallback](arkts-arkui-selectioncontainer-comp-onmenuitemclickwithtextcallback-t.md) | Invoke upon clicking an item, capable of intercepting the default system menu execution behavior. |

### Enums

| Name | Description |
| --- | --- |
| [SelectionContainerTextJoinStyle](arkts-arkui-selectioncontainer-comp-selectioncontainertextjoinstyle-e.md) | Defines text join style for SelectionContainer. |

## Examples

### Example 1: Selecting Text Across Nodes and Copying the Text

This example demonstrates how to select text across multiple Text components, concatenate the selected text, and handle copy callbacks by using [SelectionContainer](#interfaces), [copyOption](#copyoption), [textJoinStyle](arkts-arkui-selectioncontainer-comp-attribute.md#textjoinstyle), [onTextSelectionChange](#ontextselectionchange), [onWillCopy](#onwillcopy), and [onCopy](#oncopy).

Since API version 26.0.0, the SelectionContainer component and APIs such as copyOption are added.



```TypeScript
import {
  SelectionContainer,
  SelectionContainerAttribute,
  SelectionContainerTextJoinStyle
} from '@kit.ArkUI';

@Entry
@Component
struct SelectionContainerExample1 {
  @State selectedParts: string[] = [];
  @State copiedText: string = '';

  build() {
    Column({ space: 12 }) {
      Text('Long press the area below and select text across nodes.')
        .fontSize(16)

      SelectionContainer() {
        Column({ space: 8 }) {
          Text('First paragraph: SelectionContainer supports selection across multiple Text components.')
            .fontSize(18)
            .copyOption(CopyOptions.InApp)
          Text('Second paragraph: The selection result is concatenated in the visual order of the Text components.')
            .fontSize(18)
            .copyOption(CopyOptions.InApp)
          Text('Third paragraph: You can listen for selection changes, pre-copy validation, and copy completion events.')
            .fontSize(18)
            .copyOption(CopyOptions.InApp)
        }
      }
      .copyOption(CopyOptions.InApp)
      .textJoinStyle(SelectionContainerTextJoinStyle.NEWLINE)
      .caretColor(Color.Red)
      .selectedBackgroundColor('#33007DFF')
      .onTextSelectionChange((value: Array<string>) => {
        this.selectedParts = value;
        console.info(`Selected text changed: ${JSON.stringify(value)}`);
      })
      .onWillCopy((value: string) => {
        this.copiedText = `Preparing to copy: ${value}`;
        console.info(`Preparing to copy text: ${value}`);
        return true;
      })
      .onCopy((value: string) => {
        this.copiedText = `Copy succeeded: ${value}`;
        console.info(`Text copied successfully: ${value}`);
      })
      .border({ width: 1, color: '#DCDCDC' })
      .padding(12)
      .width('100%')

      Text(`Selected content: ${this.selectedParts.join(' | ')}`)
        .fontSize(14)
        .fontColor('#666666')

      Text(this.copiedText)
        .fontSize(14)
        .fontColor('#666666')
    }
    .width('100%')
    .padding(16)
  }
}
```

### Example 2: Binding a Custom Selection Menu

This example demonstrates how to bind a custom menu when selecting text across nodes through [bindSelectionMenu](#bindselectionmenu).

Since API version 26.0.0, the bindSelectionMenu attribute is added.



```TypeScript
import {
  SelectionContainer,
  SelectionContainerAttribute,
  SelectionContainerMenuOptions,
  SelectionContainerTextJoinStyle
} from '@kit.ArkUI';

@Entry
@Component
struct SelectionContainerExample2 {
  @State selectedText: string = '';
  @State menuLog: string = '';

  build() {
    Column({ space: 12 }) {
      Text('Long press the area below to select text and experience the custom menu.')
        .fontSize(16)

      SelectionContainer() {
        Column({ space: 8 }) {
          Text('First paragraph: SelectionContainer supports custom selection menus.')
            .fontSize(18)
          Text('Second paragraph: Bind a complete custom menu through bindSelectionMenu.')
            .fontSize(18)
        }
      }
      .copyOption(CopyOptions.InApp)
      .textJoinStyle(SelectionContainerTextJoinStyle.DIRECT)
      .bindSelectionMenu(
        TextSpanType.TEXT,
        this.menuBuilder,
        TextResponseType.LONG_PRESS,
        {
          onAppear: (text: string) => {
            this.menuLog = `Menu appears: ${text}`;
            console.info(`Menu appears: ${text}`);
          },
          onDisappear: () => {
            this.menuLog = 'Menu disappears';
            console.info('Menu disappears');
          },
          onMenuShow: (text: string) => {
            this.menuLog = `Menu shown: ${text}`;
            console.info(`Menu shown: ${text}`);
          },
          onMenuHide: (text: string) => {
            this.menuLog = `Menu hidden: ${text}`;
            console.info(`Menu hidden: ${text}`);
          }
        } as SelectionContainerMenuOptions
      )
      .onTextSelectionChange((value: Array<string>) => {
        this.selectedText = `Selected: ${value.join(' | ')}`;
        console.info(`Selection changed: ${JSON.stringify(value)}`);
      })
      .border({ width: 1, color: '#DCDCDC' })
      .padding(12)
      .width('100%')
    }
    .width('100%')
    .padding(16)
  }

  @Builder
  menuBuilder() {
    Column() {
      Menu() {
        MenuItemGroup() {
          MenuItem({ content: 'Custom copy', labelInfo: '' })
            .onClick(() => {
              console.info('Custom copy clicked');
            })
          MenuItem({ content: 'Custom share', labelInfo: '' })
            .onClick(() => {
              console.info('Custom share clicked');
            })
          MenuItem({ content: 'Custom translation', labelInfo: '' })
            .onClick(() => {
              console.info('Custom translation clicked');
            })
        }
      }
      .radius($r('sys.float.ohos_id_corner_radius_card'))
      .clip(true)
      .backgroundColor('#F0F0F0')
    }
  }
}
```

### Example 3: Extending Menu Options

This example uses [editMenuOptions](#editmenuoptions) to remove the translation and search menu items from the system menu and add five custom menu items. It also demonstrates, in the [onMenuItemClick](arkts-arkui-selectioncontainer-comp-onmenuitemclickwithtextcallback-t.md) callback, the difference between intercepting the system copy operation (returning true) and not intercepting the select-all operation (returning false).

The editMenuOptions attribute is added since API version 26.0.0.



```TypeScript
import {
  OnMenuItemClickWithTextCallback,
  SelectionContainer,
  SelectionContainerAttribute,
  SelectionContainerEditMenuOptions,
  SelectionContainerTextJoinStyle
} from '@kit.ArkUI';

@Entry
@Component
struct SelectionContainerExample3 {
  @State selectedText: string = '';
  @State menuClickLog: string = '';
  onCreateMenu = (menuItems: Array<TextMenuItem>) => {
    let targetIndex = menuItems.findIndex(item => item.id.equals(TextMenuItemId.TRANSLATE));
    if (targetIndex !== -1) {
      menuItems.splice(targetIndex, 1);
    }
    targetIndex = menuItems.findIndex(item => item.id.equals(TextMenuItemId.SEARCH));
    if (targetIndex !== -1) {
      menuItems.splice(targetIndex, 1);
    }
    let customItem1: TextMenuItem = {
      content: 'Annotate',
      id: TextMenuItemId.of('highlight'),
    };
    let customItem2: TextMenuItem = {
      content: 'Favorite',
      id: TextMenuItemId.of('bookmark'),
    };
    let customItem3: TextMenuItem = {
      content: 'Comment',
      id: TextMenuItemId.of('comment'),
    };
    let customItem4: TextMenuItem = {
      content: 'Export',
      id: TextMenuItemId.of('export'),
    };
    // Replace $r('app.media.startIcon') with the image resource file required by the developer.
    let customItem5: TextMenuItem = {
      content: 'Push',
      icon: $r('app.media.startIcon'),
      id: TextMenuItemId.of('push'),
    };
    menuItems.push(customItem1);
    menuItems.push(customItem2);
    menuItems.push(customItem3);
    menuItems.push(customItem4);
    menuItems.push(customItem5);
    return menuItems;
  }
  onMenuItemClick: OnMenuItemClickWithTextCallback = (menuItem: TextMenuItem, text: string) => {
    this.menuClickLog = `Menu item clicked: ${menuItem.content}, text: ${text}`;
    console.info(`Menu item clicked: ${menuItem.content}, text: ${text}`);
    if (menuItem.id.equals(TextMenuItemId.COPY)) {
      this.selectedText = `Copied: ${text}`;
      console.info(`System copy operation intercepted, return true: ${text}`);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.SELECT_ALL)) {
      this.selectedText = `Select all operation: ${text}`;
      console.info(`Select all operation not intercepted, return false: execute the system default behavior`);
      return false;
    }
    if (menuItem.id.equals(TextMenuItemId.of('highlight'))) {
      this.selectedText = `Annotated: ${text}`;
      console.info(`Custom menu item clicked: Annotate, text: ${text}`);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of('bookmark'))) {
      this.selectedText = `Favorited: ${text}`;
      console.info(`Custom menu item clicked: Favorite, text: ${text}`);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of('comment'))) {
      this.selectedText = `Commented: ${text}`;
      console.info(`Custom menu item clicked: Annotate, text: ${text}`);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of('export'))) {
      this.selectedText = `Exported: ${text}`;
      console.info(`Custom menu item clicked: Export, text: ${text}`);
      return true;
    }
    if (menuItem.id.equals(TextMenuItemId.of('push'))) {
      this.selectedText = `Pushed: ${text}`;
      console.info(`Custom menu item clicked: Push, text: ${text}`);
      return true;
    }
    return false;
  }
  @State editMenuOptions: SelectionContainerEditMenuOptions = {
    onCreateMenu: this.onCreateMenu,
    onMenuItemClick: this.onMenuItemClick
  };

  build() {
    Column({ space: 12 }) {
      Text('Long press the area below to select text and experience the extended menu.')
        .fontSize(16)

      SelectionContainer() {
        Column({ space: 8 }) {
          Text('First paragraph: SelectionContainer supports extended menu options.')
            .fontSize(18)
          Text('Second paragraph: You can remove system menu items and add custom menu items.')
            .fontSize(18)
        }
      }
      .copyOption(CopyOptions.InApp)
      .textJoinStyle(SelectionContainerTextJoinStyle.DIRECT)
      .editMenuOptions(this.editMenuOptions)
      .onTextSelectionChange((value: Array<string>) => {
        this.selectedText = `Selected: ${value.join(' | ')}`;
        console.info(`Selection changed: ${JSON.stringify(value)}`);
      })
      .border({ width: 1, color: '#DCDCDC' })
      .padding(12)
      .width('100%')

      Text(this.selectedText)
        .fontSize(14)
        .fontColor('#666666')

      Text(this.menuClickLog)
        .fontSize(14)
        .fontColor('#999999')
    }
    .width('100%')
    .padding(16)
  }
}
```

### Example 4: Closing the Selection Menu and Clearing Text Selection Through the Controllers

This example demonstrates how to close the selection menu and clear the text selection by passing [SelectionContainerController](arkts-arkui-selectioncontainer-comp-selectioncontainercontroller-c.md) through [SelectionContainer](#interfaces) and calling [closeSelectionMenu](#closeselectionmenu) and [clearTextSelection](arkts-arkui-selectioncontainer-comp-selectioncontainercontroller-c.md#cleartextselection).

Since API version 26.0.0, the [SelectionContainerController](arkts-arkui-selectioncontainer-comp-selectioncontainercontroller-c.md) and [SelectionContainerOptions](arkts-arkui-selectioncontainer-comp-selectioncontaineroptions-i.md) APIs are added.

```TypeScript
import {
  SelectionContainer,
  SelectionContainerController,
  SelectionContainerAttribute
} from '@kit.ArkUI';

@Entry
@Component
struct SelectionContainerControllerExample {
  private controller: SelectionContainerController = new SelectionContainerController();

  build() {
    Column({ space: 12 }) {
      Text('Long press the area below to select text across nodes, and then tap the button to close the selection menu or clear the selected text.')
        .fontSize(16)

      SelectionContainer({ controller: this.controller }) {
        Column({ space: 8 }) {
          Text('First paragraph: SelectionContainer supports selecting text across multiple Text components.')
            .fontSize(18)
            .copyOption(CopyOptions.InApp)
          Text('Second paragraph: After selection, you can close the selection menu or clear the selected text through the controller.')
            .fontSize(18)
            .copyOption(CopyOptions.InApp)
        }
      }
      .copyOption(CopyOptions.InApp)
      .border({ width: 1, color: '#DCDCDC' })
      .padding(12)
      .width('100%')

      Row({ space: 12 }) {
        Button('Close selection menu')
          .onClick(() => {
            this.controller.closeSelectionMenu();
          })
        Button('Clear text selection')
          .onClick(() => {
            this.controller.clearTextSelection();
          })
      }
    }
    .width('100%')
    .padding(16)
  }
}
```
