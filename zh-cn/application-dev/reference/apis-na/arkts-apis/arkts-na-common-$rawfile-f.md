# $rawfile

## $rawfile

```TypeScript
export declare function $rawfile(value: string): Resource
```

global \$rawfile function

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function $rawfile(value: string): Resource--><!--Device-unnamed-export declare function $rawfile(value: string): Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | name of the file in the resources/rawfile directory of the project. When referencing resources of the Resource type, make sure the data type is the same as that of the attribute method. For example, if an attribute method supports the string \| Resource types, the data type of the Resource type must be string. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) |  |

