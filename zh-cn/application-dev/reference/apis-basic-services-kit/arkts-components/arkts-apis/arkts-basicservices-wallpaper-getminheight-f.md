# getMinHeight

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## getMinHeight

```TypeScript
function getMinHeight(callback: AsyncCallback<number>): void
```

获取壁纸的最小高度值。使用callback异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取壁纸的最小高度值（单位为像素）成功，err为undefined，data为获取到的壁纸的最小高度值；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinHeight((error: BusinessError, data: number) => {
    if (error) {
        console.error(`Failed to getMinHeight. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to getMinHeight: ${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinHeight().then((data: number) => {
    console.info(`success to getMinHeight: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`Failed to getMinHeight. Code: ${error.code}, message: ${error.message}`);
});
```


## getMinHeight

```TypeScript
function getMinHeight(): Promise<number>
```

获取壁纸的最小高度值。使用Promise异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回壁纸的最小高度值，单位为像素。如果返回值等于0，说明没有设置壁纸，调用者应该使用默认显示的高度值代替。 |

**示例**

参见 [getMinHeight](#getminheight)
