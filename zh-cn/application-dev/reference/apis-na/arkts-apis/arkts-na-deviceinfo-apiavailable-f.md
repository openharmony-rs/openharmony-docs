# apiAvailable

## 导入模块

```TypeScript
```

## apiAvailable

```TypeScript
function apiAvailable(version: string | int): boolean
```

检查指定的API版本在当前设备上是否可用。 此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceInfo-function apiAvailable(version: string | int): boolean--><!--Device-deviceInfo-function apiAvailable(version: string | int): boolean-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| version | string \| int | 是 | 需要校验的API版本号，支持整数格式版本号和字符串格式版本号。 - 字符串采用M.S.F格式（如 "26.0.0","5.0.1"）： - 对于API 26.0.0及以上版本（version >= 26.0.0）：代表OpenHarmony和发行版系统API版本。 - 对于API 26.0.0以下版本（version &lt; 26.0.0）：代表发行版系统API版本。 - 整数格式（如13）：代表OpenHarmony SDK API版本。（仅支持API 26以下） M&gt;=26,0&lt;=S&lt;=99,0&lt;=F&lt;=99。传入无效字面量时编译报错。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 布尔值。返回true表示当前设备API版本大于等于入参版本号；返回false代表当前设备API版本小于入参版本号，或传入的版本号格式非法、该版本不存在。 |

