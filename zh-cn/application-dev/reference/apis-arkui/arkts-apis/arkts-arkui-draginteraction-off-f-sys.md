# off（系统接口）

## 导入模块

```TypeScript
import { dragInteraction } from '@kit.ArkUI';
```

## off('drag')

```TypeScript
function off(type: 'drag', callback?: Callback<DragState>): void
```

取消监听拖拽状态。

**起始版本：** 10

<!--Device-dragInteraction-function off(type: 'drag', callback?: Callback<DragState>): void--><!--Device-dragInteraction-function off(type: 'drag', callback?: Callback<DragState>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drag' | 是 | 监听类型，固定取值为 'drag'。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;DragState&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2.Incorrect parameter types.3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
// 取消注册单个回调函数
function single_callback(event: dragInteraction.DragState) {
  console.info(`Drag interaction event: ${event}`);
  return false;
}
try {
  dragInteraction.on('drag', single_callback);
  dragInteraction.off("drag", single_callback);
} catch (error) {
  console.error(`Execute failed, code: ${error.code}, message: ${error.message}`);
}

```

```TypeScript
// 取消注册所有回调函数
function all_callback(event: dragInteraction.DragState) {
  console.info(`Drag interaction event: ${event}`);
  return false;
}
try {
  dragInteraction.on('drag', all_callback);
  dragInteraction.off("drag");
} catch (error) {
  console.error(`Execute failed, code: ${error.code}, message: ${error.message}`);
}

```

