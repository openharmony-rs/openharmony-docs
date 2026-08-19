# isRequestPublishFormSupported（系统接口）

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## isRequestPublishFormSupported

```TypeScript
function isRequestPublishFormSupported(callback: AsyncCallback<boolean>): void
```

查询是否可以发布卡片到卡片使用方，使用callback异步回调。

**起始版本：** 23

<!--Device-formProvider-function isRequestPublishFormSupported(callback: AsyncCallback<boolean>): void--><!--Device-formProvider-function isRequestPublishFormSupported(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 返回查询结果的回调函数。 <br>true: 表示可以发布卡片到卡片使用方。 <br>false: 表示不可以发布卡片到卡片使用方。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |


## isRequestPublishFormSupported

```TypeScript
function isRequestPublishFormSupported(): Promise<boolean>
```

查询是否可以发布卡片到卡片使用方，使用Promise异步回调。

**起始版本：** 23

<!--Device-formProvider-function isRequestPublishFormSupported(): Promise<boolean>--><!--Device-formProvider-function isRequestPublishFormSupported(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回是否可以发布卡片到卡片使用方的结果。 <br>true: 表示可以发布卡片到卡片使用方。 <br>false: 表示不可以发布卡片到卡片使用方。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

