# Accessing DataShareExtensionAbility in the Stage Model from the FA Model

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=79e2b0709a488b07e5881d61578e00850aa4f234 translatedAt=2026-09-17T08:18:35.510Z pushedAt=2026-09-21T11:20:23.454Z -->

## Overview

In both the [FA model](ability-terminology.md#fa-model) and the [Stage model](ability-terminology.md#stage-model), data read/write involves both a client and a server.

- In the FA model, the client provides external APIs through [DataAbilityHelper](../reference/apis-ability-kit/js-apis-inner-ability-dataAbilityHelper.md), and the server provides database read/write services through [DataAbility](dataability-overview.md).

- In the Stage model, the client provides external APIs through [DataShareHelper](../reference/apis-arkdata/js-apis-data-dataShare-sys.md#datasharehelper), and the server provides database read/write services through [DataShareExtensionAbility](../reference/apis-arkdata/js-apis-application-dataShareExtensionAbility-sys.md).

After the server is upgraded from the FA model to the Stage model, the FA model client can no longer access the server on API version 9 or later.

To address this issue, the system provides a solution at the framework layer, allowing developers to smoothly transition to API version 9 or later.


## Working Principles

One compatible approach is for DataAbilityHelper to decide whether to call the DataShareHelper APIs based on whether the prefix of the passed-in URI is DataAbility or DataShare. However, this approach requires developers to modify the URI in the original client code, which cannot achieve seamless switching.

Therefore, DataAbilityHelper cannot rely solely on the URI prefix to decide whether to access DataAbility or DataShareExtensionAbility. The system adopts the following approach:

1. First, start DataAbility based on the passed-in URI. If the startup fails, convert the prefix of the passed-in URI to DataShare and then try to start DataShareExtensionAbility.

2. If the URI has no corresponding DataAbility or DataShareExtensionAbility, the startup fails. Otherwise, either DataAbility or DataShareExtensionAbility will be started.


## Constraints

1. When switching from DataAbility to DataShareExtensionAbility, only the URI prefix can be modified; other parts of the URI cannot be changed.![FAvsStage-uri](figures/FAvsStage-uri.png)

2. DataShareHelper does not implement all the functions of the original DataAbilityHelper public APIs. Therefore, some APIs cannot be made compatible, as shown in Table 1.

     **Table 1** API support for accessing Stage model DataShareExtensionAbility from the FA model

   | API | Provided by DataAbilityHelper | Provided by DataShareHelper | Compatible | 
   | -------- | -------- | -------- | -------- |
   | on | Yes | Yes | Yes | 
   | off | Yes | Yes | Yes | 
   | notifyChange | Yes | Yes | Yes | 
   | insert | Yes | Yes | Yes | 
   | delete | Yes | Yes | Yes | 
   | query | Yes | Yes | Yes | 
   | update | Yes | Yes | Yes | 
   | batchInsert | Yes | Yes | Yes | 
   | getType | Yes | No | No | 
   | getFileTypes | Yes | No | No | 
   | normalizeUri | Yes | Yes | Yes | 
   | denormalizeUri | Yes | Yes | Yes | 
   | openFile | Yes | No | No | 
   | call | Yes | No | No | 
   | executeBatch | Yes | No | No | 
