# loadNativeModule

## loadNativeModule

```TypeScript
export declare function loadNativeModule(moduleName: string): Object
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | Indicates the native module name. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | Returns the default export from the native module. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The parameter check failed. |
| [10200301](../../errorcode-universal.md#10200301-Loading) | Loading native module failed. |

