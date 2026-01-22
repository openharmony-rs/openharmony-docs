# @ohos.deviceStatus.dragInteraction（拖拽)(系统接口)

拖拽功能模块，提供注册和取消拖拽状态监听的能力。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口均为系统接口。

## 导入模块

```js
import { dragInteraction } from '@kit.ArkUI';
```

## DragState

拖拽状态。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称                  | 值   | 说明           |
| --------------------- | ---- | -------------- |
| MSG_DRAG_STATE_START  | 1    | 表示开始拖拽。 |
| MSG_DRAG_STATE_STOP   | 2    | 表示结束拖拽。 |
| MSG_DRAG_STATE_CANCEL | 3    | 表示取消拖拽。 |

## Summary<sup>11+</sup>

拖拽对象的数据摘要。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称       | 类型     | 必填 | 说明               |
| ---------- | -------- | ---- | ------------------ |
| dataType   | string   | 是   | 拖拽对象类型。     |
| dataSize   | ArkTS-Dyn: number<br/>ArkTS-Sta: int   | 是   | 拖拽对象数据长度。 |

## dragInteraction.on('drag')<sup>12+</sup>

on(type: 'drag', callback: Callback\<DragState>): void

注册监听拖拽状态。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onDragStateChange](#dragInteractionondragstatechange23)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名   | 类型                               | 必填 | 说明                             |
| -------- | ---------------------------------- | ---- | -------------------------------- |
| type     | string                             | 是   | 监听类型，固定取值为 'drag'。    |
| callback | Callback\<[DragState](#dragstate)> | 是   | 回调函数，异步返回拖拽状态消息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |

**示例：**

```ts
try {
  dragInteraction.on('drag', (data: dragInteraction.DragState) => {
    console.log(`Drag interaction event: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

## dragInteraction.onDragStateChange<sup>23+</sup>

onDragStateChange(callback: Callback<DragState>): void

注册监听拖拽状态。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('drag')](#dragInteractionondrag12)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                               | 必填 | 说明                             |
| -------- | ---------------------------------- | ---- | -------------------------------- |
| callback | Callback\<[DragState](#dragstate)> | 是   | 回调函数，异步返回拖拽状态消息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Not system application. |

**示例：**

```ts
try {
  dragInteraction.onDragStateChange((data: dragInteraction.DragState) => {
    console.log(`Drag interaction event: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

## dragInteraction.off('drag')<sup>12+</sup>

off(type: 'drag', callback?: Callback\<DragState>): void

取消监听拖拽状态。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offDragStateChange](#dragInteractionoffdragstatechange23)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名   | 类型                               | 必填 | 说明                                                                   |
| -------- | ---------------------------------- | ---- | ---------------------------------------------------------------------- |
| type     | string                             | 是   | 监听类型，固定取值为 'drag'。                                          |
| callback | Callback\<[DragState](#dragstate)> | 否   | 需要取消注册的回调函数，若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |

**示例：**

```ts
// 取消注册单个回调函数
function single_callback(event: dragInteraction.DragState) {
  console.log(`Drag interaction event: ${JSON.stringify(event)}`);
  return false;
}
try {
  dragInteraction.on('drag', single_callback);
  dragInteraction.off("drag", single_callback);
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

```ts
// 取消注册所有回调函数
function all_callback(event: dragInteraction.DragState) {
  console.log(`Drag interaction event: ${JSON.stringify(event)}`);
  return false;
}
try {
  dragInteraction.on('drag', all_callback);
  dragInteraction.off("drag");
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

## dragInteraction.offDragStateChange<sup>23+</sup>

offDragStateChange(callback?: Callback<DragState>): void

取消监听拖拽状态。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('drag')](#dragInteractionoffdrag12)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                               | 必填 | 说明                                                                   |
| -------- | ---------------------------------- | ---- | ---------------------------------------------------------------------- |
| callback | Callback\<[DragState](#dragstate)> | 否   | 需要取消注册的回调函数，若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Not system application. |

**示例：**

```ts
// 取消注册单个回调函数
function single_callback(event: dragInteraction.DragState) {
  console.log(`Drag interaction event: ${JSON.stringify(event)}`);
  return;
}
try {
  dragInteraction.onDragStateChange(single_callback);
  dragInteraction.offDragStateChange(single_callback);
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

```ts
// 取消注册所有回调函数
function all_callback(event: dragInteraction.DragState) {
  console.log(`Drag interaction event: ${JSON.stringify(event)}`);
  return;
}
try {
  dragInteraction.onDragStateChange(all_callback);
  dragInteraction.offDragStateChange();
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

## dragInteraction.getDataSummary<sup>11+</sup>

getDataSummary(): Array\<Summary>

获取所有拖拽对象的摘要。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                          | 说明                                                 |
| ----------------------------- | ---------------------------------------------------- |
| Array\<[Summary](#summary11)> | 所有拖拽对象的数据摘要，包含拖拽对象的类型和数据长度。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Not system application. |

**示例：**

```ts
let summarys: Array<dragInteraction.Summary> = dragInteraction.getDataSummary();
console.log(`Drag interaction summarys: ${JSON.stringify(summarys)}`);
```

## dragInteraction.setDragSwitchState<sup>18+</sup>

setDragSwitchState(enabled: boolean): void

控制统一拖拽功能总开关。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                               | 必填 | 说明                                                                   |
| -------- | ---------------------------------- | ---- | ---------------------------------------------------------------------- |
| enabled  | boolean                            | 是   | 设置开关状态。<br>false：关闭，true：开启。                                              |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Not system application. |

**示例：**

```ts
try {
  dragInteraction.setDragSwitchState(false);
} catch (err:BusinessError) {
  console.error(`Failed to setDragSwitchState, code: ${err.code}, message: ${err.message}`);
}
```

## dragInteraction.setAppDragSwitchState<sup>18+</sup>

setAppDragSwitchState(enabled: boolean, bundleName: string): void

控制统一拖拽适配应用开关。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                               | 必填 | 说明                                                                   |
| --------   | ---------------------------------- | ---- | ---------------------------------------------------------------------- |
| enabled    | boolean                            | 是   | 设置开关状态。<br>false：关闭，true：开启。 |
| bundleName | string                             | 是   | 设置指定应用包名。长度取值范围（0, 128]。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。
	
| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |

**示例：**

```ts
try {
  dragInteraction.setAppDragSwitchState(true, "com.app.bundleName");
} catch (err:BusinessError) {
  console.error(`Failed to setAppDragSwitchState, code: ${err.code}, message: ${err.message}`);
}
```