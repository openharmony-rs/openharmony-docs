# getMinHeightSync（系统接口）

## getMinHeightSync

```TypeScript
function getMinHeightSync(): number
```

获取壁纸的最小高度值。

**起始版本：** 9

<!--Device-wallpaper-function getMinHeightSync(): int--><!--Device-wallpaper-function getMinHeightSync(): int-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回壁纸的最小高度值，单位是像素。如果返回值等于0，说明没有设置壁纸，调用者应该使用默认显示的高度值代替。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
try {
  let minHeight = wallpaper.getMinHeightSync();
  console.info(`success to getMinHeightSync: ${JSON.stringify(minHeight)}`);
} catch (error) {
  console.error(`failed to getMinHeightSync. Code: ${error.code}, Message: ${error.message}`);
}

```

