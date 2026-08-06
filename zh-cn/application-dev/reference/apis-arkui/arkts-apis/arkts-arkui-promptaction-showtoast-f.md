# showToast

## showToast

```TypeScript
function showToast(options: ShowToastOptions): void
```

Creates and displays a toast. 创建并显示即时反馈。 > **说明：** > > - 从API version 9开始支持，从API version 18开始废弃，建议使用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_替代。 showToast需先通过\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中的 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_方法获取\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_对象， 然后通过该对象进行调用。且直接使用showToast可能导致\_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_的问题。 > > - 从API version 10开始，可以通过使用\_\_\_MD\_LINK\_DESC\_USD\_5\_\_\_中的 \_\_\_MD\_LINK\_DESC\_USD\_6\_\_\_方法获取当前UI上下文关联的 \_\_\_MD\_LINK\_DESC\_USD\_7\_\_\_对象。 > > - Toast样式单一，不支持内容的自定义，具体支持能力请参考\_\_\_MD\_LINK\_DESC\_USD\_8\_\_\_提供的接口。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 18

**替代接口：** ohos.arkui.UIContext.PromptAction#showToast

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-promptAction-function showToast(options: ShowToastOptions): void--><!--Device-promptAction-function showToast(options: ShowToastOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Toast选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameters types.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

