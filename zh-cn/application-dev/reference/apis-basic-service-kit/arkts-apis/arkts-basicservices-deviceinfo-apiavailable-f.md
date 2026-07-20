# apiAvailable

## 导入模块

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';
```

<a id="apiavailable"></a>
## apiAvailable

```TypeScript
function apiAvailable(version: string | number): boolean
```

检查指定的API版本在当前设备上是否可用。此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-function apiAvailable(version: string | number): boolean--><!--Device-deviceInfo-function apiAvailable(version: string | number): boolean-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| version | string \| number | 是 | 需要校验的API版本号，支持整数版本号和点分版本号。整数版本号范围：0<x<26。OpenHarmony点分版本号格式为M.S.F（如26.0.0），M>=26,0<=S<=99,0<=F<=99。传入无效值时报错。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 布尔值。返回true表示当前设备API版本大于等于入参版本号；返回false则表示当前设备API版本小于入参版本号 |

**示例：**

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';

// 检查API版本是否大于等于26.0.0（返回true表示当前设备API版本满足要求）
if (deviceInfo.apiAvailable('26.0.0')) {
  // 需要版本隔离的方法
}


// Check API 5.0.1 (Distribution OS version, API 26.0.0-)
if (deviceInfo.apiAvailable('5.0.1')) {
  // 需要版本隔离的方法
}


// Check API 13 (OpenHarmony SDK version, API 26.0.0-)
if (deviceInfo.apiAvailable(13)) {
  // 需要版本隔离的方法
}


```

