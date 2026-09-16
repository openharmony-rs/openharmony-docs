# requestRebuildHyperSnap

## 导入模块

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## requestRebuildHyperSnap

```TypeScript
function requestRebuildHyperSnap(): void
```

请求重新初始化应用快启。

此方法会销毁当前进程已经初始化的快启数据，系统将在合适的时机重新进行快启初始化。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000150](../errorcode-ability.md#16000150-发送请求失败) | Failed to send request to system service. |
