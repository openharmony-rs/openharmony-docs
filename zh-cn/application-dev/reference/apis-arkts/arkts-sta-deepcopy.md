# Deepcopy (深拷贝)
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供对象与集合的深拷贝能力。开发者可以使用`deepcopy`对值进行递归复制；对于无默认构造函数的类实例，可通过实现`Cloneable`接口并在子类中重写`clone`方法来自定义拷贝逻辑。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## Cloneable

标记对象支持通过`clone`方法完成拷贝的接口。当实例类型实现了`Cloneable`时，`deepcopy`会优先采用`clone`分支：类必须在类型上声明并重写实例方法`clone`，否则会在运行时抛出错误。

子类继承父类且父类或子类未正确重写`clone`时，同样可能在运行时失败，因此请在继承链上按需实现`clone`。


### clone

clone(): Cloneable

克隆当前对象，返回一个新的`Cloneable`实例。具体类型应返回与自身一致的具体类型（例如子类`clone`返回子类实例）。

**返回值：**

| 类型       | 说明           |
| ---------- | -------------- |
| Cloneable  | 拷贝后的对象。 |

**示例：**

```ts
class Point implements Cloneable {
    x: int;
    y: int;

    constructor(x: int, y: int) {
        this.x = x;
        this.y = y;
    }

    clone(): Point {
        return new Point(this.x, this.y);
    }
}

let p: Point = new Point(1, 2);
let q: Point = deepcopy(p) as Point;
console.info(q.x); // 1
```


## deepcopy

deepcopy\<T\>(src: T \| null \| undefined, depth?: int): T \| null \| undefined

对`src`进行深拷贝。`null`与`undefined`将原样返回。内置包装类型、`Array`、`Set`、`Map`、`Date`、枚举以及带默认构造函数的普通对象等按实现规则递归复制。若对象图中存在循环引用（例如两个对象互相引用），拷贝过程会记录已生成的副本：再次遇到同一源对象时直接复用该副本，而不会重复向下递归，从而避免无限循环。`Function`不进行内容克隆，返回与源相同的函数引用。

**参数：**

| 参数名  | 类型                         | 必填 | 说明                                                                 |
| ------- | ---------------------------- | ---- | -------------------------------------------------------------------- |
| src     | T \| null \| undefined       | 是   | 需要深拷贝的数据。                                                   |
| depth   | int                          | 否   | 递归复制的最大深度，默认值为**-1**，表示不限制深度（内部按最大整型深度处理）。 |

**depth取值与含义：**

| depth 取值 | 说明 |
| ---------- | ---- |
| **-1** | 对所有嵌套结构尽可能深拷贝（直至不支持的类型或实现限制）。 |
| **≥0** | 从根对象起每进入一层嵌套对象或集合计一层；超过该深度时，该层及更深层可能保留原引用而非继续克隆，用于限制拷贝深度。 |

**返回值：**

| 类型                   | 说明                 |
| ---------------------- | -------------------- |
| T \| null \| undefined | 深拷贝结果，类型与输入一致（含null与undefined）。 |

**拷贝行为说明：**

> **说明：**
>
> - 本节说明不同类别输入在拷贝时的处理方式；返回值形态见上文「返回值」一节，始终为`T \| null \| undefined`，与入参的可空形态一致。
>
> - 若对象之间存在引用关系，且形成的结构中存在循环引用，已拷贝过的源对象会与其副本建立对应关系；再次遍历到同一源对象时复用该副本，避免无限递归。
>
> - 当参数为`null`或`undefined`时，直接返回相同取值。
>
> - `String`不可变，返回与源相同的引用；`Boolean`、`Byte`、`Char`、`Short`、`Int`、`Long`、`Float`、`Double`等包装类型通过对应`valueOf`生成新实例；继承`BaseEnum`的枚举返回同一枚举引用。
>
> - `Date`使用拷贝构造得到新实例。
>
> - `Array`、`Set`、`Map`会新建容器并递归拷贝元素；`Map`的键与值均会递归拷贝。`FixedArray`在超过深度限制时可能返回原数组，否则按元素类型递归拷贝或`copyOf`。
>
> - `Function`返回原函数引用。
>
> - 若实例实现了`Cloneable`，且类型上存在重写的`clone`方法，则调用`clone()`；否则抛出错误。
>
> - 其余`Object`在具备无参默认构造函数时，先创建实例，再按继承链上的实例字段逐个递归赋值；若类无默认构造函数，须实现`Cloneable`并提供`clone`，否则会抛出错误。
>
> - 若源类型不被支持，将抛出`Error`，消息中可能包含*unsupported source object type*。

**示例 1：嵌套对象**

外层与内层均为带默认构造函数的类时，`deepcopy`会递归拷贝：修改源对象上的嵌套实例，不会影响拷贝结果中的对应字段。

```ts
class Part {
    label: string = "";
    constructor() {}
}

class Container {
    part: Part = new Part();
    constructor() {}
}

let c: Container = new Container();
c.part.label = "a";

let cCopy: Container = deepcopy(c) as Container;
c.part.label = "b";

console.info(c.part.label);     // b
console.info(cCopy.part.label); // a
```

**示例 2：限制拷贝深度**

```ts
class Tag {
    val: string = "";
    constructor() {}
}

class Node {
    id: int = 0;
    tag: Tag | undefined = undefined;
    constructor() {}
}

let n: Node = new Node();
n.id = 1;
const tag: Tag = new Tag();
tag.val = "x";
n.tag = tag;

// 深度为1：根对象新建，下一层字段可能仍为共享引用
let shallow: Node | null | undefined = deepcopy<Node>(n, 1);
// 深度为0：直接返回原对象引用
let same: Node | null | undefined = deepcopy<Node>(n, 0);
```

**错误处理：**

> **说明：**
>
> - 不符合拷贝条件时，实现可能抛出`Error`。
>
> - 请在业务侧使用try/catch处理，或事先保证类型满足拷贝前提。
>
> - 源对象类型不被实现支持时可能抛出。
>
> - 类实现了`Cloneable`但未在类型上提供可识别的`clone`重写时可能抛出。
>
> - 普通类既无无参默认构造函数、又未通过`Cloneable`提供拷贝路径时可能抛出。

**示例 3：错误捕获**

子类若实现了`Cloneable`（例如继承自已实现`Cloneable`的父类），但未在本类上重写`clone`，`deepcopy`会在运行时抛出错误：

```ts
class Base implements Cloneable {
    x: int = 0;
    constructor() {}
    clone(): Base {
        let b: Base = new Base();
        b.x = this.x;
        return b;
    }
}

class Child extends Base {
    y: int = 0;
    constructor() {
        super();
    }
    // 未重写 clone
}

try {
    let c: Child = new Child();
    deepcopy(c);
} catch (error) {
    console.error(error.message); // 例如：class ... doesn't override clone
}
```