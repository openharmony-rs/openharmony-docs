# @system.app

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## setImageCacheCount

ArkTS-Dyn接口声明：[static setImageCacheCount(value: number): void](../reference/apis-arkui/js-apis-system-app.md#setimagecachecount7)

替代的ArkTS-Sta接口声明：[setImageCacheCount(value: int): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#setimagecachecount22)

ArkTS-Dyn示例：

```typescript
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

ArkTS-Sta示例：

```typescript
'use static'
// xxx.ets
import { Entry, Column, Row, Component, Image } from '@ohos.arkui.component';
@Entry
@Component
struct Index {
  onPageShow() {
    // 设置解码后图片内存缓存上限为100张
    this.getUIContext().setImageCacheCount(100);
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      Image('https://www.example.com/xxx.png') // 请填写一个具体的网络图片地址
        .width(200)
        .height(50)
    }.width('100%')
  }
}
```

## setImageRawDataCacheSize

ArkTS-Dyn接口声明：[static setImageRawDataCacheSize(value: number): void](../reference/apis-arkui/js-apis-system-app.md#setimagerawdatacachesize7)

替代的ArkTS-Sta接口声明：[setImageRawDataCacheSize(value: int): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#setimagerawdatacachesize22)

ArkTS-Dyn示例：

```typescript
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

ArkTS-Sta示例：

```typescript
'use static'
// xxx.ets
import { Entry, Column, Row, Component, Image } from '@ohos.arkui.component';
@Entry
@Component
struct Index {
  onPageShow() {
    // 设置解码前图片数据内存缓存上限为100MB (100MB=100*1024*1024B=104857600B)
    this.getUIContext().setImageRawDataCacheSize(104857600); 
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      Image('https://www.example.com/xxx.png') // 请填写一个具体的网络图片地址
        .width(200)
        .height(50)
    }.width('100%')
  }
}
```