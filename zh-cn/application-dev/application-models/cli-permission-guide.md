# 申请CLI访问权限

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

CLI命令通过系统权限机制进行访问管控，开发者在使用CLI前需了解所需权限并完成权限申请与配置。

## 权限说明与配置

应用内通过fork + execvp调用 CLI 的前提条件是必须拥有以下权限：

| 权限名称 | 权限级别 | 授权方式 | 作用 |
| -------- | -------- | -------- | -------- |
| ohos.permission.CUSTOM_SANDBOX | normal | 系统授权（system_grant） | 允许应用自定义沙箱，是应用内通过fork+execvp调用CLI的前提条件。 |

1. 在应用工程的[module.json5配置文件](../quick-start/module-configuration-file.md#配置文件示例)的`requestPermissions`字段中声明`ohos.permission.CUSTOM_SANDBOX`权限，详见[向应用申请权限](../security/AccessToken/determine-application-mode.md)。

    ```json5
    {
      "module": {
        "name": "entry",
        "type": "entry",
        "deviceTypes": [
          "2in1"
        ],
        "abilities": [
          {
            "name": "EntryAbility",
            "srcEntry": "./ets/entryability/EntryAbility.ets",
            "exported": true
          }
        ],
        "requestPermissions": [
          {
            "name": "ohos.permission.CUSTOM_SANDBOX"
          }
        ]
      }
    }
    ```

2. 安装应用后执行CLI命令，若返回权限校验失败错误码，需检查权限是否正确声明。


## 常见配置问题

### 应用内调用CLI报错

**可能原因**：未申请`ohos.permission.CUSTOM_SANDBOX`权限。

**处理步骤**：在module.json5的`requestPermissions`中添加`ohos.permission.CUSTOM_SANDBOX`权限声明。

### 设备类型不匹配

**可能原因**：应用的`deviceTypes`未包含`2in1`，导致应用无法在PC/2in1设备上安装运行。

**处理步骤**：在module.json5中将`deviceTypes`配置为包含`2in1`。