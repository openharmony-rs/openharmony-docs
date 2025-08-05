# @ohos.matrix4 (矩阵变换)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--SE: @yangfan229-->
<!--TSE: @lxl007-->

本模块提供矩阵变换功能，支持对图形进行平移、旋转和缩放等。

> **说明：**
>
> 本模块首批接口从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## 导入模块

```ts
import { matrix4 } from '@kit.ArkUI';
```


## matrix4.init

init(options: [number,number,number,number,number,number,number,number,number,number,number,number,number,number,number,number]): Matrix4Transit

Matrix的构造函数，可以通过传入的参数创建一个四阶矩阵，矩阵为列优先。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| options | [number,number,number,number,<br/>number,number,number,number,<br/>number,number,number,number,<br/>number,number,number,number] | 是   | 参数为长度为16（4\*4）的number数组,&nbsp;详情见四阶矩阵说明。<br/>各number取值范围：(-∞, +∞)<br/>默认值：<br/>[1,&nbsp;0,&nbsp;0,&nbsp;0,<br/>0,&nbsp;1,&nbsp;0,&nbsp;0,<br/>0,&nbsp;0,&nbsp;1,&nbsp;0,<br/>0,&nbsp;0,&nbsp;0,&nbsp;1] |

**返回值：**

| 类型                              | 说明                         |
| --------------------------------- | ---------------------------- |
| [Matrix4Transit](#matrix4transit) | 根据入参创建的四阶矩阵对象。 |

**四阶矩阵说明：**

| 参数名  | 类型     | 必填   | 说明                   |
| ---- | ------ | ---- | -------------------- |
| m00  | number | 是    | x轴缩放值，单位矩阵默认为1。      |
| m01  | number | 是    | 第2个值，xyz轴旋转或倾斜会影响这个值。   |
| m02  | number | 是    | 第3个值，xyz轴旋转会影响这个值。   |
| m03  | number | 是    | 第4个值，透视投影会影响这个值。               |
| m10  | number | 是    | 第5个值，xyz轴旋转或倾斜会影响这个值。   |
| m11  | number | 是    | y轴缩放值，单位矩阵默认为1。      |
| m12  | number | 是    | 第7个值，xyz轴旋转会影响这个值。   |
| m13  | number | 是    | 第8个值，透视投影会影响这个值。               |
| m20  | number | 是    | 第9个值，xyz轴旋转会影响这个值。   |
| m21  | number | 是    | 第10个值，xyz轴旋转会影响这个值。  |
| m22  | number | 是    | z轴缩放值，单位矩阵默认为1。      |
| m23  | number | 是    | 第12个值，透视投影会影响这个值。               |
| m30  | number | 是    | x轴平移值，单位px，单位矩阵默认为0。 |
| m31  | number | 是    | y轴平移值，单位px，单位矩阵默认为0。 |
| m32  | number | 是    | z轴平移值，单位px，单位矩阵默认为0。 |
| m33  | number | 是    | 齐次坐标下生效，产生透视投影效果。    |

**示例**

```ts
import { matrix4 } from '@kit.ArkUI';

// 创建一个四阶矩阵
let matrix = matrix4.init(
  [1.0, 0.0, 0.0, 0.0,
    0.0, 1.0, 0.0, 0.0,
    0.0, 0.0, 1.0, 0.0,
    0.0, 0.0, 0.0, 1.0]);

@Entry
@Component
struct Tests {
  build() {
    Column() {
      Image($r("app.media.zh"))
        .width("40%")
        .height(100)
        .transform(matrix)
    }
  }
}
```


## matrix4.identity

identity(): Matrix4Transit

Matrix的初始化函数，可以返回一个单位矩阵对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                              | 说明           |
| --------------------------------- | -------------- |
| [Matrix4Transit](#matrix4transit) | 单位矩阵对象。 |

**示例：**

```ts
// matrix1 和 matrix2 效果一致
import { matrix4 } from '@kit.ArkUI';

let matrix1 = matrix4.init(
  [1.0, 0.0, 0.0, 0.0,
    0.0, 1.0, 0.0, 0.0,
    0.0, 0.0, 1.0, 0.0,
    0.0, 0.0, 0.0, 1.0]);
let matrix2 = matrix4.identity();

@Entry
@Component
struct Tests {
  build() {
    Column() {
      Image($r("app.media.zh"))
        .width("40%")
        .height(100)
        .transform(matrix1)
      Image($r("app.media.zh"))
        .width("40%")
        .height(100)
        .margin({ top: 150 })
        .transform(matrix2)
    }
  }
}
```

## Matrix4Transit

矩阵对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

### copy

copy(): Matrix4Transit

Matrix的拷贝函数，可以拷贝一份当前的矩阵对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                              | 说明                 |
| --------------------------------- | -------------------- |
| [Matrix4Transit](#matrix4transit) | 当前矩阵的拷贝对象。 |


**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().scale({ x: 1.5 });
  private matrix2 = this.matrix1.copy().translate({ x: 200 });
  imageSize: Length = '300px';

  build() {
    Column({ space: "50px" }) {
      Image($r("app.media.testImage"))
        .width(this.imageSize)
        .height(this.imageSize)
      Image($r("app.media.testImage"))
        .width(this.imageSize)
        .height(this.imageSize)
        .transform(this.matrix1)
      Image($r("app.media.testImage"))
        .width(this.imageSize)
        .height(this.imageSize)
        .transform(this.matrix2)
    }.alignItems(HorizontalAlign.Center)
    .height('100%').width("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

![zh-cn_image_0000001219744181](figures/h-cn_image_0000001219744185.png)
### combine

combine(options: Matrix4Transit): Matrix4Transit

Matrix的叠加函数，可以将两个矩阵的效果叠加起来生成一个新的矩阵对象。会改变调用该函数的原始矩阵。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                              | 必填 | 说明               |
| ------ | --------------------------------- | ---- | ------------------ |
| options | [Matrix4Transit](#matrix4transit) | 是   | 待叠加的矩阵对象。 |

**返回值：**

| 类型                              | 说明               |
| --------------------------------- | ------------------ |
| [Matrix4Transit](#matrix4transit) | 矩阵叠加后的对象。 |

**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().translate({ x: 200 });
  private matrix2 = matrix4.identity().scale({ x: 2 });

  build() {
    Column() {
      // 矩阵变换前
      Image($r("app.media.icon"))
        .width("40%")
        .height(100)
        .margin({ top: 50 })
      // 先平移x轴200px，再缩放两倍x轴，得到矩阵变换后的效果图
      Image($r("app.media.icon"))
        .transform(this.matrix1.copy().combine(this.matrix2))
        .width("40%")
        .height(100)
        .margin({ top: 50 })
    }
  }
}
```

![zh-cn_image_0000001118642902](figures/zh-cn_image_0000001118642902.png)


### invert

invert(): Matrix4Transit

Matrix的逆函数，可以返回一个当前矩阵对象的逆矩阵，即效果正好相反。会改变调用该函数的原始矩阵。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                              | 说明                   |
| --------------------------------- | ---------------------- |
| [Matrix4Transit](#matrix4transit) | 当前矩阵的逆矩阵对象。 |

**示例：**

```ts
import { matrix4 } from '@kit.ArkUI';

// matrix1(宽放大2倍) 和 matrix2(宽缩小2倍) 效果相反
let matrix1 = matrix4.identity().scale({ x: 2 });
let matrix2 = matrix1.copy().invert();

@Entry
@Component
struct Tests {
  build() {
    Column() {
      Image($r("app.media.zh"))
        .width(200)
        .height(100)
        .transform(matrix1)
        .margin({ top: 100 })
      Image($r("app.media.zh"))
        .width(200)
        .height(100)
        .margin({ top: 150 })
        .transform(matrix2)
    }
  }
}
```


### translate

translate(options: TranslateOption): Matrix4Transit

Matrix的平移函数，可以为当前矩阵增加x轴/y轴/z轴平移效果。会改变调用该函数的原始矩阵。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                | 必填 | 说明           |
| ------ | ----------------------------------- | ---- | -------------- |
| options | [TranslateOption](#translateoption) | 是   | 设置平移参数。 |

**返回值：**

| 类型                              | 说明                         |
| --------------------------------- | ---------------------------- |
| [Matrix4Transit](#matrix4transit) | 平移效果后的矩阵对象。 |

**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().translate({ x: 100, y: 200, z: 30 });

  build() {
    Column() {
      Image($r("app.media.bg1")).transform(this.matrix1)
        .width("40%")
        .height(100)
    }
  }
}
```

![zh-cn_image_0000001219662645](figures/zh-cn_image_0000001219662645.png)


### scale

scale(options: ScaleOption): Matrix4Transit

Matrix的缩放函数，可以为当前矩阵增加x轴/y轴/z轴缩放效果。会改变调用该函数的原始矩阵。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                        | 必填 | 说明           |
| ------ | --------------------------- | ---- | -------------- |
| options | [ScaleOption](#scaleoption) | 是   | 设置缩放参数。 |

**返回值：**

| 类型                              | 说明                         |
| --------------------------------- | ---------------------------- |
| [Matrix4Transit](#matrix4transit) | 缩放效果后的矩阵对象。 |

**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .scale({
      x: 2,
      y: 3,
      z: 4,
      centerX: 50,
      centerY: 50
    });

  build() {
    Column() {
      Image($r("app.media.testImage")).transform(this.matrix1)
        .width("300px")
        .height("300px")
    }.width("100%").height("100%").justifyContent(FlexAlign.Center)
  }
}
```

![zh-cn_image_0000001219864131](figures/zh-cn_image_0000001219864131.png)


### skew<sup>12+</sup>

skew(x: number, y: number): Matrix4Transit

Matrix的倾斜函数，可以为当前矩阵增加x轴/y轴倾斜效果。会改变调用该函数的原始矩阵。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                        | 必填 | 说明           |
| ------ | --------------------------- | ---- | -------------- |
| x | number | 是   | 设置x轴倾斜参数。 |
| y | number | 是   | 设置y轴倾斜参数。 |

**返回值：**

| 类型                              | 说明                         |
| --------------------------------- | ---------------------------- |
| [Matrix4Transit](#matrix4transit) | 倾斜效果后的矩阵对象。 |

**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().skew(2, 3);

  build() {
    Column() {
      Image($r("app.media.bg1")).transform(this.matrix1)
        .height(100)
        .margin({
          top: 300
        })
    }
    .width("100%")
    .height("100%")
  }
}
```

![zh-cn_image_0000001219864132](figures/zh-cn_image_0000001219864132.jpeg)


### rotate

rotate(options: RotateOption): Matrix4Transit

Matrix的旋转函数，可以为当前矩阵增加x轴/y轴/z轴旋转效果。会改变调用该函数的原始矩阵。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                          | 必填 | 说明           |
| ------ | ----------------------------- | ---- | -------------- |
| options | [RotateOption](#rotateoption) | 是   | 设置旋转参数。 |

**返回值：**

| 类型                              | 说明                         |
| --------------------------------- | ---------------------------- |
| [Matrix4Transit](#matrix4transit) | 旋转效果后的矩阵对象。 |

**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .rotate({
      x: 1,
      y: 1,
      z: 2,
      angle: 30
    });

  build() {
    Column() {
      Image($r("app.media.bg1")).transform(this.matrix1)
        .width("40%")
        .height(100)
    }.width("100%").margin({ top: 50 })
  }
}
```

![zh-cn_image_0000001174422898](figures/zh-cn_image_0000001174422898.png)


### transformPoint

transformPoint(options: [number, number]): [number, number]

Matrix的坐标点转换函数，可以将当前的变换效果作用到一个坐标点上。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型             | 必填 | 说明               |
| ------- | ---------------- | ---- | ------------------ |
| options | [number, number] | 是   | 需要转换的坐标点。 |

**返回值：**

| 类型             | 说明                        |
| ---------------- | --------------------------- |
| [number, number] | 返回矩阵变换后的Point对象。 |

**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private originPoint: number[] = [50, 50];
  private matrix_1 = matrix4.identity().translate({ x: 150, y: -50 });
  private transformPoint = this.matrix_1.transformPoint([this.originPoint[0], this.originPoint[1]]);
  private matrix_2 = matrix4.identity().translate({ x: this.transformPoint[0], y: this.transformPoint[1] });

  build() {
    Column() {
      Text(`矩阵变换前的坐标：[${this.originPoint}]`)
        .fontSize(16)
      Image($r("app.media.image"))
        .width('600px')
        .height('300px')
        .margin({ top: 50 })
      Text(`矩阵变换后的坐标：[${this.transformPoint}]`)
        .fontSize(16)
        .margin({ top: 100 })
      Image($r("app.media.image"))
        .width('600px')
        .height('300px')
        .margin({ top: 50 })
        .transform(this.matrix_2)
    }.width("100%").padding(50)
  }
}
```

![zh-cn_image_0000001219864133](figures/zh-cn_image_0000001219864133.PNG)

### setPolyToPoly<sup>12+</sup>

setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit

将一个多边形的顶点坐标映射到另外一个多边形的顶点坐标。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型             | 必填 | 说明               |
| ------ | ---------------- | ---- | ------------------ |
| options | [PolyToPolyOptions](#polytopolyoptions12)  | 是   | 映射相关的参数。 |

**返回值：**

| 类型                              | 说明                 |
| --------------------------------- | -------------------- |
| [Matrix4Transit](#matrix4transit) | 当前矩阵变换后的对象。 |

> **说明：**
> 需要配合scale({centerX:0,centerY:0,x:1})保证变换的中心点是组件左上角。

**示例：**

```ts
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private matrix1 = matrix4.identity().setPolyToPoly({
    src: [{ x: 0, y: 0 }, { x: 500, y: 0 }, { x: 0, y: 500 }, { x: 500, y: 500 }],
    dst: [{ x: 0, y: 0 }, { x: 500, y: 0 }, { x: 0, y: 500 }, { x: 750, y: 1000 }], pointCount: 4
  });

  build() {
    Stack() {
      Column().backgroundColor(Color.Blue)
        .width('500px')
        .height('500px')
      Image($r('app.media.transition_image1'))
        .scale({ centerX: 0, centerY: 0, x: 1 })
        .transform(this.matrix1)
        .width('500px')
        .height('500px')
    }.width("100%").height("100%").opacity(0.5)
  }
}
```
![zh-cn_image_0000001174422898](figures/setPolyTopoly.png)
## TranslateOption

平移参数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型   | 必填 | 说明                                                        |
| ---- | ------ | ---- | ----------------------------------------------------------- |
| x    | number | 否   | x轴的平移距离。<br/>单位：px<br/>默认值：0<br/>取值范围 (-∞, +∞) |
| y    | number | 否   | y轴的平移距离。<br/>单位：px<br/>默认值：0<br/>取值范围 (-∞, +∞) |
| z    | number | 否   | z轴的平移距离。<br/>单位：px<br/>默认值：0<br/>取值范围 (-∞, +∞) |

## ScaleOption

缩放参数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| x       | number | 否   | x轴的缩放倍数。x>1时以x轴方向放大，0&lt;x&lt;1时以x轴方向缩小，x<0时沿x轴反向并缩放。<br/>默认值：1<br/>取值范围 (-∞, +∞) |
| y       | number | 否   | y轴的缩放倍数。y>1时以y轴方向放大，0&lt;y&lt;1时以y轴方向缩小，y<0时沿y轴反向并缩放。<br/>默认值：1<br/>取值范围 (-∞, +∞) |
| z       | number | 否   | z轴的缩放倍数。z>1时以z轴方向放大，0&lt;z&lt;1时以z轴方向缩小，z<0时沿z轴反向并缩放。<br/>默认值：1<br/>取值范围 (-∞, +∞) |
| centerX | number | 否   | 变换中心点x轴坐标。<br/>单位：px<br/>默认值：组件中心点x轴坐标。<br/>取值范围 (-∞, +∞)    |
| centerY | number | 否   | 变换中心点y轴坐标。<br/>单位：px<br/>默认值：组件中心点y轴坐标。<br/>取值范围 (-∞, +∞)    |

## RotateOption

旋转参数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| x       | number | 否   | 旋转轴向量x坐标。<br/>默认值：0。<br/>取值范围 (-∞, +∞)      |
| y       | number | 否   | 旋转轴向量y坐标。<br/>默认值：0。<br/>取值范围 (-∞, +∞)      |
| z       | number | 否   | 旋转轴向量z坐标。<br/>默认值：0。<br/>取值范围 (-∞, +∞)。<br/>**说明：** 旋转向量中x、y、z至少有一个不为0才有意义。 |
| angle   | number | 否   | 旋转角度。<br/>默认值：0                                     |
| centerX | number | 否   | 单次矩阵变换中心点相对于组件变换中心点（锚点）的额外x轴偏移值。<br/>单位：px<br/>默认值：0<br/>**说明：** <br/>为0时表示x方向的矩阵变换中心恰好为组件x方向锚点，取值表示相对组件x方向锚点的额外偏移量。具体实现可参考[示例3（按中心点旋转）](arkui-ts/ts-universal-attributes-transformation.md#示例3按中心点旋转)。 |
| centerY | number | 否   | 单次矩阵变换中心点相对于组件变换中心点（锚点）的额外y轴偏移值。<br/>单位：px<br/>默认值：0<br/>**说明：** <br/>为0时表示y方向的矩阵变换中心恰好为组件y方向锚点，取值表示相对组件y方向锚点的额外偏移量。具体实现可参考[示例3（按中心点旋转）](arkui-ts/ts-universal-attributes-transformation.md#示例3按中心点旋转)。 |

## PolyToPolyOptions<sup>12+</sup>

多边形到多边形的映射选项。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型   | 必填 | 说明                                                        |
| ---- | ------ | ---- | ----------------------------------------------------------- |
| src    |  Array<[Point](#point12)> | 是   | 源点坐标。 |
| srcIndex    | number | 否   | 源点坐标起始索引。<br>默认值:0 <br/> 取值范围：[0, +∞)|
| dst    |  Array<[Point](#point12)>  | 是   | 目标点坐标。 |
| dstIndex    | number | 否   |  目标坐标起始索引。<br>默认值: src.length/2 <br/> 取值范围：[0, +∞) |
| pointCount    | number | 否   | 使用到的点数量。<br>默认值: 0 <br/> 取值范围：[0, +∞)|

## Point<sup>12+</sup>

坐标点的数据结构。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型   | 必填 | 说明                                                        |
| ---- | ------ | ---- | ----------------------------------------------------------- |
| x    |  number | 是   | x轴坐标。<br/>取值范围：(-∞, +∞) |
| y    | number | 是   | y轴坐标。<br/>取值范围：(-∞, +∞) |

## matrix4.copy<sup>(deprecated)</sup>

copy(): Matrix4Transit


Matrix的拷贝函数，可以拷贝一份当前的矩阵对象。

> **说明：**
>
> 从API version 10开始废弃。建议使用[Matrix4Transit.copy](#copy)替代。


**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                              | 说明                 |
| --------------------------------- | -------------------- |
| [Matrix4Transit](#matrix4transit) | 当前矩阵的拷贝对象。 |

**示例：**

```ts
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().translate({ x: 100 });
  // 对matrix1的拷贝矩阵做scale操作，不影响到matrix1
  private matrix2 = this.matrix1.copy().scale({ x: 2 });

  build() {
    Column() {
      Image($r("app.media.bg1"))
        .width("40%")
        .height(100)
        .transform(this.matrix1)
      Image($r("app.media.bg2"))
        .width("40%")
        .height(100)
        .margin({ top: 50 })
        .transform(this.matrix2)
    }
  }
}
```

![zh-cn_image_0000001219744181](figures/zh-cn_image_0000001219744181.png)

## matrix4.invert<sup>(deprecated)</sup>

invert(): Matrix4Transit

Matrix的逆函数，可以返回一个当前矩阵对象的逆矩阵，即效果正好相反。

> **说明：**
>
> 从API version 10开始废弃。建议使用[Matrix4Transit.invert](#invert)替代。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                              | 说明                   |
| --------------------------------- | ---------------------- |
| [Matrix4Transit](#matrix4transit) | 当前矩阵的逆矩阵对象。 |

## matrix4.combine<sup>(deprecated)</sup>

combine(options: Matrix4Transit): Matrix4Transit

Matrix的叠加函数，可以将两个矩阵的效果叠加起来生成一个新的矩阵对象。

> **说明：**
>
> 从API version 10开始废弃。建议使用[Matrix4Transit.combine](#combine)替代。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                              | 必填 | 说明               |
| ------- | --------------------------------- | ---- | ------------------ |
| options | [Matrix4Transit](#matrix4transit) | 是   | 待叠加的矩阵对象。 |

**返回值：**

| 类型                              | 说明                   |
| --------------------------------- | ---------------------- |
| [Matrix4Transit](#matrix4transit) | 叠加后的矩阵对象。 |

## matrix4.translate<sup>(deprecated)</sup>

translate(options: TranslateOption): Matrix4Transit

Matrix的平移函数，可以为当前矩阵增加x轴/y轴/z轴平移效果。

> **说明：**
>
> 从API version 10开始废弃。建议使用[Matrix4Transit.translate](#translate)替代。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                | 必填 | 说明           |
| ------- | ----------------------------------- | ---- | -------------- |
| options | [TranslateOption](#translateoption) | 是   | 设置平移参数。 |

**返回值：**

| 类型                              | 说明                   |
| --------------------------------- | ---------------------- |
| [Matrix4Transit](#matrix4transit) | 平移后的矩阵对象。 |

## matrix4.scale<sup>(deprecated)</sup>

scale(options: ScaleOption): Matrix4Transit

Matrix的缩放函数，可以为当前矩阵增加x轴/y轴/z轴缩放效果。

> **说明：**
>
> 从API version 10开始废弃。建议使用[Matrix4Transit.scale](#scale)替代。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                        | 必填 | 说明           |
| ------- | --------------------------- | ---- | -------------- |
| options | [ScaleOption](#scaleoption) | 是   | 设置缩放参数。 |

**返回值：**

| 类型                              | 说明                   |
| --------------------------------- | ---------------------- |
| [Matrix4Transit](#matrix4transit) | 缩放后的矩阵对象。 |

## matrix4.rotate<sup>(deprecated)</sup>

rotate(options: RotateOption): Matrix4Transit

Matrix的旋转函数，可以为当前矩阵增加x轴/y轴/z轴旋转效果。

> **说明：**
>
> 从API version 10开始废弃。建议使用[Matrix4Transit.rotate](#rotate)替代。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                          | 必填 | 说明           |
| ------- | ----------------------------- | ---- | -------------- |
| options | [RotateOption](#rotateoption) | 是   | 设置旋转参数。 |

**返回值：**

| 类型                              | 说明                   |
| --------------------------------- | ---------------------- |
| [Matrix4Transit](#matrix4transit) | 旋转后的矩阵对象。 |

## matrix4.transformPoint<sup>(deprecated)</sup>

transformPoint(options: [number, number]): [number, number]

Matrix的坐标点转换函数，可以将当前的变换效果作用到一个坐标点上。

> **说明：**
>
> 从API version 10开始废弃。建议使用[Matrix4Transit.transformPoint](#transformpoint)替代。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型             | 必填 | 说明               |
| ------- | ---------------- | ---- | ------------------ |
| options | [number, number] | 是   | 需要转换的坐标点。 |

**返回值：**

| 类型             | 说明                        |
| ---------------- | --------------------------- |
| [number, number] | 返回矩阵变换后的Point对象。 |