# \@Param：组件外部输入
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->


为了增强子组件接受外部参数输入的能力，开发者可以使用\@Param装饰器。


\@Param不仅可以接受组件外部输入，还可以接受\@Local的同步变化。在阅读本文档前，建议提前阅读：[\@Local](./arkts-new-local.md)。

> **说明：**
>
> 从API version 12开始，在\@ComponentV2装饰的自定义组件中支持使用\@Param装饰器。
>
> 从API version 12开始，该装饰器支持在原子化服务中使用。

## 概述

\@Param表示组件从外部传入的状态，使得父子组件之间的数据能够进行同步：

- \@Param装饰的变量支持本地初始化，但不允许在组件内部直接修改。

- 被\@Param装饰的变量能够在初始化自定义组件时从外部传入，当数据源也是状态变量时，数据源的修改会同步给\@Param。
- \@Param可以接受任意类型的数据源，包括普通变量、状态变量、常量、函数返回值等。
- \@Param装饰的变量变化时，会刷新该变量关联的组件。
- \@Param支持对基本类型（如number、boolean、string、Object、class）、内嵌类型（如[Array](#装饰array类型变量)、[Set](#装饰set类型变量)、[Map](#装饰map类型变量)、[Date](#装饰date类型变量)），以及null、undefined和[联合类型](#联合类型)进行观测。
- 对于复杂类型如类对象，\@Param会接受数据源的引用。在组件内可以修改类对象中的属性，该修改会同步到数据源。
- \@Param的观测能力仅限于被装饰的变量本身。详见[观察变化](#观察变化)。


## 状态管理V1版本接受外部传入的装饰器的局限性
状态管理V1存在多种可接受外部传入的装饰器，常用的有[\@State](arkts-state.md)、[\@Prop](arkts-prop.md)、[\@Link](arkts-link.md)、[\@ObjectLink](arkts-observed-and-objectlink.md)。这些装饰器使用有限制且不易区分，不当使用会导致性能问题。

<!-- @[Param_Decorator_Limitations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamDecoratorLimitations.ets) -->

``` TypeScript
@Observed
class Region {
  public x: number;
  public y: number;

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

@Observed
class Info {
  public region: Region;

  constructor(x: number, y: number) {
    this.region = new Region(x, y);
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info(0, 0);

  build() {
    Column() {
      Button('change Info')
        .onClick(() => {
          this.info = new Info(100, 100);
        })
      Child({
        region: this.info.region,
        regionProp: this.info.region,
        infoProp: this.info,
        infoLink: this.info,
        infoState: this.info
      })
    }
  }
}

@Component
struct Child {
  @ObjectLink region: Region;
  @Prop regionProp: Region;
  @Prop infoProp: Info;
  @Link infoLink: Info;
  @State infoState: Info = new Info(1, 1);

  build() {
    Column() {
      Text(`ObjectLink region: ${this.region.x}-${this.region.y}`)
      Text(`Prop regionProp: ${this.regionProp.x}-${this.regionProp.y}`)
    }
  }
}
```

在上面的示例中，\@State仅能在初始化时接收info的引用，改变info之后无法同步。\@Prop虽然能够进行单向同步，但是对于较复杂的类型来说，深拷贝性能较差。\@Link能够接受传入的引用进行双向同步，但它必须要求数据源也是状态变量，因此无法接受info中的成员属性region。\@ObjectLink能够接受类成员属性，但是要求该属性类型必须为\@Observed装饰的类。装饰器的不同限制使得父子组件之间的传值规则复杂、不易使用。因此推出\@Param装饰器，表示组件从外部传入的状态。

## 装饰器说明

| \@Param变量装饰器  | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| 装饰器参数         | 无。                                                         |
| 能否本地修改       | 否。若需要修改值，可使用\@Param搭配[\@Once](./arkts-new-once.md)修改子组件的本地值。或通过[\@Event](./arkts-new-event.md)装饰器，修改\@Param数据源的值。|
| 同步类型           | 由父到子单向同步。                                           |
| 允许装饰的变量类型 | Object、class、string、number、boolean、enum等基本类型以及Array、Date、Map、Set等内嵌类型。支持null、undefined以及联合类型。 |
| 被装饰变量的初始值 | 允许本地初始化，若不在本地初始化，则需要和[\@Require](./arkts-require.md)装饰器一起使用，要求必须从外部传入初始化。 |

## 变量传递

| 传递规则       | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| 从父组件初始化 | \@Param装饰的变量允许本地初始化，若无本地初始化则必须从外部传入初始化。当同时存在本地初始值与外部传入值时，优先使用外部传入值进行初始化。 |
| 初始化子组件   | \@Param装饰的变量可以初始化子组件中\@Param装饰的变量。       |
| 同步           | \@Param可以和父组件传入的状态变量数据源（即\@Local或\@Param装饰的变量）进行同步，当数据源发生变化时，会将修改同步给子组件的\@Param。 |

## 观察变化

使用\@Param装饰的变量具有被观测变化的能力。当装饰的变量发生变化时，会触发该变量绑定的UI组件刷新。

- 当装饰的变量类型为boolean、string、number类型时，可观察数据源同步变化。

 <!-- @[Param_Observe_Change_Variable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamObserveChangeVariable.ets) -->
 
 ``` TypeScript
 @Entry
 @ComponentV2
 struct Index {
   // 点击的次数
   @Local count: number = 0;
   @Local message: string = 'Hello';
   @Local flag: boolean = false;
 
   build() {
     Column() {
       Text(`Local ${this.count}`)
       Text(`Local ${this.message}`)
       Text(`Local ${this.flag}`)
       Button('change Local')
         .onClick(() => {
           // 对数据源的更改会同步给子组件
           this.count++;
           this.message += ' World';
           this.flag = !this.flag;
         })
       Child({
         count: this.count,
         message: this.message,
         flag: this.flag
       })
     }
   }
 }
 
 @ComponentV2
 struct Child {
   @Require @Param count: number;
   @Require @Param message: string;
   @Require @Param flag: boolean;
 
   build() {
     Column() {
       Text(`Param ${this.count}`)
       Text(`Param ${this.message}`)
       Text(`Param ${this.flag}`)
     }
   }
 }
 ```

- 当装饰的变量类型为类对象时，仅可以观察到对类对象整体赋值的变化，无法直接观察到对类成员属性赋值的变化，对类成员属性的观察依赖[\@ObservedV2](arkts-new-observedV2-and-trace.md)和[\@Trace](arkts-new-observedV2-and-trace.md)装饰器。

 <!-- @[Param_Observe_Change_Class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamObserveChangeClass.ets) -->

- 装饰的变量为简单类型数组时，可观察数组整体或数组项变化。

<!-- @[Param_Observe_Change_Array](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamObserveChangeArray.ets) -->

- 当装饰的变量是嵌套类或对象数组时，\@Param无法观察深层对象属性的变化。对深层对象属性的观测依赖\@ObservedV2与\@Trace装饰器。

<!-- @[Param_Observe_Change_Nested_Class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamObserveChangeNestedClass.ets) -->

- 装饰的变量为内置类型时，可观察变量整体赋值和API调用的变化。

  | 类型  | 可观测变化的API                                              |
      | ----- | ------------------------------------------------------------ |
  | Array | push, pop, shift, unshift, splice, copyWithin, fill, reverse, sort |
  | Date  | setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime, setUTCFullYear, setUTCMonth, setUTCDate, setUTCHours, setUTCMinutes, setUTCSeconds, setUTCMilliseconds |
  | Map   | set, clear, delete                                           |
  | Set   | add, clear, delete                                           |

## 限制条件

\@Param装饰器存在以下使用限制：

- \@Param装饰器只能在[\@ComponentV2](arkts-new-componentV2.md)装饰器的自定义组件中使用。

<!-- @[Param_Restrict_V2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamRestrictV2.ets) -->

- \@Param装饰的变量表示组件外部输入，需要初始化。支持使用本地初始值或外部传入值进行初始化。当存在外部传入值时，优先使用外部传入值。不允许既不使用本地初始值，也不使用外部传入值。

<!-- @[Param_Restrict_Initialize](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamRestrictInitialize.ets) -->

- 使用`@Param`装饰的变量在子组件中无法被直接修改。但是，如果装饰的变量是对象类型，在子组件中可以修改对象的属性。

<!-- @[Param_Restrict_Modify_Object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamRestrictModifyObject.ets) -->

## 使用场景

### 从父组件到子组件变量传递与同步

\@Param能够接受父组件\@Local或\@Param传递的数据并与之变化同步。

<!-- @[Param_Use_Scene_Parent_To_Child](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamUseSceneParentToChild.ets) -->

### 装饰Array类型变量
\@Param装饰Array类型变量，可以观察到数据源对Array整体的赋值，以及调用Array的接口`push`, `pop`, `shift`, `unshift`, `splice`, `copyWithin`, `fill`, `reverse`, `sort`带来的变化。

<!-- @[Param_Use_Scene_Array](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamUseSceneArray.ets) -->

### 装饰Date类型变量

\@Param装饰Date类型变量，可以观察到数据源对Date整体的赋值，以及调用Date的接口`setFullYear`, `setMonth`, `setDate`, `setHours`, `setMinutes`, `setSeconds`, `setMilliseconds`, `setTime`, `setUTCFullYear`, `setUTCMonth`, `setUTCDate`, `setUTCHours`, `setUTCMinutes`, `setUTCSeconds`, `setUTCMilliseconds`带来的变化。

<!-- @[Param_Use_Scene_Date](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamUseSceneDate.ets) -->

### 装饰Map类型变量

\@Param装饰Map类型变量，可以观察到数据源对Map整体的赋值，以及调用Map的接口`set`, `clear`, `delete`带来的变化。

<!-- @[Param_Use_Scene_Map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamUseSceneMap.ets) -->

### 装饰Set类型变量

\@Param装饰Set类型变量，可以观察到数据源对Set整体的赋值，以及调用Set的接口`add`, `clear`, `delete`带来的变化。

<!-- @[Param_Use_Scene_Set](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamUseSceneSet.ets) -->

### 联合类型

\@Param支持null、undefined以及联合类型。以下示例中，count类型为number | undefined，点击改变count的类型时，UI会自动刷新。

<!-- @[Param_Use_Scene_Unite](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/param/ParamUseSceneUnite.ets) -->