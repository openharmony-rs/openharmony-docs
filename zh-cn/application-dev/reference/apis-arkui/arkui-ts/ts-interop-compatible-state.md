# compatibleState (ArkTS-Sta)(系统接口)

compatibleState是用于在ArkTS-Sta中与ArkTS-Dyn状态变量进行互操作的模块。


> **说明：**
>
> 本模块仅适用于ArkTS-Sta。
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，无公开接口。


## getCompatibleState

function getCompatibleState<T>(state: IDecoratedV1Variable<T>): ESValue;

为ArkTS-Sta的状态变量获取一个ArkTS-Dyn的@State代理对象，用于与ArkTS-Dyn的状态变量进行互操作。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

**参数：**

|名称   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|state     |IDecoratedV1Variable   |是   |ArkTS-Sta的状态变量。    |


**返回值：**

|类型   | 说明             |
|------------|--------------|
|[ESValue](../../../quick-start/arkts-interop-overview.md#esvalue)   |ArkTS-Dyn的@State对象。    |


