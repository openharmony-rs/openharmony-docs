# enable

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## enable

```TypeScript
function enable(isEnable: boolean): void
```

使能ArkTS对象泄漏检测，默认关闭。开启后会收集泄漏信息，可能增加性能开销。

推荐的完整调用流程：enable() → watch() → check() → dump()

使用场景：

- 应用开发调试阶段，用于检测和定位内存泄漏问题。  
- 应用测试阶段，用于验证应用的内存管理是否正常。  
- 对内存使用有严格要求的应用，需要持续监控内存状态。

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnable | boolean | 是 | 是否使能jsLeakWatcher。true：使能jsLeakWatcher；false：不使能jsLeakWatcher。 |

**示例**

```TypeScript
jsLeakWatcher.enable(true);
```
