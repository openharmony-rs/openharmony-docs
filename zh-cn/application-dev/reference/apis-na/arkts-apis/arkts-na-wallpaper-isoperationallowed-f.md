# isOperationAllowed

<a id="isoperationallowed"></a>
## isOperationAllowed

```TypeScript
function isOperationAllowed(callback: AsyncCallback<boolean>): void
```

是否允许用户设置壁纸。

**起始版本：** 7

**废弃版本：** 9

<!--Device-wallpaper-function isOperationAllowed(callback: AsyncCallback<boolean>): void--><!--Device-wallpaper-function isOperationAllowed(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isOperationAllowed((error: BusinessError, data: Boolean) => {
    if (error) {
        console.error(`failed to isOperationAllowed because: ${JSON.stringify(error)}`);
        return;
    }
    console.info(`success to isOperationAllowed: ${JSON.stringify(data)}`);
});

```


<a id="isoperationallowed-1"></a>
## isOperationAllowed

```TypeScript
function isOperationAllowed(): Promise<boolean>
```

是否允许用户设置壁纸。

**起始版本：** 7

**废弃版本：** 9

<!--Device-wallpaper-function isOperationAllowed(): Promise<boolean>--><!--Device-wallpaper-function isOperationAllowed(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 异步回调函数，返回是否允许用户设置壁纸。如果允许返回true，否则返回false。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isOperationAllowed().then((data: Boolean) => {
    console.info(`success to isOperationAllowed: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`failed to isOperationAllowed because: ${JSON.stringify(error)}`);
});

```

