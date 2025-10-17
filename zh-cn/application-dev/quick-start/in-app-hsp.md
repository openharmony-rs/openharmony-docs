# HSP
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

HSP（Harmony Shared Package）是动态共享包，包含代码、C++库、资源和配置文件，通过HSP可以实现代码和资源的共享。HSP不支持独立发布上架，而是跟随宿主应用的APP包一起发布，与宿主应用同进程，具有相同的包名和生命周期。
> **说明：**
> 
> 应用内HSP：在编译过程中与应用包名（bundleName）强耦合，只能给某个特定的应用使用，本页面介绍应用内HSP。
> 
> [集成态HSP](integrated-hsp.md)：构建、发布过程中，不与特定的应用包名耦合；使用时，工具链支持自动将集成态HSP的包名替换成宿主应用包名，并且会重新签名生成一个新的HSP包，作为宿主应用的安装包，这个新的HSP也属于宿主应用HAP的应用内HSP。

## 使用场景
- 多个HAP/HSP共用的代码和资源放在同一个HSP中，可以提高代码、资源的可重用性和可维护性，同时编译打包时也只保留一份HSP代码和资源，能够控制应用包的大小。

- HSP在运行时[按需加载](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-modular-design#section28312051291)，有助于提升应用性能。

- 同一个组织内部的多个应用之间，可以使用集成态HSP实现代码和资源的共享。

## 约束限制

- HSP不支持在设备上单独安装/运行，需要与依赖该HSP的HAP一起安装/运行。在安装或更新时，多模块之间存在校验，详情参考[一致性校验](multi_module_installation_update_consistency_verification.md)。使用打包工具进行打包时，会进行合法性校验，详情请参考[打包工具](../../application-dev/tools/packing-tool.md)。
- 从API version 14开始HSP支持在配置文件中[声明UIAbility](../application-models/uiability-overview.md#声明配置)组件，但不支持具有入口能力的UIAbility（即skill标签配置了entity.system.home和ohos.want.action.home）。配置UIAbility的方法参考[模块中添加UIAbility](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-add-new-ability#section18658758104318)，HSP中UIAbility的启动方式与[应用内启动UIAbility](../application-models/uiability-intra-device-interaction.md)方法相同。API version 13及之前版本，不支持在配置文件中声明[UIAbility](../application-models/uiability-overview.md#声明配置)组件。
- 从API version 18开始HSP支持在配置文件中声明[ExtensionAbility](../application-models/extensionability-overview.md)组件，但不支持具有入口能力的ExtensionAbility（即skill标签配置了entity.system.home和ohos.want.action.home）。HSP中配置ExtensionAbility的方法参考[模块中添加ExtensionAbility](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-add-new-ability#section18891639459)。 API version 17及之前版本，不支持在配置文件中声明[ExtensionAbility](../application-models/extensionability-overview.md)组件。
- HSP可以依赖其他HAR或HSP，也可以被HAP或者HSP依赖集成，但不支持循环依赖，也不支持依赖传递。

> **说明：**
> 
> 循环依赖：例如有三个HSP，HSP-A、HSP-B和HSP-C，循环依赖指HSP-A依赖HSP-B，HSP-B依赖HSP-C，HSP-C又依赖HSP-A。
>
> 依赖传递：例如有三个HSP，HSP-A、HSP-B和HSP-C，依赖关系是HSP-A依赖HSP-B，HSP-B依赖HSP-C。不支持传递依赖指HSP-A可以使用HSP-B的方法和组件，但是HSP-A不能直接使用HSP-C的方法和组件。


## 创建
使用DevEco Studio创建一个用于调用C++代码的HSP模块。并在“Configure New Module”页面中启用“Enable native”选项。详见[创建HSP模块](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hsp#section7717162312546)，以创建一个名为`library`的HSP模块为例。基本的工程目录结构如下：
```
MyApplication
├── library
│   ├── src
│   │   └── main
|   |       ├── cpp
|   |       |   ├── CMakeLists.txt    //C++原生代码编译的配置文件 
|   |       |   └── napi_init.cpp     //NAPI模块初始化的C++文件
│   │       ├── ets
│   │       │   └── pages
│   │       │       └── index.ets     //模块library的页面文件
│   │       ├── resources             //模块library的资源目录
│   │       └── module.json5          //模块library的配置文件
│   ├── oh-package.json5              //模块级
│   ├── index.ets                     //入口文件index.ets
│   └── build-profile.json5           //模块级
└── build-profile.json5               //工程级
```

## 开发


介绍如何导出HSP的ArkUI组件、接口、资源，供应用内的其他HAP/HSP引用。

### 导出ArkUI组件
ArkUI组件可以通过`export`导出，例如：
<!-- @[in_app_hsp_001](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/src/main/ets/components/MyTitleBar.ets) -->
在入口文件 `index.ets` 中声明对外暴露的接口。
<!-- @[in_app_hsp_002](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/Index.ets) -->


### 导出类和方法
通过`export`导出类和方法，例如：

<!-- @[in_app_hsp_003](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/src/main/ets/utils/test.ets) -->
在入口文件 `index.ets` 中声明对外暴露的接口。

<!-- @[in_app_hsp_004](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/Index.ets) -->
### 导出native方法
在HSP中也可以包含C++编写的`so`。对于`so`中的`native`方法，HSP通过间接的方式导出，以导出`liblibrary.so`的乘法接口`multi`为例：

<!-- @[in_app_hsp_005](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/src/main/ets/utils/nativeTest.ets) -->

在入口文件 `index.ets` 中声明对外暴露的接口。

<!-- @[in_app_hsp_006](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/Index.ets) -->

### 通过$r访问HSP中的资源
在组件中，经常需要使用字符串、图片等资源。HSP中的组件需要使用资源时，一般将其所用资源放在HSP包内，而非放在HSP的使用方处，以符合高内聚低耦合的原则。

在工程中，常通过`$r`/`$rawfile`的形式引用应用资源。可以用`$r`/`$rawfile`访问本模块`resources`目录下的资源，如访问`resources`目录下定义的图片`src/main/resources/base/media/example.png`时，可以用`$r("app.media.example")`。有关`$r`/`$rawfile`的使用方式，请参阅文档[资源分类与访问](./resource-categories-and-access.md)中“资源访问-应用资源”小节。

不推荐使用相对路径的方式，容易引用错误路径。例如：
当要引用上述同一图片资源时，在HSP模块中使用`Image("../../resources/base/media/example.png")`，实际上该`Image`组件访问的是HSP调用方（如`entry`）下的资源`entry/src/main/resources/base/media/example.png`。


<!-- @[in_app_hsp_007](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/src/main/ets/pages/Index.ets) -->

### 导出HSP中的资源
跨包访问HSP内资源时，推荐实现一个资源管理类，以封装对外导出的资源。采用这种方式，具有如下优点：
- HSP开发者可以控制自己需要导出的资源，不需要对外暴露的资源可以不用导出。
- 使用方无须感知HSP内部的资源名称。当HSP内部的资源名称发生变化时，也不需要使用方跟着修改。

其具体实现如下：

将需要对外提供的资源封装为一个资源管理类：   

<!-- @[in_app_hsp_008](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/src/main/ets/ResManager.ets) -->

在入口文件 `index.ets` 中声明对外暴露的接口。

<!-- @[in_app_hsp_009](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/Index.ets) -->


## 使用

介绍如何引用HSP中的接口，以及如何通过页面路由实现HSP的pages页面跳转与返回。

### 引用HSP中的接口
要使用HSP中的接口，首先需要在使用方的 `oh-package.json5` 文件中配置对它的依赖。具体配置方法请参考[引用动态共享包](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-har-import)。
依赖配置成功后，就可以像使用HAR一样调用HSP的对外接口了。例如，上面的library已经导出了下面这些接口：

```ts
// library/index.ets
export { Log, add, minus } from './src/main/ets/utils/test';
export { MyTitleBar } from './src/main/ets/components/MyTitleBar';
export { ResManager } from './src/main/ets/ResManager';
export { nativeMulti } from './src/main/ets/utils/nativeTest';
```
<!-- @[in_app_hsp_010](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/library/Index.ets) -->
在使用方的代码中，可以这样使用：

<!-- @[in_app_hsp_011](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp1/entry/src/main/ets/pages/Index.ets) -->

### 页面跳转和返回

开发者想在entry模块中，添加一个按钮跳转至library模块中的menu页面（路径为：`library/src/main/ets/pages/library_menu.ets`），那么可以在使用方的代码（entry模块下的Index.ets，路径为：`entry/src/main/ets/pages/Index.ets`）里这样使用：

<!-- @[in_app_hsp_012](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp2/entry/src/main/ets/pages/Index.ets) -->

在library下新增page文件（library/src/main/ets/pages/library_menu.ets），其中'back_to_index'的按钮返回上一页。

<!-- @[in_app_hsp_014](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp2/library/src/main/ets/pages/library_menu.ets) -->

需要在library模块下新增route_map.json文件（library/src/main/resources/base/profile/route_map.json）。
```
{
  "routerMap": [
    {
      "name": "library_menu",
      "pageSourceFile": "src/main/ets/pages/library_menu.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is library_menu"
      }
    }
  ]
}
```

在library模块下的配置文件（library/src/main/module.json5）中配置json文件。

<!-- @[in_app_hsp_013](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/InAppHsp2/library/src/main/module.json5) -->

页面跳转和页面返回都使用了Navigation的特性，详情参考[Navigation跳转](../ui/arkts-navigation-navigation.md#路由操作)。