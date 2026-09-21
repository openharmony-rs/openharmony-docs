# isOperationAllowed

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## isOperationAllowed

```TypeScript
function isOperationAllowed(callback: AsyncCallback<boolean>): void
```

是否允许用户设置壁纸。使用callback异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示允许用户设置壁纸；返回false表示不允许。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isOperationAllowed((error: BusinessError, data: boolean) => {
    if (error) {
        console.error(`Failed to isOperationAllowed. Code: ${error.code}, message: ${error.message}`);
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

是否允许用户设置壁纸。使用Promise异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示允许用户设置壁纸；返回false表示不允许。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isOperationAllowed().then((data: boolean) => {
    console.info(`success to isOperationAllowed: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to isOperationAllowed. Code: ${error.code}, message: ${error.message}`);
});
```
