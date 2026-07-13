# FillRequestCallback（系统接口）

自动填充或者生成密码时的回调对象，可以通过此回调通知客户端成功或者失败。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## onCancel

```TypeScript
onCancel(fillContent?: string): void
```

通知自动填充已被取消。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillContent | string | 否 | 表示通知自动填充取消后，返回给输入法框架的填充内容。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.The input parameter is not valid parameter;<br>2. Mandatory parameters are left unspecified.<br>**适用版本：** 12+ |

## onFailure

```TypeScript
onFailure(): void
```

通知自动填充请求已失败。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## onSuccess

```TypeScript
onSuccess(response: FillResponse): void
```

通知自动填充请求已成功完成。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | FillResponse | 是 | 自动填充响应信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Mandatory parameters are left unspecified. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## setAutoFillPopupConfig

```TypeScript
setAutoFillPopupConfig(autoFillPopupConfig: AutoFillPopupConfig): void
```

动态调整气泡弹窗的尺寸和位置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| autoFillPopupConfig | AutoFillPopupConfig | 是 | 气泡弹窗尺寸和位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Mandatory parameters are left unspecified. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

