# NotificationContent
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

描述通知类型。

> **说明：**
>
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## NotificationContent

通知内容。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 类型                                                                        | 只读 | 可选 | 说明               |
| -----------   | --------------------------------------------------------------------------- | ---- | --- | ------------------ |
| contentType<sup>(deprecated)</sup> | [notification.ContentType](./js-apis-notification.md#contenttype)  | 否  | 是  | 通知内容类型。<br>从API version 11开始不再维护，建议使用notificationContentType代替。       |
| notificationContentType<sup>11+</sup>    | [notificationManager.ContentType](./js-apis-notificationManager.md#contenttype)                | 否  | 是  | 通知内容类型。       |
| normal         | [NotificationBasicContent](#notificationbasiccontent)                      | 否  | 是  | 基本类型通知内容。   |
| longText       | [NotificationLongTextContent](#notificationlongtextcontent)                | 否  | 是  | 长文本类型通知内容。 |
| multiLine      | [NotificationMultiLineContent](#notificationmultilinecontent)              | 否  | 是  | 多行类型通知内容。   |
| picture        | [NotificationPictureContent](#notificationpicturecontent)                  | 否  | 是  | 图片类型通知内容。   |
| systemLiveView<sup>11+</sup> | [NotificationSystemLiveViewContent](#notificationsystemliveviewcontent)    | 否  | 是  | 系统实况窗类型通知内容。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。|

## NotificationBasicContent

描述普通文本通知。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 类型    | 只读 | 可选 | 说明                               |
| -------------- | ------ | ---- |-----| ---------------------------------- |
| title          | string |  否  |  否  | 通知标题（不可为空字符串，大小不超过1024字节，超出部分会被截断）。         |
| text           | string |  否  |  否  | 通知内容（不可为空字符串，大小不超过3072字节，超出部分会被截断）。         |
| additionalText | string |  否  |  是  | 通知附加内容，是对通知内容的补充（大小不超过3072字节，超出部分会被截断）。   |
| lockscreenPicture<sup>12+</sup> | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) |  否  |  是  | 通知在锁屏界面显示的图片。当前仅支持实况窗类型通知。图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../apis-image-kit/arkts-apis-image-PixelMap.md#getpixelbytesnumber7)获取），建议图标像素长宽为128*128。实际显示效果依赖于设备能力和通知中心UI样式。   |
| structuredText<sup>21+</sup> | Map<string, string> |  否  |  是  | 通知结构化字段。当前仅支持服务提醒类短信在通知中心结构化展示。（key/value大小不超过512字节，超出部分会被截断，最多支持3对结构化数据，超出部分会被忽略。）   |

## NotificationLongTextContent

描述长文本通知。继承自[NotificationBasicContent](#notificationbasiccontent)。

> **说明：**
>
> 实际显示效果依赖于设备能力和通知中心UI样式。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 类型    | 只读 | 可选 | 说明                             |
| -------------- | ------ | ---- | --- | -------------------------------- |
| longText       | string |  否  | 否  | 通知的长文本（不可为空字符串，大小不超过3072字节，超出部分会被截断）。                     |
| briefText      | string |  否  | 否  | 通知概要内容，是对通知内容的总结（不可为空字符串，大小不超过1024字节，超出部分会被截断）。   |
| expandedTitle  | string |  否  | 否  | 通知展开时的标题（不可为空字符串，大小不超过1024字节，超出部分会被截断）。                 |


## NotificationMultiLineContent

描述多行文本通知。继承自[NotificationBasicContent](#notificationbasiccontent)。

> **说明：**
>
> - 当该类型通知与其他通知形成组通知时，该通知显示默认与[普通文本](#notificationbasiccontent)相同。展开组通知后，标题显示为展开时的标题`longTitle`，多行文本内容`lines`多行显示。<br>当该类型通知单独呈现时，该通知标题显示为展开时的标题`longTitle`，多行文本内容`lines`多行显示。
>
> - 实际显示效果依赖于设备能力和通知中心UI样式。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 类型            | 只读 | 可选 | 说明                             |
| -------------- | --------------- | --- | --- | -------------------------------- |
| briefText      | string          | 否  | 否  | 通知概要内容，是对通知内容的总结（不可为空字符串，大小不超过1024字节，超出部分会被截断）。 |
| longTitle      | string          | 否  | 否  | 通知展开时的标题（不可为空字符串，大小不超过1024字节，超出部分会被截断）。|
| lines          | Array\<string\> | 否  | 否  | 通知的多行文本（最多支持三行，每行大小不超过1024字节，超出部分会被截断）。                  |


## NotificationPictureContent

描述附有图片的通知。继承自[NotificationBasicContent](#notificationbasiccontent)。

> **说明：**
>
> 实际显示效果依赖于设备能力和通知中心UI样式。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 类型                                          | 只读 | 可选 | 说明                               |
| -------------- | -------------------------------------------- | ---- | --- |------------------------------------|
| briefText      | string                                       |  否  | 否  | 通知概要内容，是对通知内容的总结（不可为空字符串，大小不超过1024字节，超出部分会被截断）。 |
| expandedTitle  | string                                       |  否  | 否  | 通知展开时的标题（不可为空字符串，大小不超过1024字节，超出部分会被截断）。    |
| picture        | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) |  否  | 否  | 通知的图片内容(图像像素的总字节数不能超过2MB)。|


## NotificationSystemLiveViewContent

描述系统实况窗通知内容。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。继承自[NotificationBasicContent](#notificationbasiccontent)。

**系统能力**：SystemCapability.Notification.Notification

| 名称                         | 类型                                             | 只读| 可选 | 说明                               |
| ---------------------------- | ----------------------------------------------- | --- | --- | -----------------------------------|
| typeCode<sup>11+</sup>       | number                                          | 否  | 否  | 类型标识符，标记调用方业务类型。       |
| capsule<sup>11+</sup>        | [NotificationCapsule](#notificationcapsule11)   | 否  | 是  | 实况通知的胶囊。                     |
| button<sup>11+</sup>         | [NotificationButton](#notificationbutton11)     | 否  | 是  | 实况通知的按钮。                     |
| time<sup>11+</sup>           | [NotificationTime](#notificationtime11)         | 否  | 是  | 实况通知的时间。                     |
| progress<sup>11+</sup>       | [NotificationProgress](#notificationprogress11) | 否  | 是  | 实况内容的进度。                     |


## NotificationCapsule<sup>11+</sup>

描述通知胶囊。

**系统能力**：SystemCapability.Notification.Notification

| 名称            | 类型                                          | 只读 | 可选 | 说明                            |
| --------------- | -------------------------------------------- | --- | --- | -------------------------------- |
| title           | string                                       | 否  | 是  | 胶囊标题。大小不超过200字节，超出部分会被截断。                        |
| icon            | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 否  | 是  | 胶囊图片。                        |
| backgroundColor | string                                       | 否  | 是  | 背景颜色。                        |


## NotificationButton<sup>11+</sup>

描述通知按钮。

**系统能力**：SystemCapability.Notification.Notification

| 名称  | 类型                                                   | 只读 | 可选 | 说明             |
| ----- | ----------------------------------------------------- | --- | --- | ----------------- |
| names | Array\<string\>                                       | 否  |  是 | 按钮名称（最多支持3个）。   |
| icons | Array\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)\> | 否  |  是 | 按钮图片（最多支持3个）。   |
| iconsResource<sup>12+</sup> | Array\<[Resource](../apis-arkui/arkui-ts/ts-types.md#resource)\> | 否  |  是 | 按钮资源（最多支持3个）。   |

## NotificationTime<sup>11+</sup>

描述通知计时信息。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 类型              | 只读 | 可选 | 说明                             |
| -------------- | ---------------- | --- | --- | -------------------------------- |
| initialTime    | number           | 否  | 是  | 计时起始时间。单位：ms。                |
| isCountDown    | boolean          | 否  | 是  | 是否倒计时。默认为false。<br> - true：是。<br> - false：否。 |
| isPaused       | boolean          | 否  | 是  | 是否暂停。默认为false。<br> - true：是。<br> - false：否。   |
| isInTitle      | boolean          | 否  | 是  | 时间是否展示在title中。默认为false。<br> - true：是。<br> - false：否。|

**示例：**

<!--code_no_check-->
```ts
// 该通知从3秒开始倒计时，并且时间展示在title中。
time: {
    initialTime: 3000,
    isCountDown: true,
    isPaused: false,
    isInTitle: true,
}
```


## NotificationProgress<sup>11+</sup>

描述通知进度。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 类型            | 只读 | 可选 | 说明                             |
| -------------- | --------------- | --- | --- | -------------------------------- |
| maxValue        | number         | 否  | 是  | 进度最大值。                       |
| currentValue    | number         | 否  | 是  | 进度当前值。                       |
| isPercentage    | boolean        | 否  | 是  | 是否按百分比展示。默认为false。<br> - true：是。<br> - false：否。|
