# ArkTS-Sta与ArkTS-Dyn状态管理V1V2混用互操作校验规格

## 概述
从API version 23开始，在ArkTS-Sta与ArkTS-Dyn互操作中，增加状态管理V1V2混用时的编译校验规格，解决兼容性问题并保障应用稳定性和数据可靠性。

互操作时，状态管理V1与V2混用的校验规格如下：

- 互操作时，不允许在被\@Component装饰的ArkTS-Dyn组件中使用被\@ComponentV2装饰的ArkTS-Sta组件，否则编译将报错。

- 互操作时，不允许在被\@ComponentV2装饰的ArkTS-Dyn组件中使用被\@Component装饰的ArkTS-Sta组件，否则编译将报错。

- 互操作时，不允许在被\@Component装饰的ArkTS-Sta组件中使用被\@ComponentV2装饰的ArkTS-Dyn组件，否则编译将报错。

- 互操作时，不允许在被\@ComponentV2装饰的ArkTS-Sta组件中使用被\@Component装饰的ArkTS-Dyn组件，否则编译将报错。

## 开发场景

- ArkTS-Dyn与ArkTS-Sta互操作时，在被\@Component装饰的ArkTS-Dyn组件中使用被\@ComponentV2装饰的ArkTS-Sta组件，编译报错；在被\@Component装饰的组件内任何变量由\@ObservedV2装饰的class初始化，编译报错。

- ArkTS-Dyn与ArkTS-Sta互操作时，在被\@ComponentV2装饰的ArkTS-Dyn组件中使用被\@Component装饰的ArkTS-Sta组件，编译报错；在被\@ComponentV2装饰的组件内任何变量由\@Observed装饰的class初始化，编译报错。

- ArkTS-Sta与ArkTS-Dyn互操作时，在被\@Component装饰的ArkTS-Sta组件中使用被\@ComponentV2装饰的ArkTS-Dyn组件，编译报错；在被\@Component装饰的组件内任何变量由\@ObservedV2装饰的class初始化，编译报错。

- ArkTS-Sta与ArkTS-Dyn互操作时，在被\@ComponentV2装饰的ArkTS-Sta组件中使用被\@Component装饰的ArkTS-Dyn组件，编译报错；在被\@ComponentV2装饰的组件内任何变量由\@Observed装饰的class初始化，编译报错。

在ArkTS-Dyn中调用ArkTS-Sta时，父组件V2调用子组件V1示例如下：

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

  ```json
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
    // 若ArkTS-Dyn中V2的变量由ArkTS-Sta中@Observed装饰的class实例化，编译报错处理
    firstBook: Book = new Book('中学语文');
    @Local secondBook: Book = new Book('中学数学');

    schoolName: string = '高中';
    @Local className: string = '四年三班';

    build() {
      Column(undefined) {
        Text('ArkTS-Dyn调用ArkTS-Sta').fontSize(40);
        // 互操作时，父组件V2调用子组件V1，编译报错处理
        MainPage({
          schoolName: this.schoolName,
          className: this.className
        });
      }
    }
  }
  ```

在ArkTS-Sta中调用ArkTS-Dyn时，父组件V1调用子组件V2示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`static_module/src/main/ets/components`目录进行子组件构建。

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

  ```json
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
    // 若ArkTS-Sta中V1的变量由ArkTS-Dyn中@ObservedV2装饰的class实例化，编译都做报错处理
    firstBook: Book = new Book('中学语文');
    @State secondBook: Book = new Book('中学数学');

    schoolName: string = '高中';
    @State className: string = '四年三班';

    build() {
      Column(undefined) {
        Text('ArkTS-Sta调用ArkTS-Dyn').fontSize(40);
        // 互操作时，父组件V1的变量向子组件V2的变量传值，编译都做报错处理
        MainPage({
          schoolName: this.schoolName,
          className: this.className,
        });
      }
    }
  }
  ```