# TreeViewV2
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangrunsen-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->


树视图V2组件。树视图作为一种分层显示的列表，适合显示嵌套结构。拥有父节点和子节点，可展开或折叠，支持节点的增删改、拖拽移动、自定义图标、事件监听和右键菜单等功能。

用于效率型应用，如备忘录、电子邮件、图库中的侧边导航栏，适用于需要展示和管理层级结构数据、支持节点交互操作的场景。

该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制树视图的数据和状态，实现更高效的用户界面刷新。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 如果TreeViewV2设置[通用属性](ts-component-general-attributes.md)和[通用事件](ts-component-general-events.md)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到TreeViewV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议TreeViewV2设置通用属性和通用事件。

**起始版本：** 26.0.0

## 导入模块

```ts
import { TreeViewV2 } from '@kit.ArkUI';
```

## 子组件

无。

## TreeViewV2

TreeViewV2({ treeControllerV2: TreeControllerV2 })

树视图作为一种分层显示的列表，用于树形结构的组件显示，支持节点的增删改、拖拽移动、自定义图标、事件监听和右键菜单等功能，适用于需要展示和管理层级结构数据的场景。

**起始版本：** 26.0.0

**装饰器类型：** \@ComponentV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。


| 名称 | 类型 | 必填 | 装饰器类型 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| treeControllerV2 | [TreeControllerV2](#treecontrollerv2) | 是 | @Param | 树视图节点控制器，用于控制树的节点信息，绑定至树视图组件后可通过该控制器对节点进行新增、删除、修改等操作。同一个控制器不可以控制多个树视图组件。 |

### build

build(): void

build函数用于构造TreeViewV2高级组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**装饰器类型：** \@Builder

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**ArkTS-Sta起始版本：** 26.0.0


## TreeControllerV2

树视图组件的控制器，用于控制树的节点信息。将此对象绑定至树视图组件后使用，同一个控制器不可以控制多个树视图组件。

### addNode

addNode(nodeParam?: NodeParamV2): TreeControllerV2

点击某个节点后，调用该方法可以触发新增子节点。添加节点完成后，必须调用[buildDone()](#builddone)方法触发树信息的保存，否则添加的节点不会显示在树视图上。支持链式调用，如addNode().addNode().buildDone()。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| nodeParam | [NodeParamV2](#nodeparamv2) | 否 | 节点信息，用于指定新增节点的属性。如果不传该参数，在当前选中的节点下添加一个标题为"新建文件夹"的节点。 |

**返回值：** 

| 类型                              | 说明                 |
| --------------------------------- | -------------------- |
| [TreeControllerV2](#treecontrollerv2) | 树视图组件的控制器，用于链式调用其他树视图控制方法。 |

### removeNode

removeNode(): void

点击某个节点后，调用该方法删除该节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

### modifyNode

modifyNode(): void

点击某个节点后，调用该方法修改该节点，使其进入编辑态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

### buildDone

buildDone(): void

建立树视图。节点增加完毕后，必须调用该方法，触发树信息的保存。该接口采用两阶段构建模式：先通过addNode将节点添加到内存中，再调用本方法统一保存节点信息并渲染到树视图。未调用本方法时，已添加的节点不会显示在树视图中。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。


### refreshNode

ArkTS-Dyn：refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void

ArkTS-Sta：refreshNode(parentId: int, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void

调用该方法，根据传入的parentId定位父节点，更新父节点的副标题（parentSubTitle）和当前节点的副标题（currentSubtitle）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| parentId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 父节点Id。<br />取值范围：大于等于-1。<br />传入小于-1的值时，节点无效。 |
| parentSubTitle | [ResourceStr](ts-types.md#resourcestr) | 是 | 父节点副标题，用于更新父节点的副标题显示内容。 |
| currentSubtitle | [ResourceStr](ts-types.md#resourcestr) | 是 | 当前节点副标题，用于更新当前节点的副标题显示内容。 |

## NodeParamV2

节点参数接口，用于配置树节点的属性。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

| 名称 | 类型 | 只读 | 可选 | 说明                                                                                                                                               |
| -------- | -------- |---|---|--------------------------------------------------------------------------------------------------------------------------------------------------|
| parentNodeId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 是 | 父节点Id。<br />取值范围：大于等于-1。<br />默认值：-1，根节点Id值为-1。若设置数值小于-1，该节点无效，不显示在树视图上。 |
| currentNodeId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 是 | 当前子节点Id。<br />取值范围：大于等于-1。<br />不能为根节点Id，不能为null，否则会抛出异常。且不能设置两个相同的currentNodeId。<br />默认值：-1，表示未指定节点Id，此时节点Id由系统自动分配。 |
| isFolder | boolean | 否 | 是 | 是否是文件夹。传入true时节点为目录节点，可包含子节点（当需要创建可展开的父节点时选择）；传入false时节点为叶子节点，不可包含子节点（当需要创建不可展开的末级节点时选择）。不传入时默认为false（叶子节点）。                                                         |
| icon | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 图标，用于自定义节点的默认图标。当需要为节点指定自定义图标时传入此参数，不传入时节点显示系统默认图标。同时设置symbolIconStyle时，仅显示Symbol图标，icon不生效。<br/>默认值：空字符串，表示不显示自定义图标。 |
| symbolIconStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | 否 | 是 | Symbol图标样式，用于设置系统Symbol类型的图标。当需要使用系统Symbol图标（如需要与系统风格一致、支持动态颜色等场景）时传入此参数，不传入时使用icon参数指定的图标。显示优先级大于icon，同时设置symbolIconStyle和icon，只显示Symbol图标。<br/>默认值：undefined，表示不显示Symbol图标。                  |
| selectedIcon | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 选中图标，用于自定义节点被选中时的图标。当需要在节点选中状态下显示不同于默认状态的图标时传入此参数，不传入时节点选中后显示与未选中状态相同的图标。同时设置symbolSelectedIconStyle时，仅显示Symbol选中图标，selectedIcon不生效。<br/>默认值：空字符串，表示选中时不显示自定义选中图标。 |
| symbolSelectedIconStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | 否 | 是 | Symbol选中图标样式，用于设置节点选中时的系统Symbol图标。当需要使用系统Symbol图标作为选中图标（如需要与系统风格一致、支持动态颜色等场景）时传入此参数，不传入时节点选中后显示与未选中状态相同的图标。优先级大于selectedIcon，同时设置symbolSelectedIconStyle和selectedIcon时，只显示Symbol选中图标。<br/>默认值：undefined |
| editIcon | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 编辑图标，用于自定义节点进入编辑态时的图标。当需要在节点编辑状态下显示不同于默认状态的图标时传入此参数，不传入时节点编辑态显示与未编辑状态相同的图标。同时设置symbolEditIconStyle时，仅显示Symbol编辑图标，editIcon不生效。<br/>默认值：空字符串，表示编辑态不显示自定义编辑图标。 |
| symbolEditIconStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | 否 | 是 | Symbol编辑图标样式，用于设置节点编辑态的系统Symbol图标。当需要使用系统Symbol图标作为编辑图标（如需要与系统风格一致、支持动态颜色等场景）时传入此参数，不传入时节点编辑态显示与非编辑态相同的图标。优先级大于editIcon，同时设置symbolEditIconStyle和editIcon时，只显示Symbol编辑图标。<br/>默认值：undefined   |
| primaryTitle | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 主标题。<br/>默认值：空字符串，表示不显示主标题。                           |
| secondaryTitle | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 副标题。<br/>默认值：空字符串，表示不显示副标题。                         |
| container | [OnContainerCallback](#oncontainercallback) | 否 | 是 | 绑定在节点上的右键子组件容器，子组件由@Builder修饰。当需要为节点提供右键菜单或自定义右键操作时传入此参数，不传入时节点不显示右键菜单。<br/>默认值：() => void，表示不绑定右键子组件容器。 |

## TreeListenerManagerV2

树视图组件的监听管理器，用于管理树视图监听器的变化。将此对象绑定至树视图组件后使用，同一个监听管理器不可以控制多个树视图组件。该管理器采用单例模式设计，通过getInstance获取全局唯一实例，再通过getTreeListener获取监听器实例。

### getInstance

static getInstance(): TreeListenerManagerV2

获取树视图组件的监听管理器单例对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**返回值：**

| 类型              | 说明               |
| --------------- |------------------|
| [TreeListenerManagerV2](#treelistenermanagerv2) | 树视图组件的监听管理器单例对象。 |


### getTreeListener

getTreeListener(): TreeListenerV2

获取树视图监听器实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**返回值：**

| 类型           | 说明         |
| ------------ |------------|
| [TreeListenerV2](#treelistenerv2) | 树视图监听器实例，用于注册或取消树视图节点的点击、添加、删除、修改、移动等事件监听。 |


## TreeListenerV2

树视图组件的监听器，用于监听树视图节点的变化。将此对象绑定至树视图组件后使用，同一个树视图监听器不可以控制多个树视图组件。该监听器提供on和once两种事件注册方式：on方法持续监听事件直至取消，once方法监听一次后自动销毁。使用完毕后，需在组件销毁时调用offNodeClick、offNodeAdd等方法取消监听，避免内存泄漏。

### onNodeClick

onNodeClick(callback: OnChangedCallback): void

注册节点点击事件监听，持续生效。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点点击回调函数。 |


### onceNodeClick

onceNodeClick(callback: OnChangedCallback): void

注册节点点击事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点点击回调函数。 |


### offNodeClick

offNodeClick(callback?: OnChangedCallback): void

取消节点点击事件监听。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 否 | 节点点击回调函数。传入时取消对应的监听，否则取消所有节点点击监听。 |


### onNodeAdd

onNodeAdd(callback: OnChangedCallback): void

注册节点添加事件监听，持续生效。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点添加回调函数。 |


### onceNodeAdd

onceNodeAdd(callback: OnChangedCallback): void

注册节点添加事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点添加回调函数。 |


### offNodeAdd

offNodeAdd(callback?: OnChangedCallback): void

取消节点添加事件监听。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 否 | 节点添加回调函数。传入时取消对应的监听，否则取消所有节点添加监听。 |


### onNodeDelete

onNodeDelete(callback: OnChangedCallback): void

注册节点删除事件监听，持续生效。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点删除回调函数。 |


### onceNodeDelete

onceNodeDelete(callback: OnChangedCallback): void

注册节点删除事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点删除回调函数。 |


### offNodeDelete

offNodeDelete(callback?: OnChangedCallback): void

取消节点删除事件监听。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 否 | 节点删除回调函数。传入时取消对应的监听，否则取消所有节点删除监听。 |


### onNodeModify

onNodeModify(callback: OnChangedCallback): void

注册节点修改事件监听，持续生效。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点修改回调函数。 |


### onceNodeModify

onceNodeModify(callback: OnChangedCallback): void

注册节点修改事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点修改回调函数。 |


### offNodeModify

offNodeModify(callback?: OnChangedCallback): void

取消节点修改事件监听。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 否 | 节点修改回调函数。传入时取消对应的监听，否则取消所有节点修改监听。 |


### onNodeMove

onNodeMove(callback: OnChangedCallback): void

注册节点移动事件监听，持续生效，节点移动通过拖拽操作触发。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点移动回调函数。 |


### onceNodeMove

onceNodeMove(callback: OnChangedCallback): void

注册节点移动事件监听，监听一次后自动销毁。节点移动通过拖拽操作触发。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 是 | 节点移动回调函数。 |


### offNodeMove

offNodeMove(callback?: OnChangedCallback): void

取消节点移动事件监听。使用callback回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

**参数：**

| 参数名  | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | 否 | 节点移动回调函数。传入时取消对应的监听，否则取消所有节点移动监听。 |


## OnChangedCallback

type OnChangedCallback = (callbackParam: CallbackParamV2) => void

节点事件回调函数类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型      | 必填 | 说明                                            |
| :------ |:--------| :- | :-------------------------------------------------- |
| callbackParam | [CallbackParamV2](#callbackparamv2) | 是  | 节点回调参数，用于传递节点事件回调的参数信息。 |

## CallbackParamV2

节点回调参数接口，用于传递节点事件回调的参数信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

| 名称 | 类型 | 只读 | 可选 | 说明                                       |
| -------- | -------- |---|---|------------------------------------------|
| currentNodeId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 否 | 返回当前节点Id。<br />取值范围：大于等于0。              |
| parentNodeId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 是 | 返回当前父节点Id。<br />取值范围：大于等于-1。<br />默认值：-1  |
| childIndex | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 是 | 返回子索引。<br />取值范围：大于等于-1。<br />默认值：-1<br />仅在节点移动事件中有效，表示移动后的位置索引。   |

## OnContainerCallback

type OnContainerCallback = () => void

容器回调函数类型，用于定义绑定在树节点上的子组件回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 本接口实际支持的设备类型范围（Phone、PC/2in1、Tablet、TV）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Wearable）。因硬件能力限制，该接口在Wearable设备中调用将运行异常，异常信息中提示接口未定义。

## 事件
不支持[通用事件](ts-component-general-events.md)。

## 示例

### 示例1（设置树视图）

从API版本26.0.0开始，支持以下示例通过树视图组件的控制器接口对树视图的节点进行新增、删除、重命名等功能。

ArkTS-Dyn示例：
```ts
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
  // 新建树形视图控制器
  private treeControllerV2: TreeControllerV2 = new TreeControllerV2();
  // 新建树形视图监听器
  private treeListenerV2: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  // 记录当前点击的节点Id
  @Local clickNodeId: number = 0;

  // 组件销毁时，取消所有监听器
  aboutToDisappear(): void {
    this.treeListenerV2.offNodeClick();
    this.treeListenerV2.offNodeAdd();
    this.treeListenerV2.offNodeDelete();
    this.treeListenerV2.offNodeModify();
    this.treeListenerV2.offNodeMove();
  }

  // 组件初始化时。注册监听器并构建树结构
  aboutToAppear(): void {
    // 注册节点点击监听器
    this.treeListenerV2.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // 注册节点添加监听器
    this.treeListenerV2.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // 注册节点删除监听器
    this.treeListenerV2.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // 注册节点移动监听器（监听一次后自动销毁）
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
      primaryTitle: '目录1',
      secondaryTitle: '6'
    };

    // 构建树结构
    this.treeControllerV2
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: '项目1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: '目录2'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 23,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: '项目4'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 31,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录5',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 32,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录6',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 32,
        currentNodeId: 35,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录6-1',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 33,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: '项目8'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: '项目9'
      })
      .buildDone();

    this.treeControllerV2.refreshNode(-1, '父节点', '子节点');
  }

  build(): void {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        // 树形视图组件
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
ArkTS-Sta示例：
```ts
import {
  Entry, Component, Column, Builder, Flex, FlexDirection, FlexAlign, ItemAlign, TextAlign, ClickEvent, HorizontalAlign,
  Divider, Resource, SideBarContainer, SideBarContainerType, LineCapStyle, ColumnOptions, Button, ButtonType, Text, $r,
  Row, State
}from '@kit.ArkUI';
import {
  TreeControllerV2,  TreeListenerV2,  TreeListenerManagerV2,  NodeParamV2,  TreeViewV2,  CallbackParamV2
} from '@ohos.arkui.advanced.TreeViewV2';


@Entry
@Component
struct TreeView01 {
  // 创建树视图组件的控制器
  private treeController: TreeControllerV2 = new TreeControllerV2();
  // 创建树视图组件的监听器
  private treeListener: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  @State clickId: number = 0;

  aboutToDisappear(): void {
    // 取消监听
    this.treeListener.offNodeClick(undefined);
    this.treeListener.offNodeAdd(undefined);
    this.treeListener.offNodeDelete(undefined);
    this.treeListener.offNodeMove(undefined);
  }

  // 创建右侧菜单操作区
  @Builder
  menuBuilder1() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('新增')
        .fontSize(16)
        .width(100)
        .height(30)
        .textAlign(TextAlign.Center)
        .onClick((event: ClickEvent) => {
          this.treeController.addNode();
        })
      Divider()
      Text('删除')
        .fontSize(16)
        .width(100)
        .height(30)
        .textAlign(TextAlign.Center)
        .onClick((event: ClickEvent) => {
          this.treeController.removeNode();
        })
      Divider()
      Text('重命名')
        .fontSize(16)
        .width(100)
        .height(30)
        .textAlign(TextAlign.Center)
        .onClick((event: ClickEvent) => {
          this.treeController.modifyNode();
        })
    }.width(100).border({ width: 1, color: 0x80808a, radius: '16dp' })
  }

  aboutToAppear(): void {
    // 注册监听
    this.treeListener.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickId = callbackParam.currentNodeId;
    })
    this.treeListener.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickId = callbackParam.currentNodeId;
    })
    this.treeListener.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickId = callbackParam.currentNodeId;
    })
    this.treeListener.onceNodeMove((callbackParam: CallbackParamV2) => {
      this.clickId = callbackParam.currentNodeId;
    })

    // 系统文件夹图片资源
    let normalResource: Resource = $r('sys.media.ohos_ic_normal_white_grid_folder');
    // 系统全选图片资源
    let selectedResource: Resource = $r('sys.media.ohos_ic_public_select_all');
    // 系统编辑图片资源
    let editResource: Resource = $r('sys.media.ohos_ic_public_edit');
    let nodeParam: NodeParamV2 = {
      parentNodeId: -1,
      currentNodeId: 1,
      isFolder: true,
      icon: normalResource,
      selectedIcon: selectedResource,
      editIcon: editResource,
      primaryTitle: '目录1验证悬浮框自适应效果是否OK',
      secondaryTitle: '6'
    };
    // 添加树节点
    this.treeController
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: '项目1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: '目录2'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 23,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: '项目4'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 31,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录5',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 32,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录6',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 32,
        currentNodeId: 35,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录6-1',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 33,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: '目录7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: '项目8'
      })
      .addNode({ parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: '项目9'
      })
      .buildDone();
    this.treeController.refreshNode(-1, '父节点', '子节点');
  }

  build() {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        TreeViewV2({ treeControllerV2: this.treeController })
        Row() {
          Divider().vertical(true).strokeWidth(2).color(0x000000).lineCap(LineCapStyle.Round)
          Column({ space: 30 } as ColumnOptions) {
            Text('ClickId=' + this.clickId).fontSize('16fp')
            Button('Add', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeController.addNode();
              })
            Button('Modify', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeController.modifyNode();
              })
            Button('Remove', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(120)
              .onClick((event: ClickEvent) => {
                this.treeController.removeNode();
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

![示例1](figures/image-treeviewv2-demo-01.png)

### 示例2（设置Symbol类型图标）

从API版本26.0.0开始，支持以下示例通过设置[NodeParamV2](#nodeparamv2)的symbolIconStyle、symbolEditIconStyle、symbolSelectedIconStyle等属性接口，实现树视图中自定义Symbol类型图标的功能。

ArkTS-Dyn示例：
```ts
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
  // 新建树形视图控制器
  private treeControllerV2: TreeControllerV2 = new TreeControllerV2();
  // 新建树形视图监听器
  private treeListenerV2: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  // 记录当前点击的节点Id
  @Local clickNodeId: number = 0;

  // 组件销毁时，取消所有监听器
  aboutToDisappear(): void {
    this.treeListenerV2.offNodeClick();
    this.treeListenerV2.offNodeAdd();
    this.treeListenerV2.offNodeDelete();
    this.treeListenerV2.offNodeModify();
    this.treeListenerV2.offNodeMove();
  }

  // 组件初始化时。注册监听器并构建树结构
  aboutToAppear(): void {
    // 注册节点点击监听器
    this.treeListenerV2.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // 注册节点添加监听器
    this.treeListenerV2.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // 注册节点删除监听器
    this.treeListenerV2.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // 注册节点移动监听器
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
      primaryTitle: '目录1',
      secondaryTitle: '6'
    };

    // 构建树结构
    this.treeControllerV2
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: '项目1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: '目录2'
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
        primaryTitle: '目录3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: '项目4'
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
        primaryTitle: '目录5',
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
        primaryTitle: '目录6',
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
        primaryTitle: '目录6-1',
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
        primaryTitle: '目录7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: '项目8'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: '项目9'
      })
      .buildDone();

    this.treeControllerV2.refreshNode(-1, '父节点', '子节点');
  }

  build(): void {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        // 树形视图组件
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
ArkTS-Sta示例：
```ts
import {
  Entry,
  Component,
  Column,
  Builder,
  Flex,
  FlexDirection,
  FlexAlign,
  ItemAlign,
  TextAlign,
  ClickEvent,
  HorizontalAlign,
  Divider,
  Resource,
  SideBarContainer,
  SideBarContainerType,
  LineCapStyle,
  ColumnOptions,
  Button,
  ButtonType,
  Text,
  $r,
  Row,
  SymbolGlyphModifier,
  Color,
  State
} from '@kit.ArkUI';
import {
  TreeControllerV2,
  TreeListenerV2,
  TreeListenerManagerV2,
  NodeParamV2,
  TreeViewV2,
  CallbackParamV2
} from '@ohos.arkui.advanced.TreeViewV2';

@Entry
@Component
struct TreeView02 {
  // 创建树视图组件的控制器
  private treeController: TreeControllerV2 = new TreeControllerV2();
  // 创建树视图组件的监听器
  private treeListener: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  @State clickNodeId: number = 0;

  aboutToDisappear(): void {
    // 注册监听
    this.treeListener.offNodeClick(undefined);
    this.treeListener.offNodeAdd(undefined);
    this.treeListener.offNodeDelete(undefined);
    this.treeListener.offNodeMove(undefined);
  }

  aboutToAppear(): void {
    // 注册监听
    this.treeListener.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    this.treeListener.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    this.treeListener.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    this.treeListener.onceNodeMove((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })

    // 系统房屋符号资源
    let normalResource: Resource = $r('sys.symbol.house');
    // 系统汽车符号资源
    let selectedResource: Resource = $r('sys.symbol.car');
    // 系统日历符号资源
    let editResource: Resource = $r('sys.symbol.calendar');
    let normalSymbolResource: SymbolGlyphModifier =
      new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]); // 系统响铃符号资源
    let selectedSymbolResource: SymbolGlyphModifier =
      new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Blue]); // 系统心型符号资源
    let editSymbolResource: SymbolGlyphModifier =
      new SymbolGlyphModifier($r('sys.symbol.cake')).fontColor([Color.Pink]); // 系统蛋糕符号资源
    let nodeParam: NodeParamV2 = {
      parentNodeId: -1,
      currentNodeId: 1,
      isFolder: true,
      icon: normalResource,
      selectedIcon: selectedResource,
      editIcon: editResource,
      primaryTitle: '目录1',
      secondaryTitle: '6'
    };
    // 添加树节点
    this.treeController
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: '项目1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: '目录2'
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
        primaryTitle: '目录3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: '项目4'
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
        primaryTitle: '目录5',
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
        primaryTitle: '目录6',
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
        primaryTitle: '目录6-1',
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
        primaryTitle: '目录7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: '项目8'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: '项目9'
      })
      .buildDone();
    this.treeController.refreshNode(-1, '父节点', '子节点');
  }

  build() {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        TreeViewV2({ treeControllerV2: this.treeController })
        Row() {
          Divider().vertical(true).strokeWidth(2).color(0x000000).lineCap(LineCapStyle.Round)
          Column({ space: 30 } as ColumnOptions) {
            Text('ClickNodeId=' + this.clickNodeId).fontSize('16fp')
            Button('Add', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeController.addNode();
              })
            Button('Modify', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeController.modifyNode();
              })
            Button('Remove', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(120)
              .onClick((event: ClickEvent) => {
                this.treeController.removeNode();
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

![示例2](figures/image-treeviewv2-demo-02.png)
