# @ohos.arkui.drawableDescriptor (DrawableDescriptor)

本模块提供获取pixelMap的能力，包括前景、背景、蒙版和分层图标。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> 本模块同时支持ArkTs-Dyn、ArkTs-Sta。
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## 导入模块

```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';
```

## DrawableDescriptor

支持传入png、jpg、bmp、svg、gif、webp、astc、sut格式的资源类型。

### getPixelMap

getPixelMap(): image.PixelMap

获取pixelMap。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                       | 说明       |
| ---------------------------------------- | -------- |
| [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | PixelMap |

**示例：**
  ```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI'
let resManager = this.getUIContext().getHostContext()?.resourceManager
let pixmap: DrawableDescriptor = (resManager?.getDrawableDescriptor($r('app.media.icon')
    .id)) as DrawableDescriptor;
let pixmapNew: object = pixmap.getPixelMap()
  ```

当传入资源id或name为普通图片时，生成DrawableDescriptor对象。

## PixelMapDrawableDescriptor<sup>12+</sup>

支持通过传入pixelMap创建PixelMapDrawableDescriptor对象。继承自[DrawableDescriptor](#drawabledescriptor)。

### constructor<sup>12+</sup>

constructor(src?: image.PixelMap)

PixelMapDrawableDescriptor的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型              | 必填  | 说明                                       |
| --------- | ---------------- | ---- | ------------------------------------------ |
| src | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | 否 | PixelMap类型参数，存储 PixelMap 图片数据。 |


## LayeredDrawableDescriptor

当传入资源id或name为包含前景和背景资源的json文件时，生成LayeredDrawableDescriptor对象。继承自[DrawableDescriptor](#drawabledescriptor)。

drawable.json位于项目工程entry/src/main/resources/base/media目录下。定义请参考：

```json
{
  "layered-image":
  {
    "background" : "$media:background",
    "foreground" : "$media:foreground"
  }
}
```

**示例：**  

1. 使用json文件创建LayeredDrawableDescriptor。

    ```ts
    // xxx.ets
    import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

    @Entry
    @Component
    struct Index {
      private resManager = this.getUIContext().getHostContext()?.resourceManager;
 
      build() {
        Row() {
          Column() {
            Image((this.resManager?.getDrawableDescriptor($r('app.media.drawable').id) as LayeredDrawableDescriptor))
            Image(((this.resManager?.getDrawableDescriptor($r('app.media.drawable')
            .id) as LayeredDrawableDescriptor).getForeground()).getPixelMap())
          }.height('50%')
        }.width('50%')
      }
    }
    ```
2. 使用PixelMapDrawableDescriptor创建LayeredDrawableDescriptor。
   
    ```ts
    import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor } from '@kit.ArkUI';
    import { image } from '@kit.ImageKit';

    @Entry
    @Component
    struct Index {
      @State fore1: image.PixelMap | undefined = undefined;
      @State back1: image.PixelMap | undefined = undefined;

      @State foregroundDraw:DrawableDescriptor|undefined=undefined;
      @State backgroundDraw:DrawableDescriptor|undefined=undefined;
      @State maskDraw:DrawableDescriptor|undefined=undefined;
      @State maskPixel: image.PixelMap | undefined = undefined;
      @State draw : LayeredDrawableDescriptor | undefined = undefined;
      async aboutToAppear() {
        this.fore1 = await this.getPixmapFromMedia($r('app.media.foreground'));
        this.back1 = await this.getPixmapFromMedia($r('app.media.background'));
        this.maskPixel = await this.getPixmapFromMedia($r('app.media.ohos_icon_mask'));
        // 使用PixelMapDrawableDescriptor创建LayeredDrawableDescriptor
        this.foregroundDraw = new PixelMapDrawableDescriptor(this.fore1);
        this.backgroundDraw = new PixelMapDrawableDescriptor(this.back1);
        this.maskDraw = new PixelMapDrawableDescriptor(this.maskPixel);

        this.draw = new LayeredDrawableDescriptor(this.foregroundDraw,this.backgroundDraw,this.maskDraw);
      }
      build() {
        Row() {
          Column() {
              Image(this.draw)
                .width(300)
                .height(300)
          }.height('100%').justifyContent(FlexAlign.Center)
        }.width('100%').height("100%").backgroundColor(Color.Pink)
      }
      // 根据资源，通过图片框架获取pixelMap
      private async getPixmapFromMedia(resource: Resource) {
        let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent({
          bundleName: resource.bundleName,
          moduleName: resource.moduleName,
          id: resource.id
        });
        let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
        let createPixelMap: image.PixelMap = await imageSource.createPixelMap({
          desiredPixelFormat: image.PixelMapFormat.BGRA_8888
        });
        await imageSource.release();
        return createPixelMap;
      }
    }
    ```

### constructor<sup>12+</sup>

constructor(foreground?: DrawableDescriptor, background?: DrawableDescriptor, mask?: DrawableDescriptor)

LayeredDrawableDescriptor的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型              | 必填  | 说明                                       |
| --------- | ---------------- | ---- | ------------------------------------------ |
| foreground | [DrawableDescriptor](#drawabledescriptor)  | 否   | 分层图标的前景图片选项。 |
| background   | [DrawableDescriptor](#drawabledescriptor) | 否   | 分层图标的背景图片选项。  |
| mask | [DrawableDescriptor](#drawabledescriptor) | 否 | 分层图标的遮罩选项。 |

### getForeground
getForeground(): DrawableDescriptor

获取前景的DrawableDescriptor对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| [DrawableDescriptor](#drawabledescriptor) | DrawableDescriptor对象。 |

**示例：**
  ```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getForeground(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    let layeredDrawableDescriptor = (drawable as LayeredDrawableDescriptor).getForeground();
    return layeredDrawableDescriptor;
  }

  aboutToAppear(): void {
    this.drawableDescriptor = this.getForeground();
  }

  build() {
    RelativeContainer() {
      if (this.drawableDescriptor) {
        Image(this.drawableDescriptor)
          .width(100)
          .height(100)
          .borderWidth(1)
          .backgroundColor(Color.Green);
      }
    }
    .height('100%')
    .width('100%')
  }
}
  ```

### getBackground

getBackground(): DrawableDescriptor

获取背景的DrawableDescriptor对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| [DrawableDescriptor](#drawabledescriptor) | DrawableDescriptor对象。 |

**示例：**
  ```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getBackground(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    let layeredDrawableDescriptor = (drawable as LayeredDrawableDescriptor).getBackground();
    return layeredDrawableDescriptor;
  }

  aboutToAppear(): void {
    this.drawableDescriptor = this.getBackground();
  }

  build() {
    RelativeContainer() {
      if (this.drawableDescriptor) {
        Image(this.drawableDescriptor)
          .width(100)
          .height(100)
      }
    }
    .height('100%')
    .width('100%')
  }
}
  ```

### getMask

getMask(): DrawableDescriptor

获取蒙版的DrawableDescriptor对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| [DrawableDescriptor](#drawabledescriptor) | DrawableDescriptor对象。 |

**示例：**
  ```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getMask(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    let layeredDrawableDescriptor = (drawable as LayeredDrawableDescriptor).getMask();
    return layeredDrawableDescriptor;
  }

  aboutToAppear(): void {
    this.drawableDescriptor = this.getMask();
  }

  build() {
    RelativeContainer() {
      if (this.drawableDescriptor) {
        Image(this.drawableDescriptor)
          .width(100)
          .height(100)
      }
    }
    .height('100%')
    .width('100%')
  }
}
  ```
### getMaskClipPath

static getMaskClipPath(): string

LayeredDrawableDescriptor的静态方法，获取系统内置的裁切路径参数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| string | 返回裁切路径的命令字符串。 |

**示例：**

  ```ts
// xxx.ets
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Image($r('app.media.icon'))
          .width('200px').height('200px')
          .clipShape(new Path({commands:LayeredDrawableDescriptor.getMaskClipPath()}))
        Text(`获取系统内置的裁剪路径参数：`)
          .fontWeight(800)
        Text(JSON.stringify(LayeredDrawableDescriptor.getMaskClipPath()))
          .padding({ left: 20, right: 20 })
      }.height('100%').justifyContent(FlexAlign.Center)
    }.width('100%')
  }
}
  ```

## AnimationOptions<sup>12+</sup>

用于控制通过Image组件显示的PixelMap数组动画的播放行为。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTs-Dyn起始版本：** 12

**ArkTs-Sta起始版本：** 22

| 名称      | 类型    | 必填  | 说明                                    |
| ---------- | ------ | -----| --------------------------------------- |
| duration   | ArkTS-Dyn: number <br> ArkTS-Sta: int | 否   | 设置图片数组播放总时间。默认每张图片播放1秒。<br/> 取值范围：[0, +∞)      |
| iterations | ArkTS-Dyn: number <br> ArkTS-Sta: int | 否   | 设置图片数组播放次数。默认为1，值为-1时表示无限播放，值为0时表示不播放，值大于0时表示播放次数。 |

**示例：**

```ts
import { AnimationOptions } from '@kit.ArkUI';
@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 2000, iterations: 1 };
  build() {
  }
}
```

## AnimatedDrawableDescriptor<sup>12+</sup>

使用Image组件播放PixelMap数组时传入AnimatedDrawableDescriptor对象，该对象继承自[DrawableDescriptor](#drawabledescriptor)。

### constructor<sup>12+</sup>

constructor(pixelMaps: Array\<image.PixelMap>, options?: AnimationOptions)

AnimatedDrawableDescriptor的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型              | 必填  | 说明                                       |
| --------- | ---------------- | ---- | ------------------------------------------ |
| pixelMaps | Array\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)>  | 是   | PixelMap 数组类型参数，存储 PixelMap 图片数据。 |
| options   | [AnimationOptions](#animationoptions12) | 否   | 动画控制选项。                               |

**示例：**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct Example {
  pixelmaps: Array<image.PixelMap>  = [];
  options: AnimationOptions = {duration:1000, iterations:-1};
  @State animated: AnimatedDrawableDescriptor  = new AnimatedDrawableDescriptor(this.pixelmaps, this.options);
  async aboutToAppear() {
    this.pixelmaps.push(await this.getPixmapFromMedia($r('app.media.icon')));
    this.animated = new AnimatedDrawableDescriptor(this.pixelmaps, this.options);
  }
  build() {
    Column() {
      Row() {
        Image(this.animated)
      }
    }
  }
  private async getPixmapFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent({
      bundleName: resource.bundleName,
      moduleName: resource.moduleName,
      id: resource.id
    });
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let createPixelMap: image.PixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return createPixelMap;
  }
}

```

### 使用@ohos.transfer进行DrawableDescriptor类型转换

ArkTS-Dyn中使用ArkTS-Sta的DrawableDescriptor对象。

- 在ArkTS-Sta主模块中创建ArkTS-Dyn DrawableDescriptor，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  // entry/src/main/ets/pages/Index.ets
  import { Entry, Column, Component, Button, PixelMap, $r, FlexAlign } from '@ohos.arkui.component';
  import { PixelMapDrawableDescriptor, DrawableDescriptor } from '@ohos.arkui.drawableDescriptor';
  import transfer from '@ohos.transfer';
  import { MyChild, createPixelMapDrawDynamic } from 'library';

  @Entry
  @Component
  struct Index {
    aboutToAppear() {
      let resManager = this.getUIContext().getHostContext()?.resourceManager;
      if (resManager) {
        let drawableDescriptor: DrawableDescriptor = resManager.getDrawableDescriptor($r('app.media.startIcon').id);
        let pixelMap = drawableDescriptor.getPixelMap() as PixelMap;
        let pixelMapDraw = new PixelMapDrawableDescriptor(pixelMap);
        try {
          let pixelMapDrawDynamic = transfer.transferDynamic(pixelMapDraw, "ArkUI.DrawableDescriptor") as Object;
          let moduleName = ESValue.load("@normalized:N&entry&com.example.myApplication&library/Index&1.0.0");
          let pixelMapFunc = moduleName.getProperty('createPixelMapDrawDynamic');
          pixelMapFunc.invoke(pixelMapDrawDynamic);
        } catch (e: Error) {
          console.log('transferDynamic catch error：-----------' + e.message);
        }
      }
    }

    build() {
      Column() {
        MyChild()
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn DrawableDescriptor的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
    
  import { PixelMapDrawableDescriptor } from '@kit.ArkUI';

  let g_pixelMapDraw: PixelMapDrawableDescriptor = null;

  export function createPixelMapDrawDynamic(pixelMapDraw: any) {
    g_pixelMapDraw = pixelMapDraw;
  }

  @Component
  export struct MyChild {
    @State pixelMapDraw_: any = null;

    build() {
      Column({ space: 5 }) {
        Button('更新图片')
          .onClick(() => {
            let pixelMapDraw = g_pixelMapDraw;
            if (pixelMapDraw) {
              this.pixelMapDraw_ = pixelMapDraw;
            }
          })
        Image(this.pixelMapDraw_)
          .width(100)
          .height(100)
      }
    }
  }
  ```
  ![image](figures/drawableTransferDyn.png)

ArkTS-Sta中使用ArkTS-Dyn的DrawableDescriptor对象。

- 在ArkTS-Sta主模块得到ArkTS-Dyn子模块`library`创建的ArkTS-Dyn DrawableDescriptor对象。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  // entry/src/main/ets/pages/Index.ets  
  import { Entry, Column, Component, Button, Image, Row, FlexAlign } from '@ohos.arkui.component';
  import { PixelMapDrawableDescriptor } from '@ohos.arkui.drawableDescriptor';
  import transfer from '@ohos.transfer';
  import { State } from '@ohos.arkui.stateManagement';
  import { getPixelMapDrawDynamic } from 'library';

  @Entry
  @Component
  struct Index {
    @State pixelMapDrawableDescriptor_: PixelMapDrawableDescriptor = new PixelMapDrawableDescriptor();

    aboutToAppear() {
      let resPixelMap = getPixelMapDrawDynamic();
      try {
        let PixelMapDrawStatic = transfer.transferStatic(resPixelMap, "ArkUI.DrawableDescriptor");
        this.pixelMapDrawableDescriptor_ = PixelMapDrawStatic as PixelMapDrawableDescriptor;
      } catch (e: Error) {
        console.log('transferStatic catch error：-----------' + e.message);
      }
    }

    build() {
      Column() {
        Image(this.pixelMapDrawableDescriptor_)
          .width(100)
          .height(100)
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
  }
  ```
  
- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供创建ArkTS-Dyn DrawableDescriptor的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { PixelMapDrawableDescriptor } from '@kit.ArkUI';
  import { image } from '@kit.ImageKit';

  export function getPixelMapDrawDynamic() {
    let opts: image.SourceOptions = {
      sourcePixelFormat: image.PixelMapFormat.BGRA_8888,
      sourceDensity: 0
    };
    let imageSourceApi: image.ImageSource =
      image.createImageSource("/data/storage/el2/base/haps/entry/files/startIcon.png", opts);
    if (imageSourceApi == undefined) {
      return undefined;
    }
    let option: image.DecodingOptions = { desiredPixelFormat: 4 };
    let pixelMap = imageSourceApi.createPixelMapSync(option);
    let pixelMapDraw: PixelMapDrawableDescriptor = new PixelMapDrawableDescriptor(pixelMap);
    return pixelMapDraw;
  }
  ```
  ![image](figures/drawableTransferSta.png)