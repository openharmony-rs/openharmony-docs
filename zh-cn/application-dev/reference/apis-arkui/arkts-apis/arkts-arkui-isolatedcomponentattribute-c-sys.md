# IsolatedComponentAttribute（系统接口）

定义IsolatedComponent的属性方法。

**继承/实现关系：** IsolatedComponentAttribute extends [CommonMethod<IsolatedComponentAttribute>](CommonMethod<IsolatedComponentAttribute>)

**起始版本：** 12

<!--Device-unnamed-declare class IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>--><!--Device-unnamed-declare class IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

<a id="onerror"></a>
## onError

```TypeScript
onError(
    callback: ErrorCallback
  ): IsolatedComponentAttribute
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IsolatedComponentAttribute-onError(
    callback: ErrorCallback
  ): IsolatedComponentAttribute--><!--Device-IsolatedComponentAttribute-onError(
    callback: ErrorCallback
  ): IsolatedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 当发生除与IsolatedAbility断开连接之外的错误时回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IsolatedComponentAttribute](arkts-arkui-isolatedcomponentattribute-c-sys.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@systemapi@stagemodelonly |

