# 创建应用多实例
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

应用多实例允许一个应用同时运行多个页面，实现多个账号同时登录使用，且互不影响。主要应用场景包括社交账户多开和游戏大小号多开等，无需切换账号从而避免频繁登录的繁琐操作。

桌面上的多个应用进程页面都是独立的进程，各个进程的运行、通知等都是彼此独立的；各实例共享数据，可通过账号进行切换。

应用多实例间的关系：
- 多实例的应用图标相同。
- 各实例共享数据，可通过账号进行切换。

## 约束限制

应用多实例仅支持2in1设备。

## 应用多实例的开发步骤
1. 应用多实例的配置方法。

    在工程项目中对App/app.json5配置文件配置[multiAppMode](app-configuration-file.md#multiappmode标签)字段。具体配置如下：
    ```json
    {
      "app": {
        //  ...
        "multiAppMode": {
          "multiAppModeType": "multiInstance",
          "maxCount": 5
        }
      }
    }
    ```

2. 创建应用多实例。

- 将已配置好的工程编译打包安装到设备上。
- 首次右击桌面应用图标启动一个应用进程，然后再次右击该应用图标，选择“打开”。
此时桌面上会显示同一个应用的两个进程页面。

