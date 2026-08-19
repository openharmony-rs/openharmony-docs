# openToast

## 导入模块

```TypeScript
```

## openToast

```TypeScript
export function openToast(options: ShowToastOptions): Promise<int>
```

显示即时反馈并通过Promise返回其id。 > **说明：** > > - 不支持在输入法类型窗口中使用子窗（showMode设置为TOP_MOST或者SYSTEM_TOP_MOST）的openToast，详情见输入法框架的约束与限制说明 > [createPanel](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-inputmethodability-i.md#createpanel) > 。 > > - 直接使用openToast可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用UIContext中的 > getPromptAction方法获取到PromptAction对象，再通过该对象调用 > [openToast](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opentoast18)实现。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-promptAction-export function openToast(options: ShowToastOptions): Promise<int>--><!--Device-promptAction-export function openToast(options: ShowToastOptions): Promise<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ShowToastOptions | 是 | Toast选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 返回即时反馈的id，可供closeToast使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

