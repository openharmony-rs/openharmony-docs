# off_streamChange（系统接口）

## off_streamChange

```TypeScript
function off(type: 'streamChange', callback?: Callback<number>): void
```

取消订阅WLAN数据流改变事件。 &lt;p&gt;如果没有指定callback参数，将取消注册该事件关联的所有回调函数。&lt;/p&gt;

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** streamChange

**需要权限：** ohos.permission.MANAGE_WIFI_CONNECTION

<!--Device-wifi-function off(type: 'streamChange', callback?: Callback<number>): void--><!--Device-wifi-function off(type: 'streamChange', callback?: Callback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 否 | 状态改变回调函数。1:向下，2:向上，3:双向 |

