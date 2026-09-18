# off（系统接口）

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## off('wallpaperChange')

```TypeScript
function off(
    type: 'wallpaperChange',
    callback?: (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) => void
  ): void
```

取消订阅壁纸变化通知事件。不支持多线程并发调用。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wallpaperChange' | 是 | 事件回调类型。支持的事件为'wallpaperChange'，完成壁纸切换后触发该事件。 |
| callback | (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) =&gt; void | 否 | 表示要取消的壁纸变化回调，不填写该参数则取消订阅该type对应的所有回调。<br>- wallpaperType：壁纸类型。<br>- resourceType：壁纸资源类型。<br>- uri：壁纸资源地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |
