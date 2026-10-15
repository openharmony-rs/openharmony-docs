# SessionStatus

```TypeScript
enum SessionStatus
```

Enumerates the status values of a CLI tool or commad execution session.

**Since:** 26.0.1

<!--Device-cliManager-enum SessionStatus--><!--Device-cliManager-enum SessionStatus-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## COMPLETED

```TypeScript
COMPLETED = 'completed'
```

The session has completed. The tool process exited normally, and the execution result is available in [result](arkts-ability-climanager-clisessioninfo-i.md#result).

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SessionStatus-COMPLETED = 'completed'--><!--Device-SessionStatus-COMPLETED = 'completed'-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## FAILED

```TypeScript
FAILED = 'failed'
```

The session has failed. The tool process encountered an error or was forcibly terminated. The failure details are available in [result](arkts-ability-climanager-clisessioninfo-i.md#result).

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SessionStatus-FAILED = 'failed'--><!--Device-SessionStatus-FAILED = 'failed'-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## RUNNING

```TypeScript
RUNNING = 'running'
```

The session is running. The tool process has been created and is currently executing.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SessionStatus-RUNNING = 'running'--><!--Device-SessionStatus-RUNNING = 'running'-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
