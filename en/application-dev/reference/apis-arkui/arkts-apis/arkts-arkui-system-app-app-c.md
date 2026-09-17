# App

Defines static functions of App class

**Since:** 3

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## Modules to Import

```TypeScript
import { App, AppResponse, RequestFullWindowOptions, ScreenOnVisibleOptions } from '@kit.ArkUI';
```

## getInfo

```TypeScript
static getInfo(): AppResponse
```

Obtains the declared information in the **config.json** file of an application. In the stage model, this API returns **null**.

This API is deprecated since API version 9. You are advised to use [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md) instead.

**Since:** 3

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Return value:**

| Type | Description |
| --- | --- |
| [AppResponse](arkts-arkui-system-app-appresponse-i.md) | Application response information. |

**Examples**

```TypeScript
ArkTS example:
```

```TypeScript
JS example:
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

Requests the application to run in full window. In some scenarios, such as semi-modal FA, the FA runs in non-full window. In this case, you can call this API. This API is invalid for an application already in full-window mode.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** startAbility

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RequestFullWindowOptions](arkts-arkui-system-app-requestfullwindowoptions-i.md) | No | Transition time from non-full window to full window, in milliseconds. By default, the value is in direct proportion to the distance between the non-full window and the full window. |

**Examples**

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

Defines whether to keep the application visible when the screen is woken up.

This API is deprecated since API version 8.

**Since:** 3

**Deprecated since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ScreenOnVisibleOptions](arkts-arkui-system-app-screenonvisibleoptions-i.md) | No | With keep-alive, the system is prevented from returning to the home screen when the screen is locked, so that the application is visible when the screen is woken up. |

## setImageCacheCount

```TypeScript
static setImageCacheCount(value: number): void
```

Set image cache capacity of decoded image count. if not set, the application will not cache any decoded image.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | capacity of decoded image count. |

**Examples**

```TypeScript
// xxx.ets
import app, { AppResponse } from '@system.app';

@Entry
@Component
struct Index {
  onPageShow() {
    // Set the maximum number of decoded images that can be cached in the memory to 100.
    app.setImageCacheCount(100);
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      // xxxxxxxxxxxxx indicates the image address.
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

Set image file cache size in bytes on disk before decode. if not set, the application will cache 100MB image files on disk.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | capacity of raw image data size in bytes. |

**Examples**

```TypeScript
// app.ets
import app, { AppResponse } from '@system.app';

export default class OnC {
  onCreate() {
    app.setImageFileCacheSize(209715200);
    // Set the upper limit of the image file cache to 200 MB. (200 × 1024 × 1024 B= 209715200 B = 200 MB).
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

Set image cache capacity of raw image data size in bytes before decode. if not set, the application will not cache any raw image data.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | capacity of raw image data size in bytes. |

**Examples**

```TypeScript
// xxx.ets
import app, { AppResponse } from '@system.app';

@Entry
@Component
struct Index {
  onPageShow() {
    // Set the upper limit of the memory for caching image data before decoding to 100 MB. (100 × 1024 × 1024 B =104857600 B = 100 MB).
    app.setImageRawDataCacheSize(104857600); 
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      // xxxxxxxxxxxxx indicates the image address.
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

Terminates the current ability. In the stage model, this API has no effect.

This API is deprecated since API version 7. You are advised to use [@ohos.ability.featureAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-featureability.md) instead.

**Since:** 3

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Examples**

```TypeScript
ArkTS example:
```

```TypeScript
JS example:
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
