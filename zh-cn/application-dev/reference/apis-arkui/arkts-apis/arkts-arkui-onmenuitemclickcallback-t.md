# OnMenuItemClickCallback

```TypeScript
export type OnMenuItemClickCallback = (menuItem: TextMenuItem, range: TextRange) => boolean
```

菜单项功能函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnMenuItemClickCallback = (menuItem: TextMenuItem, range: TextRange) => boolean--><!--Device-unnamed-export type OnMenuItemClickCallback = (menuItem: TextMenuItem, range: TextRange) => boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| menuItem | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 菜单项。\_\_\_HTML\_TAG\_USD\_0\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_1\_\_\_从API version 23开始，对于具备可展开二级菜单能力的一级菜单项，例如自动填充，仅执行系统默认逻辑，不会执行用 户自定义逻辑。  |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 选中的文本信息。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 菜单项的执行逻辑。\_\_\_HTML\_TAG\_USD\_0\_\_\_返回为true，拦截系统默认逻辑，仅执行自定义逻辑。\_\_\_HTML\_TAG\_USD\_1\_\_\_返回为false，先执行自定义逻辑，再执行系统逻辑。 |

