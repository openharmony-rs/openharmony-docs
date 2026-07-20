# getMinHeight

<a id="getminheight"></a>
## getMinHeight

```TypeScript
function getMinHeight(callback: AsyncCallback<number>): void
```

获取壁纸的最小高度值。

**起始版本：** 7

**废弃版本：** 9

<!--Device-wallpaper-function getMinHeight(callback: AsyncCallback<number>): void--><!--Device-wallpaper-function getMinHeight(callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinHeight((error: BusinessError, data: Number) => {
    if (error) {
        console.error(`failed to getMinHeight because: ${JSON.stringify(error)}`);
        return;
    }
    console.info(`success to getMinHeight: ${JSON.stringify(data)}`);
});

```


<a id="getminheight-1"></a>
## getMinHeight

```TypeScript
function getMinHeight(): Promise<number>
```

获取壁纸的最小高度值。

**起始版本：** 7

**废弃版本：** 9

<!--Device-wallpaper-function getMinHeight(): Promise<number>--><!--Device-wallpaper-function getMinHeight(): Promise<number>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 返回壁纸的最小高度值，单位是像素。如果返回值等于0，说明没有设置壁纸，调用者应该使用默认显示的高度值代替。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinHeight().then((data: Number) => {
    console.info(`success to getMinHeight: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`failed to getMinHeight because: ${JSON.stringify(error)}`);
});

```

