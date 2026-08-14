# Filter

图像效果类，用于通过链式调用将指定效果添加到效果链表中，适用于图片滤镜处理、视觉效果增强、图像美化等场景。 在调用Filter的方法前，需要先通过[createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createEffect)创建一个Filter实例。 在添加效果后，需调用[getEffectPixelMap](arkts-arkgraphics2d-effectkit-filter-i.md#getEffectPixelMap)获取处理后的图像。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-effectKit-interface Filter--><!--Device-effectKit-interface Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## ellipticalGradientBlur

```TypeScript
ellipticalGradientBlur(blurRadius: double, center: EllipticalMaskCenter,
      maskRadius: EllipticalMaskRadius, fractionStops: FractionStop[]): Filter
```

将带有椭圆形遮罩的渐变模糊效果添加到效果链表中，返回链表的头节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Filter-ellipticalGradientBlur(blurRadius: double, center: EllipticalMaskCenter,      maskRadius: EllipticalMaskRadius, fractionStops: FractionStop[]): Filter--><!--Device-Filter-ellipticalGradientBlur(blurRadius: double, center: EllipticalMaskCenter,      maskRadius: EllipticalMaskRadius, fractionStops: FractionStop[]): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | double | 是 | 模糊半径，取正整数，单位为px，模糊半径大于60px时自动截断。 模糊效果与所设置的模糊半径值成正比，值越大效果越明显。 |
| center | [EllipticalMaskCenter](arkts-arkgraphics2d-effectkit-ellipticalmaskcenter-t-sys.md) | 是 | 椭圆形遮罩的中心点坐标。 |
| maskRadius | [EllipticalMaskRadius](arkts-arkgraphics2d-effectkit-ellipticalmaskradius-t-sys.md) | 是 | 椭圆形遮罩在X轴和Y轴方向的半径。 |
| fractionStops | [FractionStop](../../apis-na/arkts-apis/arkts-na-fractionstop-t.md)[] | 是 | 渐变模糊位置与程度数组。数组元素为二元数组，第一个元素表示位置，第二个元素表示模糊程度。 位置取值范围为[0, 1]，椭圆中心对应位置0，椭圆边界对应位置1。模糊程度取值范围为[0, 1]，0表示无模糊，大于1的值自动转为1。 位置参数值需严格递增，数组长度不能小于2，最大为12。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回已添加的图像效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

## 示例

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// 传入读取的图片数据
function ImageEllipticalGradientBlur(Image: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(Image);
    let blurRadius:number = 25;
    let fractionStops:FractionStop[] = [[0, 0.2], [0.5, 0.7]];
    let maskRadius:effectKit.EllipticalMaskRadius = [1, 1];
    let center:effectKit.EllipticalMaskCenter = [0.5, 0.5];
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // 对图片添加效果标识
        headFilter.ellipticalGradientBlur(blurRadius, center, maskRadius, fractionStops);
      }
      // 按照添加的效果标识对图片进行处理并且返回处理好的图片数据
      headFilter.getEffectPixelMap(false).then(imageData => {
        resolve(imageData);
      })
    })
  })
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // 读取rawfile文件夹下的图片文件，也可根据需求更换读取方式，保证最终得到的是ArrayBuffer格式的图片数据即可
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try{
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    }catch (err){
      return undefined
    }
  }

  async aboutToAppear(): Promise<void>{
    this.imageBuffer = await this.getFileBuffer();
    if(this.imageBuffer == undefined){
      return;
    }
    // 图片处理为异步操作，可以依据是否需要拿到处理好的图片数据再进行下一步逻辑，按需添加await进行同步
    this.imagePixelMap = await ImageEllipticalGradientBlur(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}
```

