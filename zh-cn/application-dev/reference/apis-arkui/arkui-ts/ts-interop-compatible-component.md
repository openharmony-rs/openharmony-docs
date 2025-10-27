# compatibleComponent (ArkTS-Sta)(系统接口)

compatibleComponent是用于在ArkTS-Sta中引用ArkTS-Dyn自定义组件的占位组件。

> **说明：**
>
> 本模块仅适用于ArkTS-Sta。
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，无公开接口。

## compatibleComponent

compatibleComponent(init: CompatibleInitCallback, update: CompatibleUpdateCallback): void

在ArkTS-Sta中引用ArkTS-Dyn自定义组件的占位组件。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|init     | [CompatibleInitCallback](#compatibleinitcallback)   |是   |初始化占位组件的回调函数。    |
|update   | [CompatibleUpdateCallback](#compatibleupdatecallback)  |是   |更新占位组件的回调函数。   |
|component| ExtendableComponent  |否   |当前ArkTS-Sta自定义组件。   |


## CompatibleInitCallback

type CompatibleInitCallback = () => CompatibleComponentInfo

初始化占位组件的回调函数类型。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

**返回值：**

|类型   |说明       |
|-----------|--------------|
|[CompatibleComponentInfo](#compatiblecomponentinfo)  |占位组件的信息。 |



## CompatibleUpdateCallback

type CompatibleUpdateCallback = (component: ESValue) => void

更新占位组件的回调函数类型。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|component   |[ESValue](../../../quick-start/arkts-interop-overview.md#esvalue)   |是   |在ArkTS-Dyn上下文创建的自定义组件对象。    |



## CompatibleComponentInfo

interface CompatibleComponentInfo {
  name: string;
  component: ESValue;
}

在ArkTS-Dyn中创建的自定义组件对象的信息。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

|名称   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|name     |string   |是   |在ArkTS-Dyn中创建的自定义组件对象的名称。    |
|component   |[ESValue](../../../quick-start/arkts-interop-overview.md#esvalue)   |是   |在ArkTS-Dyn中创建的自定义组件对象。    |


