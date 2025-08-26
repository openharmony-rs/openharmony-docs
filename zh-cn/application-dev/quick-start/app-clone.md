# 创建应用分身
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

应用分身能实现在一个设备上安装多个相同的应用，实现多个账号同时登录使用和运行并且互不影响。主要应用场景有社交账号双开、游戏大小号双开等，无需账号切换，从而省去频繁登录的繁琐。

创建应用分身之后，桌面上会出现多个相同图标的应用，其中带有下角标的应用图标表示分身应用。

主应用与分身应用之间的关系如下：
- 主应用和分身应用共享同一个应用。例如，当主应用更新/升级时，主应用与分身应用都会同步更新，包括应用的图标（icon）和名称（label）、应用特性本身的新特性等。
- 主应用和分身应用，其对应的使能和相关配置都是独立的，数据也是彼此隔离。
- 主应用被卸载时，所有分身应用也会同步卸载。卸载分身应用时，不会影响主应用。

以下图片展示了应用分身的效果：

![示例图1](figures/app-clone1.png)

## 约束与限制
输入法应用配置分身无效，无法创建应用分身。

## 应用分身的开发步骤

1. 配置应用分身的方法。

    在工程项目中对AppScope/app.json5配置文件配置[multiAppMode](app-configuration-file.md#multiappmode标签)字段。具体配置如下：
    ```json
    {
      "app": {
        "multiAppMode": {
          "multiAppModeType": "appClone",
          "maxCount": 2
        }
      }
    }
    ```



2. 创建分身应用。

    - 首先将已配置好的工程编译打包安装到设备上。
 
      ![示例图2](figures/app-clone4.png)

    - 然后打开设置>系统>应用分身，点击“创建分身”。

      ![示例图3](figures/app-clone5.png)

      ![示例图4](figures/app-clone3.png)

    - 返回桌面，检查创建是否成功。

      ![示例图1](figures/app-clone1.png)

      图中的三个应用都是独立的进程，运行、数据、通知等，都是彼此独立的。



