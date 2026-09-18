# FollowXMode (System API)

Define followXMode.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

## DEFAULT

```TypeScript
DEFAULT = 0
```

Files are searched based on the follow rules configured in the **followx_file_list.cfg** file at each configuration level.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

## NO_RULE_FOLLOWED

```TypeScript
NO_RULE_FOLLOWED = 1
```

No follow rule is used even if the **followx_file_list.cfg** file exists.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

## SIM_DEFAULT

```TypeScript
SIM_DEFAULT = 10
```

Files are searched in **etc/carrier/&#36;{opkey}** at each configuration level based on the opkey of the default card.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

## SIM_1

```TypeScript
SIM_1 = 11
```

Files are searched in **etc/carrier/&#36;{opkey}** at each configuration level based on the opkey of card 1.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

## SIM_2

```TypeScript
SIM_2 = 12
```

Files are searched in **etc/carrier/&#36;{opkey}** at each configuration level based on the opkey of card 2.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

## USER_DEFINED

```TypeScript
USER_DEFINED = 100
```

In user-defined mode, configuration files are obtained based on the follow rule provided by **extra**, and the **followx_file_list.cfg** file at each configuration level is ignored.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.
