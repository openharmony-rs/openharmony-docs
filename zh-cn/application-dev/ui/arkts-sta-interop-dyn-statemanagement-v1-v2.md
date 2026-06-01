# ArkTS-Sta与ArkTS-Dyn状态管理V1V2混用互操作校验规格
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lixingchi1; @katabanga-->
<!--Designer: @lixingchi1; @katabanga-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

## 概述
从API version 23开始，在ArkTS-Sta与ArkTS-Dyn互操作中，增加状态管理V1V2混用时的编译校验规格，解决兼容性问题并保证应用稳定性和数据可靠性。

互操作时，\@Component与\@ComponentV2不可跨ArkTS-Dyn与ArkTS-Sta混用。具体校验规格如下表所示。

**ArkTS-Dyn调用ArkTS-Sta自定义组件混用规格**

| 父组件 | 子组件 | 是否支持 |
|---|---|---|
| \@Component | \@Component | 支持 |
| \@Component | \@ComponentV2 | 不支持（编译报错） |
| \@ComponentV2 | \@ComponentV2 | 支持 |
| \@ComponentV2 | \@Component | 不支持（编译报错） |

**ArkTS-Sta调用ArkTS-Dyn自定义组件混用规格**

| 父组件 | 子组件 | 是否支持 |
|---|---|---|
| \@Component | \@Component | 支持 |
| \@Component | \@ComponentV2 | 不支持（编译报错） |
| \@ComponentV2 | \@ComponentV2 | 支持 |
| \@ComponentV2 | \@Component | 不支持（编译报错） |

**变量装饰器混用规格**

| 自定义组件装饰器 | 变量由\@Observed装饰的class初始化 | 变量由\@ObservedV2装饰的class初始化 |
|---|---|---|
| \@Component | 支持 | 不支持（编译报错） |
| \@ComponentV2 | 不支持（编译报错） | 支持 |

## 使用场景

下文结合用例说明互操作时状态管理V1与V2混用的编译报错场景。

### ArkTS-Dyn调用ArkTS-Sta

ArkTS-Dyn调用ArkTS-Sta，父组件V2调用子组件V1示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录进行子组件构建。

  ```ts
  'use static'

  // static_module/src/main/ets/components/MainPage.ets
  import { Text, Column, Component, Row } from '@ohos.arkui.component';
  import { State, Observed } from '@ohos.arkui.stateManagement';

  @Component
  export struct MainPage {
    @State schoolName: string = '高中';
    @State className: string = '三年四班';

    build() {
      Row() {
        Column() {
          Text(this.schoolName)
          .fontSize(30);
          Text(this.className)
          .fontSize(30);
        }
      }
    }
  }

  @Observed
  export class Book {
    private bookName: string = '中学语文';

    constructor(bookName: string) {
      this.bookName = bookName;
    }
  }
  ```

- 对ArkTS-Sta子模块`static_module/Index.ets`文件中的数据模型进行导出。

  ```TypeScript
  'use static'

  // static_module/Index.ets
  export { MainPage, Book } from './src/main/ets/components/MainPage';
  ```

- 在主模块的`entry/oh-package.json5`文件中配置子模块依赖。

  ```json5
  // entry/oh-package.json5

  "dependencies": {
    // 从根目录导入依赖模块
    "static_module": "file:../static_module",
  }
  ```

- 在ArkTS-Dyn主模块的`entry/src/main/ets/pages/Index.ets`文件中进行互操作。

  ```ts
  import { MainPage, Book } from 'static_module';

  @Entry
  @ComponentV2
  struct Index {
    // ArkTS-Dyn中V2变量由ArkTS-Sta中@Observed装饰的class实例化，编译报错
    firstBook: Book = new Book('中学语文');
    @Local secondBook: Book = new Book('中学数学');

    schoolName: string = '高中';
    @Local className: string = '四年三班';

    build() {
      Column(undefined) {
        Text('ArkTS-Dyn调用ArkTS-Sta').fontSize(40);
        // ArkTS-Dyn父组件V2调用ArkTS-Sta子组件V1，编译报错
        MainPage({
          schoolName: this.schoolName,
          className: this.className
        });
      }
    }
  }
  ```

上述示例中，存在以下编译报错：

1. ArkTS-Dyn中@ComponentV2的普通变量由ArkTS-Sta中@Observed装饰的class实例化，报错信息为：`The type of the regular property cannot be a class decorated with @Observed when interop.`
2. ArkTS-Dyn中@ComponentV2的@Local变量由ArkTS-Sta中@Observed装饰的class实例化，报错信息为：`The type of the @Local property can not be a class decorated with @Observed when interop.`
3. ArkTS-Dyn中@ComponentV2父组件调用ArkTS-Sta中@Component子组件，报错信息为：`The @Component 'MainPage' cannot be used in the @ComponentV2 'Index' when interop.`

### ArkTS-Sta调用ArkTS-Dyn

ArkTS-Sta调用ArkTS-Dyn，父组件V1调用子组件V2示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录进行子组件构建。

  ```ts
  // dynamic_module/src/main/ets/components/MainPage.ets
  @ComponentV2
  export struct MainPage {
    @Local schoolName: string = '高中';
    @Local className: string = '四年三班';

    build() {
      Row() {
        Column() {
          Text(this.schoolName)
          .fontSize(30);
          Text(this.className)
          .fontSize(30);
        }
      }
    }
  }

  @ObservedV2
  export class Book {
    private bookName: string = '中学语文';

    constructor(bookName: string) {
      this.bookName = bookName;
    }
  }
  ```

- 对ArkTS-Dyn子模块`dynamic_module/Index.ets`文件中的数据模型进行导出。

  ```TypeScript
  // dynamic_module/Index.ets

  export { MainPage, Book } from './src/main/ets/components/MainPage';
  ```

- 在主模块的`entry/oh-package.json5`文件中配置子模块依赖。

  ```json5
  // entry/oh-package.json5

  "dependencies": {
    // 从根目录导入依赖模块
    "dynamic_module": "file:../dynamic_module",
  }
  ```

- 在ArkTS-Sta主模块的`entry/src/main/ets/pages/Index.ets`文件中进行互操作。

  ```ts
  'use static'
  import { Entry, Text, Column, Component, Row, ComponentV2, State } from '@kit.ArkUI';
  import { MainPage, Book } from 'dynamic_module';

  @Entry
  @Component
  struct Index {
    // ArkTS-Sta中V1变量由ArkTS-Dyn中@ObservedV2装饰的class实例化，编译报错
    firstBook: Book = new Book('中学语文');
    @State secondBook: Book = new Book('中学数学');

    schoolName: string = '高中';
    @State className: string = '四年三班';

    build() {
      Column(undefined) {
        Text('ArkTS-Sta调用ArkTS-Dyn').fontSize(40);
        // ArkTS-Sta父组件V1调用ArkTS-Dyn子组件V2，编译报错
        MainPage({
          schoolName: this.schoolName,
          className: this.className,
        });
      }
    }
  }
  ```

上述示例中，存在以下编译报错：

1. ArkTS-Sta中@Component的普通变量由ArkTS-Dyn中@ObservedV2装饰的class实例化，报错信息为：`The type of the 'regular' property cannot be a class decorated with '@ObservedV2' when interop.`
2. ArkTS-Sta中@Component的@State变量由ArkTS-Dyn中@ObservedV2装饰的class实例化，报错信息为：`The type of the '@State' property cannot be a class decorated with '@ObservedV2' when interop.`
3. ArkTS-Sta中@Component父组件调用ArkTS-Dyn中@ComponentV2子组件，报错信息为：`The @ComponentV2 'MainPage' cannot be used in the @Component 'Index' when interop.`