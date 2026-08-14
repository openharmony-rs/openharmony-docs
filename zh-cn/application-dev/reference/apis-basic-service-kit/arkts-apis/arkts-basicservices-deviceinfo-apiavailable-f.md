# apiAvailable

## apiAvailable

```TypeScript
function apiAvailable(version: string | number): boolean
```

检查指定的API版本在当前设备上是否可用。 此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-function apiAvailable(version: string | number): boolean--><!--Device-deviceInfo-function apiAvailable(version: string | number): boolean-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| version | string \| number | 是 | 需要校验的API版本号，支持整数格式版本号和字符串格式版本号。 - 字符串采用M.S.F格式（如 "26.0.0","5.0.1"）： - 对于API 26.0.0及以上版本（version >= 26.0.0）：代表OpenHarmony和发行版系统API版本。 - 对于API 26.0.0以下版本（version &lt; 26.0.0）：代表发行版系统API版本。 - 整数格式（如 13）：代表OpenHarmony SDK API版本。（仅支持API 26以下） M&gt;=26,0<=S<=99,0<=F<=99。传入无效字面量时编译报错。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 布尔值。返回true表示当前设备API版本大于等于入参版本号；返回false代表当前设备API版本小于入参版本号，或传入的版本号格式非法、该版本不存在。 |

## 示例

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

