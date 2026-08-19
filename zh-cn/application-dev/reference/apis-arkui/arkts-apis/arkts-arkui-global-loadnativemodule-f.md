# loadNativeModule

## 导入模块

```TypeScript
```

## loadNativeModule

```TypeScript
export declare function loadNativeModule(moduleName: string): Object
```

同步动态加载native模块，目的是按需加载所需要的模块。 使用该接口会增加so文件的加载时间，使用前需评估其对应用性能和功能的影响。 > **说明：** > > loadNativeModule加载的模块名称为依赖方oh-package.json5文件的dependencies字段中声明的依赖名称。 > > loadNativeModule仅支持在Stage模型的UI主线程中加载native模块。 > > 无论moduleName参数使用常量字符串还是变量表达式，都需要配置接口调用的依赖。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare function loadNativeModule(moduleName: string): Object--><!--Device-unnamed-export declare function loadNativeModule(moduleName: string): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 加载的模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | native模块的默认导出，需使用ArkTS的ESObject类型去接收。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. |
| [10200301](../../apis-arkts/errorcode-utils.md#10200301-加载native模块失败) | Loading native module failed. |

