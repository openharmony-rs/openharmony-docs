# loadNativeModule

## loadNativeModule

```TypeScript
export declare function loadNativeModule(moduleName: string): Object
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |
| [10200301](../../apis-arkts/errorcode-utils.md#10200301-加载native模块失败) | Loading native module failed. |

