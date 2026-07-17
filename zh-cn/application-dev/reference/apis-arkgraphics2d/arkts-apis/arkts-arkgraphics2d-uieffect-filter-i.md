# Filter

**起始版本：** 12

<!--Device-uiEffect-interface Filter--><!--Device-uiEffect-interface Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## blur

```TypeScript
blur(blurRadius: number): Filter
```

将模糊效果添加至组件上。

**起始版本：** 12

<!--Device-Filter-blur(blurRadius: double): Filter--><!--Device-Filter-blur(blurRadius: double): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | number | 是 | 模糊半径，单位为px。取值需大于等于0，模糊半径越大，模糊效果越强。模糊半径为0时无模糊效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | - 返回挂载了模糊效果的Filter。 |

**示例：**

```TypeScript
// xxx.ts
import { uiEffect } from '@kit.ArkGraphics2D';

// 创建Filter实例
let filter: uiEffect.Filter = uiEffect.createFilter();
// 设置模糊半径为10px
filter.blur(10);

@Entry
@Component
struct UIEffectFilterExample {
    build() {
        Column({ space: 15 }) {
            Text('UIEffectFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
            Image($r('app.media.foreground'))
                .width(100)
                .height(100)
                .backgroundImage($r('app.media.background'))
                .backgroundImagePosition(Alignment.Center)
                .backgroundImageSize({ width: 90, height: 90 })
                // 将Filter效果应用到组件背景
                .backgroundFilter(filter)
        }
        .height('100%')
        .width('100%')
    }
}

```

