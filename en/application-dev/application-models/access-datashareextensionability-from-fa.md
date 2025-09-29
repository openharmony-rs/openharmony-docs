# Accessing a DataShareExtensionAbility from the FA Model

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## Overview

Regardless of the [FA model](ability-terminology.md#fa-model) or [stage model](ability-terminology.md#stage-model), the data read/write function consists of the client and server.

- In the FA model, the client uses [DataAbilityHelper](../reference/apis-ability-kit/js-apis-inner-ability-dataAbilityHelper.md) to provide external APIs, and the server uses [DataAbility](dataability-overview.md) to provide database read and write services.

- In the stage model, the client uses [DataShareHelper](../reference/apis-arkdata/js-apis-data-dataShare-sys.md#datasharehelper) to provide external APIs, and the server uses [DataShareExtensionAbility](../reference/apis-arkdata/js-apis-application-dataShareExtensionAbility-sys.md) to provide database read and write services

If the client uses the FA model whereas the server is upgraded to the stage model, the client cannot access the server.

To resolve this issue, the system provides a solution on the framework side for smooth evolution.


## Basic Principles

A compatible method is that **DataAbilityHelper** determines whether to call the **DataShareHelper** APIs based on the URI prefix (either **DataAbility** or **DataShare**). However, this method requires modification to the URI in the original client code.

Instead of manual modification, the system adopts the following processing:

1. The system attempts to start the DataAbility based on the URI passed in. If the startup fails, the system converts the URI prefix to **DataShare** and attempts to start the DataShareExtensionAbility.

2. If the URI does not map to any DataAbility or DataShareExtensionAbility, the startup fails. Otherwise, either the DataAbility or DataShareExtensionAbility is started.


## Constraints

1. When you switch a DataAbility to a DataShareExtensionAbility, only the URI prefix can be modified.

   ![FAvsStage-uri](figures/FAvsStage-uri.png)

2. The **DataShareHelper** class implements only certain APIs of **DataAbilityHelper**. For details about the APIs, see the table below.

   **Table 1** API compatibility when the FA model accesses a DataShareExtensionAbility of the stage model

   | API| Provided by DataAbilityHelper| Provided by DataShareHelper| Compatible|
   | -------- | -------- | -------- | -------- |
   | on | Yes| Yes| Yes|
   | off | Yes| Yes| Yes|
   | notifyChange | Yes| Yes| Yes|
   | insert | Yes| Yes| Yes|
   | delete | Yes| Yes| Yes|
   | query | Yes| Yes| Yes|
   | update | Yes| Yes| Yes|
   | batchInsert | Yes| Yes| Yes|
   | getType | Yes| No| No|
   | getFileTypes | Yes| No| No|
   | normalizeUri | Yes| Yes| Yes|
   | denormalizeUri | Yes| Yes| Yes|
   | openFile | Yes| No| No|
   | call | Yes| No| No|
   | executeBatch | Yes| No| No|
