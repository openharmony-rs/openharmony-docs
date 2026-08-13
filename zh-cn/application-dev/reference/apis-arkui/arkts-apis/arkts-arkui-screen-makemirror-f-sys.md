# makeMirror（系统接口）

## makeMirror

```TypeScript
function makeMirror(mainScreen:long, mirrorScreen:Array<long>, callback: AsyncCallback<long>): void
```

将屏幕设置为镜像模式，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-screen-function makeMirror(mainScreen:long, mirrorScreen:Array<long>, callback: AsyncCallback<long>): void--><!--Device-screen-function makeMirror(mainScreen:long, mirrorScreen:Array<long>, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreen | long | 是 | 主屏幕ID，该参数仅支持整数输入。 |
| mirrorScreen | Array&lt;long&gt; | 是 | 镜像屏幕ID集合，其中ID应为整数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数。返回镜像屏幕的群组id，其中id为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let mainScreenId: number = 0; // 主屏ID
let mirrorScreenIds: Array<number> = [1, 2, 3]; // 镜像屏ID集合
// 设置屏幕为镜像模式
screen.makeMirror(mainScreenId, mirrorScreenIds, (err: BusinessError, data: number) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set screen mirroring. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: long = 0;
let mirrorScreenIds: Array<long> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds, (err: BusinessError | null, data: long | undefined) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to set screen mirroring. Code: ${err?.code}, message: ${err?.message}`);
    return;
  }
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
});
```


## makeMirror

```TypeScript
function makeMirror(mainScreen:long, mirrorScreen:Array<long>): Promise<long>
```

将屏幕设置为镜像模式，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-screen-function makeMirror(mainScreen:long, mirrorScreen:Array<long>): Promise<long>--><!--Device-screen-function makeMirror(mainScreen:long, mirrorScreen:Array<long>): Promise<long>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreen | long | 是 | 主屏幕ID，该参数仅支持整数输入。 |
| mirrorScreen | Array&lt;long&gt; | 是 | 镜像屏幕ID集合。其中ID应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象。返回镜像屏幕的群组id，其中id为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let mainScreenId: number = 0; // 主屏ID
let mirrorScreenIds: Array<number> = [1, 2, 3]; // 镜像屏ID集合
// 设置屏幕为镜像模式
screen.makeMirror(mainScreenId, mirrorScreenIds).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen mirroring. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: long = 0;
let mirrorScreenIds: Array<long> = [1, 2, 3];
screen.makeMirror(mainScreenId, mirrorScreenIds).then((data: long) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: Error) => {
  console.error(`Failed to set screen mirroring. Code: ${err?.code}, message: ${err?.message}`);
});
```

