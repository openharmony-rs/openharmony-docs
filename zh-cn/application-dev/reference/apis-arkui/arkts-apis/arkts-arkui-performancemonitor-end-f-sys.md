# end（系统接口）

## 导入模块

```TypeScript
import { performanceMonitor } from '@kit.ArkUI';
```

<a id="end"></a>
## end

```TypeScript
function end(scene: string): void
```

用于标记用户场景结束，用户场景结束时调用此接口。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-performanceMonitor-function end(scene: string): void--><!--Device-performanceMonitor-function end(scene: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scene | string | 是 | 用户场景id，与begin配对严格保持一致，否则本次场景监测无效。 |

**示例：**

用户点击图标启动应用场景动效结束点。

```TypeScript
performanceMonitor.end("LAUNCHER_APP_LAUNCH_FROM_ICON");

```

