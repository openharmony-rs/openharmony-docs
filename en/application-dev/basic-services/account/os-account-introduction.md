# System Account Introduction

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=2d4bad83eb03b69babfde901d5e6eeccd92b443c translatedAt=2026-11-03T13:19:22.777Z pushedAt=2026-11-04T01:48:09.399Z nl=1 -->

## System Account ID System

In OpenHarmony, each system account is assigned a unique integer identifier upon creation, called the **system account ID**, which corresponds to the `localId` field in [OsAccountInfo](../../reference/apis-basic-services-kit/js-apis-osAccount.md#osaccountinfo). System account IDs are classified into the following categories by purpose:

| Range | Category | Purpose |
|------|------|------|
| ID=0 | System-level public service account | System-level services and applications are installed and run under this account. |
| ID=1 | Enterprise-level public service account | Enterprise-level services and applications are installed and run under this account. |
| ID=2~99 | Reserved system accounts | Reserved by the system, not yet defined. |
| ID=100+ | Natural person user account | Accounts used by natural persons, with IDs starting from 100. |

> **NOTE**
> 
> For the installation specifications of apps under each type of system account, see [App Installation Instructions](../../tools/bm-tool.md#userid).

## Related Documents

- [OsAccountInfo](../../reference/apis-basic-services-kit/js-apis-osAccount.md#osaccountinfo)
