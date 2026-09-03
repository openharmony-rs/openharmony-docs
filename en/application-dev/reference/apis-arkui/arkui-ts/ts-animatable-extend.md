# @AnimatableExtend: Animatable Property Definition

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-28T01:36:50.899Z pushedAt=2026-08-28T08:14:19.288Z -->

The **@AnimatableExtend** decorator is used to customize animatable property methods. Functions defined within this decorator must be used together with the [animation](ts-animatorproperty.md#animation) property and called before the **animation** property, so that changing the property value can trigger the animation effect of the **animation** property. During the animation process, the function is called on a frame-by-frame basis until the animation ends. Common uses of this decorator include:

1. Converting non-animatable properties into animatable ones: Customize data calculation rules that enable interpolation for the property (that is, calculate the intermediate value of each frame between the animation start value and end value according to certain rules), allowing the animation to drive the property to gradually transition from the start value to the end value.

2. Enabling frame-by-frame property changes to achieve frame-by-frame layout effects.

- Animatable property: a property that triggers an animation effect when its value changes (after being called before the **animation** property), resulting in a smooth transition effect. Examples include **height**, **width**, **backgroundColor**, **translate**, and **fontSize** (of the **Text** component).

- Non-animatable property: a property that does not trigger an animation effect when its value changes (even if called before the **animation** property). Its value changes abruptly without transitions. An example is the **points** property of the **Polyline** component.

> **NOTE**
>
> - This decorator is supported since API version 10. If new content is added in subsequent versions, the start version of the content will be marked with a superscript.
>
> - The APIs of this module can be used only in the stage model.
>
> - When using a property method decorated by @AnimatableExtend, the method must be called before the **animation** property of the same component for the animation transition effect to take effect.

## Syntax

```ts
@AnimatableExtend(UIComponentName) function functionName(value: typeName) { 
  .propertyName(value)
}
```

- \@AnimatableExtend can be defined only globally.

- The parameter of the \@AnimatableExtend decorated function must be of the number type or a custom type that implements the **AnimatableArithmetic\<T\>** API.

- The function body of an \@AnimatableExtend decorated function can only access attribute methods of the component type specified within the parentheses of @AnimatableExtend.

- Functions defined by \@AnimatableExtend must be called before the **animation** property for the animation effect to take effect. If they are called after the **animation** property or are not used together with the **animation** property, the property value changes abruptly to the target value without any animation transition effect.

## AnimatableArithmetic\<T\>

The **AnimatableArithmetic** API defines animation calculation rules for non-number data types. To animate non-number data (such as arrays, structs, and colors), you need to implement the addition, subtraction, multiplication, and equality checking functions in the **AnimatableArithmetic\<T\>** API. This enables the data to participate in animation interpolation calculations and to detect whether the data has changed. In other words, the non-number data is defined as types that implement the **AnimatableArithmetic\<T\>** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### plus

plus(rhs: AnimatableArithmetic\<T\>): AnimatableArithmetic\<T\>

Defines the addition operation rule for this data type. It must be implemented together with the other methods of the **AnimatableArithmetic\<T\>** API to enable the custom data type to participate in the animation interpolation operation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                               | Mandatory| Description                                   |
| ----- | --------------------------------- | ---- | ------------------------------------- |
| rhs | [AnimatableArithmetic\<T\>](#animatablearithmetict) | Yes | The other data object for addition with the current object. It should be an instance of the same concrete type as the current object. |

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| [AnimatableArithmetic\<T\>](#animatablearithmetict) | Result of the addition operation, used to calculate the intermediate value between two data values during the animation interpolation process. |

### subtract

subtract(rhs: AnimatableArithmetic\<T\>): AnimatableArithmetic\<T\>

Defines the subtraction operation rule for this data type. In the animation interpolation operation, it is used to calculate the difference between the start value and the target value, and the difference is used as the input of the multiplication operation. It must be implemented together with the other methods of the **AnimatableArithmetic\<T\>** API to enable the custom data type to participate in the animation interpolation operation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                               | Mandatory| Description                                   |
| ----- | --------------------------------- | ---- | ------------------------------------- |
| rhs | [AnimatableArithmetic\<T\>](#animatablearithmetict) | Yes | The other data object for subtraction with the current object. It should be an instance of the same concrete type as the current object. |

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| [AnimatableArithmetic\<T\>](#animatablearithmetict) | Result of the subtraction operation, used to calculate the data difference during the animation interpolation process to obtain intermediate frame data. |

### multiply

multiply(scale: number): AnimatableArithmetic\<T\>

Defines the multiplication operation rule for this data type. In the animation interpolation operation, it is used to scale the difference according to the animation progress ratio (between 0 and 1), and the scaled difference is added to the start value through the plus operation. It must be implemented together with the other methods of the AnimatableArithmetic\<T\> interface to enable the custom data type to participate in the animation interpolation operation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                               | Mandatory| Description                                   |
| ----- | --------------------------------- | ---- | ------------------------------------- |
| scale | number | Yes    | Coefficient of the multiplication operation. The value range is [0, +∞), and the typical value range during animation interpolation is [0, 1].                           |

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| [AnimatableArithmetic\<T\>](#animatablearithmetict) | Result of the multiplication operation, used to scale data by a coefficient during the animation interpolation process to calculate intermediate frame data. |

### equals

equals(rhs: AnimatableArithmetic\<T\>): boolean

Defines the equality check rule for this data type. During the animation process, it is used to identify whether the data has changed. If the current value is equal to the target value, the animation transition is no longer triggered. It must be implemented together with the other methods of the **AnimatableArithmetic\<T\>** API to enable the custom data type to participate in the animation interpolation operation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                               | Mandatory| Description                                   |
| ----- | --------------------------------- | ---- | ------------------------------------- |
| rhs | [AnimatableArithmetic\<T\>](#animatablearithmetict) | Yes | The other data object to compare with the current object for equality. |

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| boolean | Whether the objects are equal. Returns **true** if they are equal; returns **false** otherwise. |

## Example

### Example 1: Implementing a Frame-by-Frame Layout Effect

The following example implements the frame-by-frame layout effects by changing the width of the **Text** component.

```ts
@AnimatableExtend(Text)
function animatableWidth(width: number) {
  .width(width)
}

@Entry
@Component
struct AnimatablePropertyExample {
  @State textWidth: number = 80;

  build() {
    Column() {
      Text("AnimatableProperty")
        .animatableWidth(this.textWidth)
        .animation({ duration: 2000, curve: Curve.Ease })
      Button("Play")
        .onClick(() => {
          this.textWidth = this.textWidth === 80 ? 160 : 80;
        })
    }.width("100%")
    .padding(10)
  }
}
```

![animatableExtend](figures/AnimatableProperty.gif)

### Example 2: Implementing a Polyline Animation Effect

The following example implements a polyline animation effect.

```ts
class Point {
  x: number
  y: number

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }

  plus(rhs: Point): Point {
    return new Point(this.x + rhs.x, this.y + rhs.y);
  }

  subtract(rhs: Point): Point {
    return new Point(this.x - rhs.x, this.y - rhs.y);
  }

  multiply(scale: number): Point {
    return new Point(this.x * scale, this.y * scale);
  }

  equals(rhs: Point): boolean {
    return this.x === rhs.x && this.y === rhs.y;
  }
}

// PointVector implements the AnimatableArithmetic<T> API.
class PointVector extends Array<Point> implements AnimatableArithmetic<PointVector> {
  constructor(value: Array<Point>) {
    super();
    value.forEach(point => this.push(point));
  }

  plus(rhs: PointVector): PointVector {
    let result = new PointVector([]);
    const len = Math.min(this.length, rhs.length);
    for (let i = 0; i < len; i++) {
      result.push((this as Array<Point>)[i].plus((rhs as Array<Point>)[i]));
    }
    return result;
  }

  subtract(rhs: PointVector): PointVector {
    let result = new PointVector([]);
    const len = Math.min(this.length, rhs.length);
    for (let i = 0; i < len; i++) {
      result.push((this as Array<Point>)[i].subtract((rhs as Array<Point>)[i]));
    }
    return result;
  }

  multiply(scale: number): PointVector {
    let result = new PointVector([]);
    for (let i = 0; i < this.length; i++) {
      result.push((this as Array<Point>)[i].multiply(scale));
    }
    return result;
  }

  equals(rhs: PointVector): boolean {
    if (this.length !== rhs.length) {
      return false;
    }
    for (let i = 0; i < this.length; i++) {
      if (!(this as Array<Point>)[i].equals((rhs as Array<Point>)[i])) {
        return false;
      }
    }
    return true;
  }

  get(): Array<Object[]> {
    let result: Array<Object[]> = [];
    this.forEach(point => result.push([point.x, point.y]));
    return result;
  }
}

@AnimatableExtend(Polyline)
function animatablePoints(points: PointVector) {
  // Convert PointVector to the array format required by the points attribute of Polyline.
  .points(points.get())
}

@Entry
@Component
struct AnimatablePropertyExample {
  @State points: PointVector = new PointVector([
    new Point(50, Math.random() * 200),
    new Point(100, Math.random() * 200),
    new Point(150, Math.random() * 200),
    new Point(200, Math.random() * 200),
    new Point(250, Math.random() * 200),
  ])

  build() {
    Column() {
      Polyline()
        .animatablePoints(this.points)
        .animation({ duration: 1000, curve: Curve.Ease }) // Set the animation parameters.
        .size({ height: 220, width: 300 })
        .fill(Color.Green)
        .stroke(Color.Red)
        .backgroundColor('#eeaacc')
      Button("Play")
        .onClick(() => {
          // points is a data type that implements the animation protocol. During the animation, points can be changed from the previous PointVector data to the new one based on the defined operation rules and animation parameters to generate the PointVector data of each frame and then generate an animation.
          this.points = new PointVector([
            new Point(50, Math.random() * 200),
            new Point(100, Math.random() * 200),
            new Point(150, Math.random() * 200),
            new Point(200, Math.random() * 200),
            new Point(250, Math.random() * 200),
          ]);
        })
    }.width("100%")
    .padding(10)
  }
}
```

![image](figures/animatable-points.gif)