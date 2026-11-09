# setGlobalPriorityCursor（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setGlobalPriorityCursor

```TypeScript
function setGlobalPriorityCursor(cursor: CustomCursor): Promise<void>
```

设置全局高优先级光标。设置成功后，当光标可见时光标样式将被锁定和限制，不受其他样式的影响，直到它被清除或被新的全局高优先级光标覆盖。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_CURSOR_STYLE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pointer-function setGlobalPriorityCursor(cursor: CustomCursor): Promise<void>--><!--Device-pointer-function setGlobalPriorityCursor(cursor: CustomCursor): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cursor | [CustomCursor](arkts-input-pointer-customcursor-i.md) | 是 | 光标资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes:         1. The hardware does not support the capability; 2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [3800001](../errorcode-infraredemitter.md#3800001-多模输入服务内部错误) | Input service exception. Possible causes: 1. Memory allocation failure.         2. Thread busy. 3. Service terminated abnormally. 4. Other unexpected errors. Try again later. |
