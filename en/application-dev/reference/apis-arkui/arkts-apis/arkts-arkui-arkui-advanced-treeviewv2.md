# @ohos.arkui.advanced.TreeViewV2

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [TreeControllerV2](arkts-arkui-arkui-advanced-treeviewv2-treecontrollerv2-c.md) | Declare TreeControllerV2 |
| [TreeListenerManagerV2](arkts-arkui-arkui-advanced-treeviewv2-treelistenermanagerv2-c.md) | Declare class TreeListenerManagerV2 |
| [TreeListenerV2](arkts-arkui-arkui-advanced-treeviewv2-treelistenerv2-c.md) | Declare class TreeListenerV2 |

### Structs

| Name | Description |
| --- | --- |
| [TreeViewV2](arkts-arkui-arkui-advanced-treeviewv2-treeviewv2-s.md) | Declare TreeViewV2 Component |

### Interfaces

| Name | Description |
| --- | --- |
| [CallbackParamV2](arkts-arkui-arkui-advanced-treeviewv2-callbackparamv2-i.md) | Declare CallbackParamV2 |
| [NodeParamV2](arkts-arkui-arkui-advanced-treeviewv2-nodeparamv2-i.md) | Declare NodeParamV2 |

### Types

| Name | Description |
| --- | --- |
| [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Callback method of event registration and processing. |
| [OnContainerCallback](arkts-arkui-oncontainercallback-t.md) | Set subcomponent binded on tree item. |

## Examples

### Example 1: Configuring a Tree View

Since API version 26.0.0, the following example supports adding, deleting, and renaming nodes in a tree view through the controller API of the tree view component.

```TypeScript
import {
  TreeControllerV2,
  TreeListenerV2,
  TreeListenerManagerV2,
  NodeParamV2,
  TreeViewV2,
  CallbackParamV2
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct TreeViewV2Demo {
  // Create a tree view controller.
  private treeControllerV2: TreeControllerV2 = new TreeControllerV2();
  // Create a tree view listener.
  private treeListenerV2: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  // Record the ID of the currently clicked node.
  @Local clickNodeId: number = 0;

  // Cancel all listeners when the component is destroyed.
  aboutToDisappear(): void {
    this.treeListenerV2.offNodeClick();
    this.treeListenerV2.offNodeAdd();
    this.treeListenerV2.offNodeDelete();
    this.treeListenerV2.offNodeModify();
    this.treeListenerV2.offNodeMove();
  }

  // Register listeners and build the tree structure when the component is initialized.
  aboutToAppear(): void {
    // Register the node click listener.
    this.treeListenerV2.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node add listener.
    this.treeListenerV2.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node delete listener.
    this.treeListenerV2.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node move listener.
    this.treeListenerV2.onceNodeMove((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
      console.info(`Node moved to index: ${callbackParam.childIndex}`);
    })

    let normalResource: Resource = $r('sys.media.ohos_ic_normal_white_grid_folder');
    let selectedResource: Resource = $r('sys.media.ohos_ic_public_select_all');
    let editResource: Resource = $r('sys.media.ohos_ic_public_edit');

    let nodeParam: NodeParamV2 = {
      parentNodeId: -1,
      currentNodeId: 1,
      isFolder: true,
      icon: normalResource,
      selectedIcon: selectedResource,
      editIcon: editResource,
      primaryTitle: 'Directory 1',
      secondaryTitle: '6'
    };

    // Build the tree structure.
    this.treeControllerV2
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: 'Item 1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: 'Directory 2'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 23,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: 'Project 4'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 31,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 5',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 32,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 6',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 32,
        currentNodeId: 35,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 6-1',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 33,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: 'Item 8'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: 'Item 9'
      })
      .buildDone();

    this.treeControllerV2.refreshNode(-1, 'Parent node', 'Child node');
  }

  build(): void {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        // Tree view component.
        TreeViewV2({ treeControllerV2: this.treeControllerV2 })
        Row() {
          Divider().vertical(true).strokeWidth(2).color(0x000000).lineCap(LineCapStyle.Round)
          Column({ space: 30 }) {
            Text('ClickNodeId=' + this.clickNodeId).fontSize('16fp')
            Button('Add', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.addNode();
              })
            Button('Modify', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.modifyNode();
              })
            Button('Remove', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(120)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.removeNode();
              })
          }.height('100%').width('70%').alignItems(HorizontalAlign.Start).margin(10)
        }
      }
      .focusable(true)
      .showControlButton(false)
      .showSideBar(true)
    }
  }
}
```

### Example 2: Setting a Symbol Icon

Since API version 26.0.0, the following example demonstrates how to customize symbol icons in the tree view by setting the attribute APIs such as symbolIconStyle, symbolEditIconStyle, and symbolSelectedIconStyle of [NodeParamV2](arkts-arkui-arkui-advanced-treeviewv2-nodeparamv2-i.md).

```TypeScript
import {
  TreeControllerV2,
  TreeListenerV2,
  TreeListenerManagerV2,
  NodeParamV2,
  TreeViewV2,
  CallbackParamV2,
  SymbolGlyphModifier
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct TreeViewV2Demo {
  // Create a tree view controller.
  private treeControllerV2: TreeControllerV2 = new TreeControllerV2();
  // Create a tree view listener.
  private treeListenerV2: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  // Record the ID of the currently clicked node.
  @Local clickNodeId: number = 0;

  // Cancel all listeners when the component is destroyed.
  aboutToDisappear(): void {
    this.treeListenerV2.offNodeClick();
    this.treeListenerV2.offNodeAdd();
    this.treeListenerV2.offNodeDelete();
    this.treeListenerV2.offNodeModify();
    this.treeListenerV2.offNodeMove();
  }

  // Register the listener and build the tree structure during component initialization.
  aboutToAppear(): void {
    // Register the node click listener.
    this.treeListenerV2.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    });
    // Register the node add listener.
    this.treeListenerV2.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node delete listener.
    this.treeListenerV2.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node move listener (destroyed automatically after listening once).
    this.treeListenerV2.onceNodeMove((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
      console.info(`Node moved to parent: ${callbackParam.parentNodeId}, index: ${callbackParam.childIndex}`);
    })

    let normalResource: Resource = $r('sys.symbol.house');
    let selectedResource: Resource = $r('sys.symbol.car');
    let editResource: Resource = $r('sys.symbol.calendar');

    let normalSymbolResource: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.bell'))
      .fontColor([Color.Red]);
    let selectedSymbolResource: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.heart'))
      .fontColor([Color.Blue]);
    let editSymbolResource: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.cake'))
      .fontColor([Color.Pink]);

    let nodeParam: NodeParamV2 = {
      parentNodeId: -1,
      currentNodeId: 1,
      isFolder: true,
      icon: normalResource,
      selectedIcon: selectedResource,
      editIcon: editResource,
      primaryTitle: 'Directory 1',
      secondaryTitle: '6'
    };

    // Build the tree structure.
    this.treeControllerV2
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: 'Item 1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: 'Directory 2'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 23,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: 'Project 4'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 31,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 5',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 32,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 6',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 32,
        currentNodeId: 35,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 6-1',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 33,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: 'Project 8'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: 'Project 9'
      })
      .buildDone();

    this.treeControllerV2.refreshNode(-1, 'Parent node', 'Child node');
  }

  build(): void {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        // Tree view component
        TreeViewV2({ treeControllerV2: this.treeControllerV2 })
        Row() {
          Divider().vertical(true).strokeWidth(2).color(0x000000).lineCap(LineCapStyle.Round)
          Column({ space: 30 }) {
            Text('ClickNodeId=' + this.clickNodeId).fontSize('16fp')
            Button('Add', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.addNode();
              })
            Button('Modify', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.modifyNode();
              })
            Button('Remove', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(120)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.removeNode();
              })
          }.height('100%').width('80%').alignItems(HorizontalAlign.Start).margin(10)
        }
      }
      .focusable(true)
      .showControlButton(false)
      .showSideBar(true)
    }
  }
}
```
