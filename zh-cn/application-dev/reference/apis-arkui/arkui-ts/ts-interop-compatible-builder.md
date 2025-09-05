# transferCompatibleBuilder (ArkTS-Sta)(系统接口)

transferCompatibleBuilder被用于在ArkTS-Sta中给ArkTS-Dyn的@BuilderParam传递自定义构建函数。

> **说明：**
>
> 本模块仅适用于ArkTS-Sta。
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，无公开接口。

## transferCompatibleBuilder

transferCompatibleBuilder\<T extends Function\>(@Builder builder: T): ESValue

在ArkTS-Sta中给ArkTS-Dyn的@BuilderParam传递@Builder函数（适用于非字面量更新场景）。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|builder| T  |是   |自定义构建函数。   |

**返回值：**

|类型   |说明       |
|-----------|--------------|
|[ESValue](../../../quick-start/arkts-interop-overview.md#esvalue)  |可互操作的自定义构建函数。 |


## CompatibleUpdatableBuilder

type CompatibleUpdatableBuilder\<T\> = (arg: T) => void

自定义构建函数的类型。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|arg| T  |是   |自定义构建函数。   |


## transferCompatibleUpdatableBuilder

transferCompatibleUpdatableBuilder\<T extends Object\>(builder: CompatibleUpdatableBuilder\<T\>): ESValue

在ArkTS-Sta中给ArkTS-Dyn的@BuilderParam传递@Builder函数（适用于字面量更新场景）。

**ArkTS模式**：该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本**：20

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|builder| [CompatibleUpdatableBuilder\<T\>](#compatibleupdatablebuilder)  |是   |自定义构建函数。   |

**返回值：**

|类型   |说明       |
|-----------|--------------|
|[ESValue](../../../quick-start/arkts-interop-overview.md#esvalue)  |可互操作的自定义构建函数。 |
