# UI组件适配（系统接口）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## UIExtensionComponent (系统接口)

### onResult

ArkTS-Dyn接口声明：[onResult(callback: Callback\<{code: number; want?: Want}>)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onresultdeprecated)

替代的ArkTS-Sta接口声明：[onTerminated(callback: Callback&lt;TerminationInfo&gt;)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onterminated12)



ArkTS-Dyn示例：

<!--code_no_check-->
```ts
UIExtensionComponent({
                bundleName: "com.example.newdemo",
                abilityName: "UIExtensionProvider",
                parameters: {
                  "ability.want.params.uiExtensionType": "sys/commonUI"
                }
})
.onResult((info) => {
    console.info('onResult: code =' + info.code + ', want = ' + JSON.stringify(info.want));
})
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
UIExtensionComponent({
                bundleName: "com.example.newdemo",
                abilityName: "UIExtensionProvider",
                parameters: {
                  "ability.want.params.uiExtensionType": "sys/commonUI"
                }
} as Record<String, Object>)
.onTerminated((info) => {
    console.info('onTerminated: code =' + info.code + ', want = ' + JSON.stringify(info.want));
})
```

### onRelease

ArkTS-Dyn接口声明：[onRelease(callback: Callback\<number>)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onreleasedeprecated)

替代的ArkTS-Sta接口声明：[onTerminated(callback: Callback&lt;TerminationInfo&gt;)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onterminated12)或者[onError(callback:ErrorCallback)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onerror)



ArkTS-Dyn示例：

<!--code_no_check-->
```ts
UIExtensionComponent({
                bundleName: "com.example.newdemo",
                abilityName: "UIExtensionProvider",
                parameters: {
                  "ability.want.params.uiExtensionType": "sys/commonUI"
                }
})
.onRelease((info) => {
    console.info('onRelease: releaseCode =' + JSON.stringify(info));
})
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
UIExtensionComponent({
                bundleName: "com.example.newdemo",
                abilityName: "UIExtensionProvider",
                parameters: {
                  "ability.want.params.uiExtensionType": "sys/commonUI"
                }
} as Record<String, Object>)
.onError((err) => {
    console.error('onError: code =' + err.code + ', name = ' + err.name + ', message = ' + err.message);
    console.error('onError: ' + JSON.stringify(err));
})
```

## AbilityComponent (系统接口)

### AbilityComponent

ArkTS-Dyn接口声明：[AbilityComponent(value: {want: Want})](../reference/apis-arkui/arkui-ts/ts-container-ability-component-sys.md#接口)

替代的ArkTS-Sta接口声明：[UIExtensionComponent(want: Want, options?: UIExtensionOptions)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#接口)



ArkTS-Dyn示例：

<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct MyComponent {

  build() {
      Column() {
          AbilityComponent({
              want: {
                  bundleName: '',
                  abilityName: ''
              },
          })
      }
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct MyComponent {
build() {
  Column() {
      UIExtensionComponent({
        bundleName: "com.example.newdemo",
        abilityName: "UIExtensionProvider",
        parameters: {
          "ability.want.params.uiExtensionType": "sys/commonUI"
        }
      })
    }
  }
}
```

### onConnect

ArkTS-Dyn接口声明：[onConnect(callback:()&nbsp;=&gt;&nbsp;void)](../reference/apis-arkui/arkui-ts/ts-container-ability-component-sys.md#onconnect)

替代的ArkTS-Sta接口声明：[onRemoteReady(callback: Callback\<UIExtensionProxy>)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onremoteready)



ArkTS-Dyn示例：

<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct MyComponent {

  build() {
      Column() {
          AbilityComponent({
              want: {
                  bundleName: '',
                  abilityName: ''
              },
          })
          .onConnect(() => {
              console.log('AbilityComponent connect')
          })
      }
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct MyComponent {
build() {
  Column() {
      UIExtensionComponent({
        bundleName: "com.example.newdemo",
        abilityName: "UIExtensionProvider",
        parameters: {
          "ability.want.params.uiExtensionType": "sys/commonUI"
        }
      } as Record<String, Object>)
      .onRemoteReady((proxy) => {
        console.info('onRemoteReady, for test');
      })
    }
  }
}
```

### onDisConnect

ArkTS-Dyn接口声明：[onDisConnect(callback:()&nbsp;=&gt;&nbsp;void)](../reference/apis-arkui/arkui-ts/ts-container-ability-component-sys.md#ondisconnect)

替代的ArkTS-Sta接口声明：[onTerminated(callback: Callback&lt;TerminationInfo&gt;)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onterminated12)或者[onError(callback:ErrorCallback)](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#onerror)



ArkTS-Dyn示例：

<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct MyComponent {

  build() {
      Column() {
          AbilityComponent({
              want: {
                  bundleName: '',
                  abilityName: ''
              },
          })
          .onDisconnect(() => {
              console.log('AbilityComponent disconnect')
          })
      }
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct MyComponent {
build() {
  Column() {
      UIExtensionComponent({
        bundleName: "com.example.newdemo",
        abilityName: "UIExtensionProvider",
        parameters: {
          "ability.want.params.uiExtensionType": "sys/commonUI"
        }
      } as Record<String, Object>)
      .onRelease((info) => {
        console.info('onRelease: releaseCode =' + JSON.stringify(info));
      })
    }
  }
}
```

## @system.app

### setImageCacheCount

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

### setImageRawDataCacheSize

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