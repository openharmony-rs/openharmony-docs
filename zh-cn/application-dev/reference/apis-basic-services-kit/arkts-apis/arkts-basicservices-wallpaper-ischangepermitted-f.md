# isChangePermitted

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## isChangePermitted

```TypeScript
function isChangePermitted(callback: AsyncCallback<boolean>): void
```

是否允许应用改变当前用户的壁纸。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isChangePermitted((error: BusinessError, data: boolean) => {
    if (error) {
        console.error(`Failed to isChangePermitted. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to isChangePermitted: ${JSON.stringify(data)}`);
});
```


## isChangePermitted

```TypeScript
function isChangePermitted(): Promise<boolean>
```

是否允许应用改变当前用户的壁纸。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;boolean&gt; | 返回是否允许应用改变当前用户的壁纸。如果允许返回true，否则返回false。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isChangePermitted().then((data: boolean) => {
    console.info(`success to isChangePermitted: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`Failed to isChangePermitted. Code: ${error.code}, message: ${error.message}`);
});
```
