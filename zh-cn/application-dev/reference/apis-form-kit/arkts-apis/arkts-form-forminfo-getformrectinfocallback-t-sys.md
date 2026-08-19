# GetFormRectInfoCallback（系统接口）

```TypeScript
type GetFormRectInfoCallback = (formId: string) => Promise<formInfo.Rect>
```

卡片位置、尺寸查询回调。使用Promise异步回调。

**起始版本：** 23

<!--Device-formInfo-type GetFormRectInfoCallback = (formId: string) => Promise<formInfo.Rect>--><!--Device-formInfo-type GetFormRectInfoCallback = (formId: string) => Promise<formInfo.Rect>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[formInfo.Rect](arkts-form-forminfo-rect-i.md)&gt; | Promise对象，返回卡片相对屏幕左上角的位置信息和卡片尺寸信息。 |

