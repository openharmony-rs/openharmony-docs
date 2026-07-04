# 包管理子系统Changelog

## cl.bundlemanager.1 module.json配置中skillProfiles标签新增version必填字段

**访问级别**

公开接口

**变更原因**

为支持技能版本管理，[module.json5配置文件](../../../application-dev/quick-start/module-configuration-file.md)中[skillProfiles标签](../../../application-dev/quick-start/module-configuration-file.md#skillprofiles标签)新增`version`必填字段，用于标识技能的语义化版本号。

**变更影响**

此变更涉及应用适配。

- 变更前：`skillProfiles`中的技能配置项不包含`version`字段。

- 变更后：`skillProfiles`中的每个技能配置项必须包含`version`字段，且该字段为必填项。

**起始 API Level**

26.0.0

**变更发生版本**

从OpenHarmony SDK 7.0.0.32版本开始。

**变更的接口/组件**

[module.json5配置文件](../../../application-dev/quick-start/module-configuration-file.md)中[skillProfiles标签](../../../application-dev/quick-start/module-configuration-file.md#skillprofiles标签)配置项。

**适配指导**

如果应用使用了`skillProfiles`配置技能，开发者必须在每个技能配置项中添加`version`字段：

1. 确认应用`module.json`中是否包含`skillProfiles`配置。
2. 如包含，检查每个技能配置项是否已配置`version`字段。
3. 为未配置`version`的技能添加符合语义化版本号规范的版本号，格式为`主版本号.次版本号.补丁版本号`。

**skillProfiles配置示例**

```json5
{
  "module": {
    // ...
    "skillProfiles": [
      {
        "name": "my-skill",
        "version": "1.0.0",   // 必选项
        "abilityName": "EntryAbility",
        "permissions": []
      }
    ],
    // ...
  }
}
```

## cl.bundlemanager.2 module.json配置中skillProfiles的name字段命名规则变更

**访问级别**

公开接口

**变更原因**

为规范技能名称的命名规则，[module.json5配置文件](../../../application-dev/quick-start/module-configuration-file.md)中[skillProfiles标签](../../../application-dev/quick-start/module-configuration-file.md#skillprofiles标签)的`name`字段命名规则进行了调整，使其更符合常见的命名规范。

**变更影响**

此变更涉及应用适配。

- 变更前：`name`字段中间允许配置多个连续连字符。

- 变更后：`name`字段中间不允许配置多个连续连字符。

**命名规则变更对比**

| 示例 | 修改前 | 修改后 |
| -------- | -------- | -------- |
| "my--skill" | ✅ 支持 | ❌ 不支持（连续连字符） |

**起始 API Level**

26.0.0

**变更发生版本**

从OpenHarmony SDK 7.0.0.32版本开始。

**变更的接口/组件**

[module.json5配置文件](../../../application-dev/quick-start/module-configuration-file.md)中[skillProfiles标签](../../../application-dev/quick-start/module-configuration-file.md#skillprofiles标签)的`name`字段。

**适配指导**

如果应用使用了`skillProfiles`配置技能，开发者需要检查技能名称是否符合新的命名规则：

1. 检查应用`module.json`中`skillProfiles`的`name`字段值。
2. 确认名称中不包含连续的连字符。

**适配示例**

```json5
// 变更前 - 不符合新规则的名称
{
  "module": {
    "name": "entry",
    "type": "entry",
    "skillProfiles": [
      {
        "name": "my--skill",         // ❌ 连续连字符
        "version": "1.0.0",
        "abilityName": "EntryAbility",
        "permissions": []
      }
    ]
  }
}

// 变更后 - 符合新规则的名称
{
  "module": {
    "name": "entry",
    "type": "entry",
    "skillProfiles": [
      {
        "name": "my-skill",          // ✅ 符合规则
        "version": "1.0.0",
        "abilityName": "EntryAbility",
        "permissions": []
      }
    ]
  }
}
```
