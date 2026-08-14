# canIUse

## canIUse

```TypeScript
export declare function canIUse(syscap: string): boolean
```

查询系统是否具备某个系统能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare function canIUse(syscap: string): boolean--><!--Device-unnamed-export declare function canIUse(syscap: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| syscap | string | 是 | 待查询的系统能力名称。不支持输入null、undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 系统能力查询结果，true表示系统具备该能力，false表示系统不具备。 |

