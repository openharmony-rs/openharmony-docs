# Filter

Filter效果类，用于将模糊、边缘像素扩展、水波纹等效果添加到组件上。在调用Filter的方法前， 需要先通过[createFilter](arkts-arkgraphics2d-uieffect-createfilter-f.md)创建一个Filter实例。

**起始版本：** 23

<!--Device-uiEffect-interface Filter--><!--Device-uiEffect-interface Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## blur

```TypeScript
blur(blurRadius: double): Filter
```

将模糊效果添加至组件上。

**起始版本：** 23

<!--Device-Filter-blur(blurRadius: double): Filter--><!--Device-Filter-blur(blurRadius: double): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | double | 是 | 模糊半径，单位为px。 取值需大于等于0，模糊半径越大，模糊效果越强。 模糊半径为0时无模糊效果。传入负数时自动修正为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回挂载了模糊效果的Filter，支持链式调用继续添加其他效果。 |

**示例**

```TypeScript
// xxx.ts
import { uiEffect } from '@kit.ArkGraphics2D';

let filter: uiEffect.Filter = uiEffect.createFilter();
filter.blur(10);

@Entry
@Component
struct UIEffectFilterExample {
    build(){
        Column({ space: 15 }) {
            Text('UIEffectFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
            Image($r('app.media.foreground'))
                .width(100)
                .height(100)
                .backgroundImage($r('app.media.background'))
                .backgroundImagePosition(Alignment.Center)
                .backgroundImageSize({ width: 90, height: 90 })
                .backgroundFilter(filter)
        }
        .height('100%')
        .width('100%')
    }
}
```

