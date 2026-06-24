# apiAvailable

## apiAvailable

```TypeScript
function apiAvailable(version: string | number): boolean
```

<!--RP13-->

检查指定的API版本在当前设备上是否可用。

此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。

**起始版本：** 26.0.0

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| version | string \| number | 是 | 需要校验的API版本号，支持整数版本号和点分版本号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns `true` if the specified API version is available on the<br/>current device, `false` otherwise. |

**示例：**

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';

// Check API 26.0.0 (String format for API 26.0.0+ represents both OpenHarmony and Distribution OS)
if (deviceInfo.apiAvailable("26.0.0")) {
   // 需要版本隔离的方法
}


// Check API 5.0.1 (Distribution OS version, API 26.0.0-)
if (deviceInfo.apiAvailable("5.0.1")) {
   // 需要版本隔离的方法
}


// Check API 13 (OpenHarmony SDK version, API 26.0.0-)
if (deviceInfo.apiAvailable(13)) {
   // 需要版本隔离的方法
}


```

