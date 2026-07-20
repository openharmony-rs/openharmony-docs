# getMinWidthSync（系统接口）

<a id="getminwidthsync"></a>
## getMinWidthSync

```TypeScript
function getMinWidthSync(): number
```

获取壁纸的最小宽度值。

**起始版本：** 9

<!--Device-wallpaper-function getMinWidthSync(): int--><!--Device-wallpaper-function getMinWidthSync(): int-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 壁纸的最小宽度值，单位是像素。如果返回值等于0，说明没有设置壁纸，调用者应该使用默认显示的宽度值代替。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
try {
  let minWidth = wallpaper.getMinWidthSync();
  console.info(`success to getMinWidthSync: ${JSON.stringify(minWidth)}`);
} catch (error) {
  console.error(`failed to getMinWidthSync. Code: ${error.code}, Message: ${error.message}`);
}

```

