# offReadingScreenPermissionListener（系统接口）

## offReadingScreenPermissionListener

```TypeScript
function offReadingScreenPermissionListener(callback?: Callback<ReadingScreenPermissionStatus>): void
```

关闭屏幕内容访问权限监测。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_SCREEN_CONTENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-onScreen-function offReadingScreenPermissionListener(callback?: Callback<ReadingScreenPermissionStatus>): void--><!--Device-onScreen-function offReadingScreenPermissionListener(callback?: Callback<ReadingScreenPermissionStatus>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ReadingScreenPermissionStatus](arkts-multimodalawareness-onscreen-readingscreenpermissionstatus-i-sys.md)&gt; | 否 | 回调函数。需要取消监听的回调函数，需与订阅时传入的回调函数一致。若不填，则取消当前监听该事件的所有回调 函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [34000001](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000001-服务异常) | Service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to get page content forbidden by &lt;br&gt; permission: ohos.permission.GET_SCREEN_CONTENT. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A nonsystem application uses the system API. |

## 示例

```TypeScript
import onScreen from "@ohos.multimodalAwareness.onScreen";
try {
  onScreen.offReadingScreenPermissionListener();
  console.info(`offReadingScreenPermissionListener succeeded.`);
} catch (err) {
  console.error('offReadingScreenPermissionListener failed, errCode = ' + err.code);
}
```

