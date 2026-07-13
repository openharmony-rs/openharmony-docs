# App

定义App类的静态函数

**起始版本：** 3

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## getInfo

```TypeScript
static getInfo(): AppResponse
```

获取当前应用配置文件中声明的信息。在Stage模型下接口返回值为null。

从API version9开始，推荐使用
[bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)
。

**起始版本：** 3

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AppResponse | 定义AppResponse信息。 |

**示例：**

ArkTS示例：

```TypeScript
import app, { AppResponse } from '@system.app';
export default class Info {
  getInfo() {
    let info:AppResponse = app.getInfo();
    console.info(JSON.stringify(info));
  }
}

```

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        app.getInfo example
    </text>
    <div class="info-item">
        <text class="label">appName:</text>
        <text class="value">{{appName}}</text>
    </div>
    <div class="info-item">
        <text class="label">versionName:</text>
        <text class="value">{{versionName}}</text>
    </div>
    <div class="info-item">
        <text class="label">versionCode:</text>
        <text class="value">{{versionCode}}</text>
    </div>
    <input type="button" value="getAppInfo" style="width: 240px; height: 50px; margin: 5px;" onclick="getAppInfo"></input>
</div>

```

```TypeScript
/* xxx.css */
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    left: 0px;
    top: 0px;
    width: 454px;
    height: 454px;
    background-color: #000000;
}
.title {
    font-size: 32px;
    text-align: center;
    width: 400px;
    height: 80px;
    margin-top: 20px;
    color: #ffffff;
}
.info-item {
    width: 400px;
    height: 60px;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-top: 10px;
    padding-left: 20px;
    padding-right: 20px;
    background-color: #1a1a1a;
    border-radius: 10px;
}
.label {
    font-size: 24px;
    color: #aaaaaa;
}
.value {
    font-size: 24px;
    color: #ffffff;
}

```

```TypeScript
// xxx.js
import app from '@system.app';

export default {
    data: {
        fontSize: '32px',
        fontColor: '#ffffff',
        appName: '',
        versionName: '',
        versionCode: ''
    },
    onInit() {
        this.getAppInfo();
    },
    getAppInfo() {
        try {
            const info = app.getInfo();
            console.info('app.getInfo success');
            console.info('appName: ' + info.appName);
            console.info('versionName: ' + info.versionName);
            console.info('versionCode: ' + info.versionCode);
            this.appName = info.appName || 'Unknown';
            this.versionName = info.versionName || 'Unknown';
            this.versionCode = String(info.versionCode) || 'Unknown';
        } catch (error) {
            console.error('app.getInfo failed: ' + error.message);
            this.appName = 'Failed';
            this.versionName = 'Failed';
            this.versionCode = 'Failed';
        }
    }
}

```

## requestFullWindow

```TypeScript
static requestFullWindow(options?: RequestFullWindowOptions): void
```

Requests the application to run in full window.
In some scenarios, such as semi-modal FA, the FA runs in non-full window.
In this case, you can call this API.
This API is invalid for an application already in full-window mode.

**起始版本：** 3

**废弃版本：** 8

**替代接口：** startAbility

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RequestFullWindowOptions | 否 | Transition time from non-full window to full window, in milliseconds. |

**示例：**

```TypeScript
import app, { AppResponse } from '@system.app';
export default class Req {
  requestFullWindow() {
    app.requestFullWindow({
      duration: 200
    });
  }
} 

```

## screenOnVisible

```TypeScript
static screenOnVisible(options?: ScreenOnVisibleOptions): void
```

定义屏幕唤醒时是否保持应用可见。

该接口从API version 8 开始废弃。

**起始版本：** 3

**废弃版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ScreenOnVisibleOptions | 否 | 当启动保活时，锁屏时将阻止系统返回桌面显示，以保持屏幕唤醒时应用可见。 |

## setImageCacheCount

```TypeScript
static setImageCacheCount(value: number): void
```

Set image cache capacity of decoded image count.
if not set, the application will not cache any decoded image.

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | capacity of decoded image count. |

**示例：**

```TypeScript
// xxx.ets
import app, { AppResponse } from '@system.app';

@Entry
@Component
struct Index {
  onPageShow() {
    // 设置解码后图片内存缓存上限为100张
    app.setImageCacheCount(100);
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      // xxxxxxxxxxxxx为图片地址
      Image('xxxxxxxxxxxxx')
        .width(200)
        .height(50)
    }.width('100%')
  }
}

```

## setImageFileCacheSize

```TypeScript
static setImageFileCacheSize(value: number): void
```

设置图像文件在解码前在磁盘上的缓存大小（字节）。

如果未设置，应用程序将在磁盘上缓存 100MB 的图像文件。

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 原始图像数据大小的容量，单位为字节。 |

**示例：**

```TypeScript
// app.ets
import app, { AppResponse } from '@system.app';

export default class OnC {
  onCreate() {
    app.setImageFileCacheSize(209715200);
    // 设置图片文件数据缓存上限为200MB (200MB=200*1024*1024B=209715200B) 
    console.info('Application onCreate');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }
}

```

## setImageRawDataCacheSize

```TypeScript
static setImageRawDataCacheSize(value: number): void
```

Set image cache capacity of raw image data size in bytes before decode.
if not set, the application will not cache any raw image data.

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | capacity of raw image data size in bytes. |

**示例：**

```TypeScript
// xxx.ets
import app, { AppResponse } from '@system.app';

@Entry
@Component
struct Index {
  onPageShow() {
    // 设置解码前图片数据内存缓存上限为100MB (100MB=100*1024*1024B=104857600B)
    app.setImageRawDataCacheSize(104857600); 
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      // xxxxxxxxxxxxx为图片地址
      Image('xxxxxxxxxxxxx')
        .width(200)
        .height(50)
    }.width('100%')
  }
}

```

## terminate

```TypeScript
static terminate(): void
```

退出当前Ability。在Stage模型下接口功能不生效。

从API version 7开始，推荐使用[`@ohos.ability.featureAbility`](../../apis-ability-kit/arkts-apis/arkts-ability-featureability.md)。

**起始版本：** 3

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**示例：**

ArkTS示例：

```TypeScript
import app, { AppResponse } from '@system.app';
export default class TerM {
  terminate() {
    app.terminate();
  }
}

```

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        app.terminate example
    </text>
    <text class="desc">
        Click the button below to exit the app
    </text>
    <input type="button" value="exit app" style="width: 240px; height: 50px; margin: 5px;" onclick="terminateApp"></input>
</div>

```

```TypeScript
/* xxx.css */
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    left: 0px;
    top: 0px;
    width: 454px;
    height: 454px;
    background-color: #000000;
}
.title {
    font-size: 32px;
    text-align: center;
    width: 400px;
    height: 80px;
    margin-top: 60px;
    color: #ffffff;
}
.desc {
    font-size: 24px;
    text-align: center;
    width: 290px;
    height: 120px;
    margin-top: 20px;
    color: #aaaaaa;
}

```

```TypeScript
// xxx.js
import app from '@system.app';

export default {
    data: {
        fontSize: '32px',
        fontColor: '#ffffff'
    },
    terminateApp() {
        console.info('Calling app.terminate...');
        try {
            app.terminate();
            console.info('app.terminate called');
        } catch (error) {
            console.error('app.terminate failed: ' + error.message);
        }
    }
}

```

