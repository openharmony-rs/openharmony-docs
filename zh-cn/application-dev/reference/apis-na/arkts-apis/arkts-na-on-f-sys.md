# on（系统接口）

## on('wallpaperChange')

```TypeScript
function on(
    type: 'wallpaperChange',
    callback: (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) => void
  ): void
```

订阅壁纸变化通知事件。不支持多线程并发调用。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'wallpaperChange' | 是 | 事件回调类型。支持的事件为'wallpaperChange'，完成壁纸切换后触发该事件。 |
| callback | (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) =&gt; void | 是 | 壁纸变化触发该回调方法，返回壁纸类型和壁纸资源类型。<br/>- wallpaperType：壁纸类型。<br/>- resourceType：壁纸资源类型。<br/>- uri：壁纸资源地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application usessystem API. |

**示例：**

```TypeScript
try {
    let listener = (wallpaperType: wallpaper.WallpaperType, resourceType: wallpaper.WallpaperResourceType): void => {
        console.info(`wallpaper color changed.`);
    };
    wallpaper.on('wallpaperChange', listener);
} catch (error) {
    console.error(`failed to on. Code: ${error.code}, Message: ${error.message}`);
}

```

