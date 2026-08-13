# getSessionDescriptors（系统接口）

## getSessionDescriptors

```TypeScript
function getSessionDescriptors(category: SessionCategory): Promise<Array<Readonly<AVSessionDescriptor>>>
```

根据不同的会话类别获取对应的会话描述。使用Promise异步回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getSessionDescriptors(category: SessionCategory): Promise<Array<Readonly<AVSessionDescriptor>>>--><!--Device-avSession-function getSessionDescriptors(category: SessionCategory): Promise<Array<Readonly<AVSessionDescriptor>>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| category | [SessionCategory](arkts-avsession-avsession-sessioncategory-e-sys.md) | 是 | 指定会话的类别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Readonly&lt;[AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i-sys.md)&gt;&gt;&gt; | Promise对象。返回对应类别的会话描述的只读对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

