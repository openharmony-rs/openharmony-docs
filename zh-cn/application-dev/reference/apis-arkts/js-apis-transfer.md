# @ohos.transfer (系统对象转换工具)

ArkTS1.1和ArkTS1.2交互过程中，存在系统对象的交互。本模块提供了系统对象转换能力：

- 从ArkTS1.2系统对象转换为ArkTS1.1系统对象的能力。

- 从ArkTS1.1系统对象转换为ArkTS1.2系统对象的能力。

> **说明：**
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块仅使用于ArkTS1.2。
>
> - 本模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。

## 导入模块

```ts
import { transfer } from '@kit.ArkTS'
```

## transfer.transferStatic

transferStatic(input: Any, inputName: string): Object

从ArkTS1.1系统对象转换为ArkTS1.2系统对象。

**原子化服务API**：从API version 20 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 名称 | 类型   | 必填 | 说明                             |
| ---- | ------ | ---- | -------------------------------- |
| input | Any | 是   | 待转换的ArkTS1.1对象。 |
| inputName | string | 是   | 转换对象的key值，取值参见[key值列表](#转换对象key值列表)。 |

**返回值：**

| 类型                    | 说明                             |
| ----------------------- | -------------------------------- |
| Object | 转换后的ArkTS1.2对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 10200067 | Transfer Error. The input name is not supported! |

**示例：**

```ts
// ArkTS1.1环境
import { dyamic2Static } from 'har2';
let dynamic_obj = new ArrayBuffer(8);
dyamic2Static(dynamic_obj); // 调用ArkTS1.2环境中的dyamic2Static方法
    
// ArkTS1.2环境
import { transfer } from '@kit.ArkTS'
function dyamic2Static(dynamic_obj: Any) {
   let static_obj = transfer.transferStatic(dynamic_obj, 'InteropTransferHelper')
   // handle static_obj
}
```

## transfer.transferDynamic

transferDynamic(input: Object, inputName: string): Any

从ArkTS1.2系统对象转换为ArkTS1.1系统对象。

**原子化服务API**：从API version 20 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 名称 | 类型   | 必填 | 说明                             |
| ---- | ------ | ---- | -------------------------------- |
| input | Object | 是   | 待转换的ArkTS1.2对象。 |
| inputName | string | 是   | 转换对象的key值，取值参见[key值列表](#转换对象key值列表)。 |

**返回值：**

| 类型                    | 说明                             |
| ----------------------- | -------------------------------- |
| Any | 转换后的ArkTS1.1对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 10200067 | Transfer Error. The input name is not supported! |

**示例：**

```ts
// ArkTS1.2环境
import { transfer } from '@kit.ArkTS'

let static_obj = new ArrayBuffer(8);
let dynamic_obj = transfer.transferDynamic(static_obj, 'InteropTransferHelper')
// 调用1.0中的har1func方法处理dynamic_obj
let moduleName = ESValue.load('@nomalized:....');
let har1func = moduleName.getProperty('har1func');  
har1func.invoke(ESObject.wrap(dynamic_obj));


// ArkTS1.1环境
export function har1func(dynamic_obj: Any) {
    // handle dynamic_obj
}
```

## 转换对象key值列表
| key  |系统对象 |
|------ | ----  |
|"InteropTransferHelper" | [ArrayBuffer](../../arkts-utils/arraybuffer-object.md)|
| "ArkUI.NavDestinationInfo" | [uiObserver.NavDestinationInfo](../apis-arkui/js-apis-arkui-observer.md#navdestinationinfo)|
| "ArkUI.NavigationInfo" | [uiObserver.NavigationInfo](../apis-arkui/js-apis-arkui-observer.md#navigationinfo12)|
| "ArkUI.RouterPageInfo" | [uiObserver.RouterPageInfo](../apis-arkui/js-apis-arkui-observer.md#routerpageinfo)| 
| "AbilityKit.UIAbilityContext" | [common.UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#uiabilitycontext)|   
