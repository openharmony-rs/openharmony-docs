# watch

## 导入模块

```TypeScript
```

## watch

```TypeScript
function watch(obj: object, msg: string): void
```

注册待检测泄漏的对象。使用场景：  
- 在创建可能发生泄漏的关键对象后（如自定义组件、Window等），立即注册进行监控。  
- 对应用生命周期中的重要对象进行注册，以便及时发现泄漏。  
- 在特定功能模块中使用到的对象，如XComponent、NodeContainer等，注册以监控其释放情况。

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | 需要检测的对象。    **说明：**可传入任何非null的ArkTS对象，不支持undefined和基本类型。 |
| msg | string | 是 | 自定义对象信息。 |

**示例**

```TypeScript
let obj:Object = new Object();
jsLeakWatcher.watch(obj, "Trace Object");
```
