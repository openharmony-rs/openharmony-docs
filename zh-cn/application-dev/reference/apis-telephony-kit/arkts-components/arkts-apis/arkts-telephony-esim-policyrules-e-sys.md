# PolicyRules（系统接口）

配置文件的策略规则。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## POLICY_RULE_DISABLE_NOT_ALLOWED

```TypeScript
POLICY_RULE_DISABLE_NOT_ALLOWED = 1
```

启用此配置文件后，将无法禁用。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## POLICY_RULE_DELETE_NOT_ALLOWED

```TypeScript
POLICY_RULE_DELETE_NOT_ALLOWED = 1 << 1
```

无法删除此配置文件。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## POLICY_RULE_DISABLE_AND_DELETE

```TypeScript
POLICY_RULE_DISABLE_AND_DELETE = 1 << 2
```

禁用后应删除此配置文件。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。
