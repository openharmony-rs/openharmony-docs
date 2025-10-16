# applySync/flushUpdates/flushUIUpdates接口：同步刷新

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

为了实现状态管理V2与animateTo等动效的同步刷新，开发者可以使用applySync、flushUpdates或flushUIUpdates接口。

> **说明：**
>
> 从API version 22开始，开发者可以使用UIUtils中的applySync、flushUpdates和flushUIUpdates接口实现状态管理V2的同步标脏。



## 概述

与状态管理V1不同的是，状态管理V2修改完状态变量后不会立即标脏，而是抛出一个Promise微任务（优先级低于宏任务），该微任务在当前宏任务执行完成后才会处理自定义组件标脏。但是animateTo动效是立即执行闭包函数并触发FlushBuild，刷新脏节点。当动效中使用了状态变量，而此刻状态变量的变化尚未标脏，导致animateTo的首帧动效不符合预期。为此，引入applySync、flushUpdates和flushUIUpdates接口，实现状态管理V2的同步标脏，确保动效达到预期效果。

使用applySync/flushUpdates/flushUIUpdates接口需要导入UIUtils工具。

```ts
import { UIUtils } from '@kit.ArkUI';
```



## 使用规则

- applySync接口用于同步刷新指定的状态变量，该接口接收一个闭包函数，仅刷新闭包函数内的修改，包括更新@Computed计算、@Monitor回调以及重新渲染UI节点。

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local w: number = 50; // 宽度
    @Local h: number = 50; // 高度
    @Local message: string = 'Hello';
  
    build() {
      Column() {
        Button('change size')
          .margin(20)
          .onClick(() => {
            // 在执行动画前，存在额外的修改
            UIUtils.applySync(() => {
              this.w = 100;
              this.h = 100;
              this.message = 'Hello World';
            })
  
            animateTo({
              duration: 1000
            }, () => {
              console.log(`pikalov2 in-animateTo(in ) this.w=${this.w}, h=${this.h}`)
              this.w = 200;
              this.h = 200;
              this.message = 'Hello ArkUI';
              console.log(`pikalov2 in-animateTo(out ) this.w=${this.w}, h=${this.h}`)
            })
          })
        Column() {
          Text(`${this.message}`)
        }
        .backgroundColor('#ff17a98d')
        .width(this.w)
        .height(this.h)
      }
    }
  }
  ```

- flushUpdates接口用于同步刷新在调用该函数之前所有的状态变量修改，包括更新@Computed计算、@Monitor回调以及重新渲染UI节点。

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local w: number = 50; // 宽度
    @Local h: number = 50; // 高度
    @Local message: string = 'Hello';
  
    build() {
      Column() {
        Button('change size')
          .margin(20)
          .onClick(() => {
            // 在执行动画前，存在额外的修改
            this.w = 100;
            this.h = 100;
            this.message = 'Hello World';
            UIUtils.flushUpdates();
  
            animateTo({
              duration: 1000
            }, () => {
              console.log(`pikalov2 in-animateTo(in ) this.w=${this.w}, h=${this.h}`)
              this.w = 200;
              this.h = 200;
              this.message = 'Hello ArkUI';
              console.log(`pikalov2 in-animateTo(out ) this.w=${this.w}, h=${this.h}`)
            })
          })
        Column() {
          Text(`${this.message}`)
        }
        .backgroundColor('#ff17a98d')
        .width(this.w)
        .height(this.h)
      }
    }
  }
  ```

- flushUIUpdates接口用于同步刷新在调用该函数之前所有的UI节点。

## 限制条件

- 在applySync闭包函数中调用flushUpdates或flushUIUpdates接口，这两个接口会被跳过，不起作用。

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local w: number = 50; // 宽度
    @Local h: number = 50; // 高度
  
    build() {
      Column() {
        Button('change size')
          .margin(20)
          .onClick(() => {
            // 在执行动画前，存在额外的修改
            UIUtils.applySync(() => {
              this.w = 100;
              UIUtils.flushUpdates(); // 在applySync中，flushUpdates被忽略
              UIUtils.flushUIUpdates(); // 在applySync中，flushUIUpdates被忽略
            })
            this.h = 100;
            UIUtils.flushUpdates(); //会生效
  
            animateTo({
              duration: 1000
            }, () => {
              console.log(`pikalov2 in-animateTo(in ) this.w=${this.w}, h=${this.h}`)
              this.w = 200;
              this.h = 200;
              console.log(`pikalov2 in-animateTo(out ) this.w=${this.w}, h=${this.h}`)
              // 第二处增加
            })
          })
        Column() {
          Text(`BOX`)
        }
        .backgroundColor('#ff17a98d')
        .width(this.w)
        .height(this.h)
      }
    }
  }
  ```

- 不支持在@Computed装饰的getter方法中调用applySync、flushUpdates和flushUIUpdates接口，否则运行时会报错。

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Page {
    @Local firstName: string = 'Hua';
    @Local lastName: string = 'Li';
    @Local count: number = 0;
  
    @Computed
    get fullName() {
      // 在computed中调用applySync、flushUpdates、flushUIUpdates运行时报错
      UIUtils.flushUIUpdates();
      UIUtils.flushUpdates();
      UIUtils.applySync(() => {
        this.count++;
      })
      return this.firstName + ' ' + this.lastName;
    }
  
    build() {
      Column() {
        Text(`${this.fullName}`)
        Text(`${this.count}`)
        Button('change fullName').onClick(() => {
          this.firstName = 'Zhang';
          this.lastName = 'San';
        })
      }
    }
  }
  ```

在@Computed中调用applySync、flushUpdates和flushUIUpdates接口时，会抛出`The function is not allowed to be called in @Computed`错误信息。

- 不支持在@Monitor回调函数中调用flushUpdates和flushUIUpdates接口，否则运行时会报错。

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  
  @Entry
  @ComponentV2
  struct Page {
    @Local count: number = 0;
    @Monitor('count')
    onCountChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
      UIUtils.flushUpdates(); // 在monitor中调用flushUpdates会运行时报错
      UIUtils.flushUIUpdates(); // 在monitor中调用flushUIUpdates会运行时报错
  
    }
  
    build() {
      Column() {
        Text(`${this.count}`)
        Button('change count').onClick(() => {
          this.count++;
        })
      }
    }
  }
  ```

在@Monitor回调函数中调用flushUpdates和flushUIUpdates接口会抛出错误信息`The function is not allowed to be called in @Monitor`。

## 使用场景

### 动效场景

在animateTo前修改状态变量`wid`，触发了onSizeChange事件，带入动画中，产生背景色的无限循环动画。

```ts
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Example {
  @Local rotateAngle:number=0
  @Local wid:number=100
  @Local color:Color=Color.Red

  build(){
    Column(){
      Column()
        .size({width:100,height:100})
        .backgroundColor(this.color)
      Button('animate')
        .margin(50)
        .width(this.wid)
        .rotate({x:0,y:0,z:1,angle:this.rotateAngle})
        .onSizeChange((oldValue:SizeOptions,newValue:SizeOptions)=>{
          if(Number(newValue.width)>=150){
            this.color=Color.Blue;
          }else{
            this.color=Color.Red;
          }
        })
        .onClick(()=>{
          UIUtils.applySync(() => {
            this.wid=200;
          })

          animateTo({
            iterations:-1,//设置-1表示动画无限循环
            playMode:PlayMode.Alternate,
          },()=>{
            this.rotateAngle=90
          })
        })
    }.width('100%').margin({top:5})
  }
}
```

### 路由场景

```ts
// Index.ets

import { UIUtils } from '@ohos.arkui.StateManagement';
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2 class  Info {
  @Trace id : string = "";
}

@Entry
@ComponentV2
struct SharedTransitionExample {
  @Local info : Info = AppStorageV2.connect(Info, () => new Info())!

  build() {
    Column() {
      Image($r('app.media.startIcon')).width(50).height(50).margin({ left: 20, top: 20 })
        .sharedTransition(this.info.id, { duration: 800, curve: Curve.Linear, delay: 100 })
    }.width('100%').height('100%').alignItems(HorizontalAlign.Start)
    .onClick(() => {
      UIUtils.applySync(() => {
        this.info.id = "id1"; // 不匹配
      })
      this.getUIContext().getRouter().pushUrl({ url: 'pages/PageTransitionTwo' })
    })
  }
}
```

```ts
// PageTransitionTwo.ets

import { UIUtils } from '@ohos.arkui.StateManagement';
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2 class  Info {
  @Trace id : string = "";
}

@Entry
@ComponentV2
struct pageBExample {
  build() {
    Stack() {
      Image($r('app.media.startIcon')).width(150).height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
        .onClick(()=>{
          UIUtils.applySync(() => {
            AppStorageV2.connect(Info, () => new Info())!.id = "sharedImage"
          })

          this.getUIContext().getRouter().back();
        })
    }.width('100%').height('100%')
  }
}
```

在从Index页面跳转到PageTransitionTwo页面时，id不匹配，图标没有动画。在从PageTransitionTwo页面返回Index页面是，id匹配，图标动效正常。

### 在addMonitor异步刷新中调用同步刷新接口

```ts
import { UIUtils } from '@ohos.arkui.StateManagement';

@Entry
@ComponentV2
struct Index {
  @Local local: string = '1';
  onLocalChange(): void {
    console.info(`onLocalChange ${this.local}`);
  }
  aboutToAppear(): void {
    UIUtils.addMonitor(this, ['local'], this.onLocalChange, {isSynchronous: false});
  }
  build() {
    Column() {
      Button('change')
        .onClick((e: ClickEvent) => {
          this.local += '1';
          this.local += '1';
          UIUtils.flushUpdates();
          this.local += '2';
          this.local += '2';
        })
    }
  }
}
```

addMonitor打开异步刷新后，在一次点击事件中多次修改状态变量，只会触发一次回调。但如果在多次修改过程中调用flushUpdates接口，则之前的修改将会同步刷新。因此，在上述代码中，每次点击按钮都会打印两条日志。