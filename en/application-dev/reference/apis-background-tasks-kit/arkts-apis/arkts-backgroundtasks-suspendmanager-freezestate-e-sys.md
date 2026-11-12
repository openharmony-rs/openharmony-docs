# FreezeState (System API)

```TypeScript
export enum FreezeState
```

Enumerates the freeze states of an application.

**Since:** 26.1.0

<!--Device-suspendManager-export enum FreezeState--><!--Device-suspendManager-export enum FreezeState-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

## ACTIVE

```TypeScript
ACTIVE = 0
```

The application is in the active state.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FreezeState-ACTIVE = 0--><!--Device-FreezeState-ACTIVE = 0-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

## DOZE

```TypeScript
DOZE = 1
```

The application is in the doze state, entering the freeze process but not yet fully frozen.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FreezeState-DOZE = 1--><!--Device-FreezeState-DOZE = 1-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

## FROZEN

```TypeScript
FROZEN = 2
```

The application is in the frozen state.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FreezeState-FROZEN = 2--><!--Device-FreezeState-FROZEN = 2-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.
