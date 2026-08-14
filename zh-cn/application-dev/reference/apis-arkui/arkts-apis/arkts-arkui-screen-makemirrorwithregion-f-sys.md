# makeMirrorWithRegion（系统接口）

## makeMirrorWithRegion

```TypeScript
function makeMirrorWithRegion(mainScreen: long, mirrorScreen: Array<long>, mainScreenRegion: Rect): Promise<long>
```

将屏幕的某一矩形区域设置为镜像模式，使用Promise异步回调。调用该接口后，不建议再进行屏幕的旋转/折叠，否则可能导致镜像内容异常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-screen-function makeMirrorWithRegion(mainScreen: long, mirrorScreen: Array<long>, mainScreenRegion: Rect): Promise<long>--><!--Device-screen-function makeMirrorWithRegion(mainScreen: long, mirrorScreen: Array<long>, mainScreenRegion: Rect): Promise<long>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainScreen | long | 是 | 主屏幕ID，该参数仅支持正整数输入。 |
| mirrorScreen | Array&lt;long&gt; | 是 | 镜像屏幕ID集合。其中ID应为正整数。 |
| mainScreenRegion | Rect | 是 | 主屏创建镜像的矩形区域。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象。返回镜像屏幕的群组id，其中id为正整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let mainScreenId: number = 0; // 主屏ID
let mirrorScreenIds: Array<number> = [1, 2, 3]; // 镜像屏ID集合
// 主屏创建镜像的矩形区域
let mainScreenRegion: screen.Rect = {
  left: 0,
  top: 0,
  width: 1920,
  height: 1080
};
// 将屏幕的某一矩形区域设置为镜像模式
screen.makeMirrorWithRegion(mainScreenId, mirrorScreenIds, mainScreenRegion).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen area mirroring. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let mainScreenId: long = 0;
let mirrorScreenIds: Array<long> = [1, 2, 3];
let mainScreenRegion: screen.Rect = {
  left : 0,
  top : 0,
  width : 1920,
  height : 1080
};
screen.makeMirrorWithRegion(mainScreenId, mirrorScreenIds, mainScreenRegion).then((data: long) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: Error) => {
  console.error(`Failed to set screen area mirroring. Code: ${err?.code}, message: ${err?.message}`);
});
```

