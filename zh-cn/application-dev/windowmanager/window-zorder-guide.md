# 窗口层级

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->

## 场景介绍

**窗口层级**是指多个窗口在屏幕上的堆叠顺序，决定窗口的前后显示关系，通常称为**Z序（ZOrder）**。

ZOrder值越大，窗口越靠前显示，能够覆盖ZOrder值较小的窗口；反之，ZOrder值较小的窗口则可能被其他窗口遮挡。

对于三方应用，无法直接修改窗口的ZOrder，但可以通过控制**zLevel**属性来间接影响子窗口的显示层级。

系统通过管理ZOrder和zLevel实现对用户界面可见性与交互优先级的控制。

本节将从基本概念、层级规则、父子窗口关系、TopMost窗口机制以及相关接口示例五个方面，系统化阐述窗口层级管理机制。

## 基本概念与层级规则

### ZOrder与zLevel

**ZOrder**表示系统内部维护的窗口堆叠顺序。数值越大，窗口越靠前。三方应用不可直接修改ZOrder。

**zLevel**表示三方应用可控制的应用内子窗口之间的相对层级，仅针对非模态子窗口有效。zLevel取值范围为[-10000, 10000]，默认值为0。zLevel越高，对应的ZOrder越大，窗口越靠前。

### 窗口zLevel层级规则

- **不同zLevel的子窗口**

  - zLevel高的窗口始终覆盖zLevel低的窗口，即使点击zLevel较低的窗口，也不会将其抬升至zLevel更高的窗口之上。

- **相同zLevel的子窗口**

  - 默认后创建的窗口层级更高。

  - 用户点击某个子窗口时，该窗口的ZOrder会被提升至同zLevel中的最高位置，实现“点击置顶”。

  - 若调用[setRaiseByClickEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setraisebyclickenabled14)接口传入false，则禁用点击抬升功能，点击时层级保持不变。

### 窗口类型层级规则

- **所有窗口类型的层级**

  系统中所有类型的窗口自上而下的层级关系如下表所示（层级由高到低）：

  | 窗口类别 | 说明 |
  | -------- | -------- |
  | 画中画窗口 | 以小窗形式显示的视频窗口，如视频通话或视频播放过程中上划退出应用，画面仍以小窗形式继续显示。 |
  | 全局悬浮窗 | 使用[WindowType.TYPE_FLOAT](../reference/apis-arkui/arkts-apis-window-e.md#windowtype7)创建的窗口，需申请ohos.permission.SYSTEM_FLOAT_WINDOW权限，位于所有应用窗口之上；另有相机类型悬浮窗、全局搜索窗口等系统接口窗口，仅系统应用可创建。 |
  | 置顶模态主窗口 | 模态主窗口叠加置顶效果，遮蔽并拦截其后方窗口的交互，同时位于其他应用主窗口之上，但仍低于系统窗口。 |
  | 置顶主窗口 | 调用[setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)置顶的主窗口，位于其他应用的普通主窗口之上，但仍低于系统窗口。 |
  | 模态主窗口 | 设置模态效果的主窗口，遮蔽并拦截其后方窗口的交互。 |
  | 应用主窗口 | 默认创建的应用主窗口，多个主窗口之间按激活顺序叠放。 |

  各层级的具体数值在不同设备形态（PC/手机/Pad）及系统版本上存在差异，上表仅描述相对层级关系。

- **相同类型窗口的层级调整**

  同类型窗口（多个主窗口、多个普通子窗）之间可通过点击或快捷键（如Alt+Tab）调整层级。

- **应用内子窗口类型的默认层级**

  系统为不同类型的子窗口分配了默认层级。优先级由高到低如下所示：

  | 窗口类型     | 创建方式 |
  | -------- | -------- |
  | 模应用子窗   | 调用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12)接口，并设置子窗口参数[SubWindowOptions](../reference/apis-arkui/arkts-apis-window-i.md#subwindowoptions11)中的isModal为true，modalityType为APPLICATION_MODALITY。 |
  | Toast子窗  | 调用[showToast()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showtoast)接口，并设置showMode为TOP_MOST。 |
  | 文本菜单子窗   | 调用[showActionMenu()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showactionmenu)接口，并设置showInSubWindow为true。 |
  | Dialog子窗 | 调用[openCustomDialog()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12)传入dialogContent、options参数，并设置showInSubWindow为true。<br>调用[openCustomDialog()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)传入options参数，并设置showInSubWindow为true。<br>调用[openCustomDialogWithController()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18)，并设置showInSubWindow为true。 |
  | 模态子窗     | 调用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12)接口，并设置子窗口参数[SubWindowOptions](../reference/apis-arkui/arkts-apis-window-i.md#subwindowoptions11)中的isModal为true，modalityType为WINDOW_MODALITY。 |
  | 普通子窗     | 调用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12)接口创建的默认子窗。 |

  不同类型窗口之间不能通过点击或API调整跨越层级范围。

### 父子窗口层级规则

- 当父窗口被抬升时，其所有子窗口也会随之抬升；当子窗口被抬升时，其父窗口也会随之抬升。
- 子窗口的层级始终高于其父窗口。
- 窗口抬升可通过调用[raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14)接口或点击窗口实现。

### TopMost置顶窗口层级规则

- 在[自由窗口](window-terminology.md#freeform-window自由窗口)状态下，应用主窗口可通过调用[setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)接口传入true将自身置于其他应用窗口之上，以实现“不被遮挡”的常驻显示效果，需合理使用，避免影响用户体验。

- 使用该接口需要申请权限ohos.permission.WINDOW_TOPMOST。

## 窗口层级控制机制汇总表


| 特性/操作 | 控制方式 | 生效范围 | 适用场景 |
| -------- | -------- | -------- | -------- |
| ZOrder | 系统管理 | 可跨应用生效 | 内部渲染顺序管理 |
| zLevel | setSubWindowZLevel()/创建窗口时设置 | 仅同应用内生效 | 子窗口层级管理 |
| 窗口置顶 | setWindowTopmost() | 可跨应用生效 | 视频、导航等常驻窗口 |
| 点击抬升 | setRaiseByClickEnabled() | 同应用内同类型子窗口之间 | 防误触、固定布局 |

## 层级相关开发场景

| 功能 | 典型场景 | 对应接口 |
| -------- | -------- | -------- |
| 设置主窗口置顶 | 用于实现将窗口置于其他应用窗口之上不被遮挡。如视频通话、导航等场景。 | [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) |
| 提升子窗口到顶层 | 将子窗口提升至当前应用内同类型子窗口的最顶层，只在当前应用同一个父窗口下相同zLevel值的子窗范围内生效。<br>例如，视频会议中的悬浮工具栏，主窗口是视频画面，子窗口包括聊天框、共享控制栏等。点击聊天框时，可调用raiseToAppTop()将其提升到顶层，避免被其他子窗口遮挡。 | [raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14) |
| 禁止/使能子窗点击抬升功能 | 可用于固定布局的工具面板，防止用户误操作导致层级混乱。 | [setRaiseByClickEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setraisebyclickenabled14) |
| 获取当前应用内层级最高的窗口 | 可判断当前最前显示的窗口（可能是主窗口或子窗口），用于日志记录或状态同步等场景。 | [getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1) |

> **说明：**
>
> - 合理设置zLevel，避免层级冲突。
>
> - TopMost功能谨慎使用，避免干扰系统多窗口体验。
>
> - 对于需要高优先级显示的关键界面，可通过[raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14)确保可见性，使用此接口前，需确保该窗口已调用showWindow()类接口（[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9-1)/[showWindow(options: ShowWindowOptions)](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow20)）并执行完毕。
>
> - [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)仅在[自由窗口](window-terminology.md#freeform-window自由窗口)状态下生效。开发者可通过[isInFreeWindowMode()](../reference/apis-arkui/arkts-apis-window-Window.md#isinfreewindowmode22)查询当前窗口是否处于自由窗口，并结合[on('freeWindowModeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onfreewindowmodechange22)事件监听器实时监听窗口模式的变化，从而准确判断何时可以安全调用[setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)。

## 相关实践

### 使用模态子窗实现关键操作确认

删除、支付、退出登录等关键操作通常需要用户二次确认，且确认完成前应阻断页面其他操作。此时可创建模态子窗承载确认弹窗：模态子窗的层级高于所属主窗口及普通子窗，弹出后其遮蔽范围内的窗口不可交互，直至子窗关闭。

开发步骤：

1. 通过主窗口调用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12)创建子窗，并在[SubWindowOptions](../reference/apis-arkui/arkts-apis-window-i.md#subwindowoptions11)中设置isModal为true：
   - modalityType为WINDOW_MODALITY时，仅遮蔽父窗口，适合单页面内的操作确认；
   - modalityType为APPLICATION_MODALITY时，遮蔽当前应用的所有窗口，适合全局性阻断（仅自由多窗模式设备支持）。
2. 调用loadContent()加载确认弹窗页面，调用showWindow()显示子窗。
3. 用户确认或取消后，调用destroy()销毁子窗，被遮蔽窗口恢复交互。

```ts
// 示例：弹出删除确认模态子窗
import { window } from '@kit.ArkUI';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function showDeleteConfirm(context: common.UIAbilityContext): Promise<void> {
  let mainWindow = context.windowStage.getMainWindowSync();
  let options: window.SubWindowOptions = {
    title: '删除确认',
    decorEnabled: false,
    isModal: true,
    modalityType: window.ModalityType.WINDOW_MODALITY
  };
  try {
    let subWindow = await mainWindow.createSubWindowWithOptions('deleteConfirm', options);
    subWindow.loadContent('pages/DeleteConfirm', (err: BusinessError) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      subWindow.showWindow();
    });
  } catch (exception) {
    console.error(`Failed to create the subwindow. Cause code: ${exception.code}, message: ${exception.message}`);
  }
}
```

> **说明：**
>
> - 模态子窗的默认层级高于普通子窗和文本菜单子窗，无需额外调用[setSubWindowZLevel()](../reference/apis-arkui/arkts-apis-window-Window.md#setsubwindowzlevel18)调整层级。
> - 独立子窗设置模态属性不生效。
> - 如需中途取消模态，可调用[setSubWindowModal()](../reference/apis-arkui/arkts-apis-window-Window.md#setsubwindowmodal12)传入false。

### 实现应用主窗口置顶

视频通话、实时导航等场景中，应用主窗口需要常驻显示、不被其他应用窗口遮挡，可通过[setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)实现置顶。

开发步骤：

1. 在module.json5中声明权限ohos.permission.WINDOW_TOPMOST。
2. 调用[isInFreeWindowMode()](../reference/apis-arkui/arkts-apis-window-Window.md#isinfreewindowmode22)确认当前处于[自由窗口](window-terminology.md#freeform-window自由窗口)状态（置顶仅在该状态下生效）；必要时注册[on('freeWindowModeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onfreewindowmodechange22)监听窗口模式变化。
3. 需要置顶时调用setWindowTopmost(true)，不再需要时调用setWindowTopmost(false)取消置顶。

```ts
// 示例：设置主窗口置顶
import { window } from '@kit.ArkUI';
import { common } from '@kit.AbilityKit';

async function setTopmost(context: common.UIAbilityContext, isTopmost: boolean): Promise<void> {
  let mainWindow = context.windowStage.getMainWindowSync();
  if (!mainWindow.isInFreeWindowMode()) {
    console.info('The window is not in free window mode, topmost is not supported.');
    return;
  }
  try {
    await mainWindow.setWindowTopmost(isTopmost);
    console.info('Succeeded in setting window topmost.');
  } catch (exception) {
    console.error(`Failed to set window topmost. Cause code: ${exception.code}, message: ${exception.message}`);
  }
}
```

```json
// module.json5
{
  "module": {
    "requestPermissions": [
      {
        "name": "ohos.permission.WINDOW_TOPMOST"
      }
    ]
  }
}
```

> **说明：**
>
> - 置顶主窗口仅高于其他应用的普通主窗口，仍低于系统窗口（如输入法窗口、全局悬浮窗、系统Toast窗口）。
> - 建议在页面中提供明显的置顶/取消置顶入口，避免长期置顶干扰用户的多任务操作。

