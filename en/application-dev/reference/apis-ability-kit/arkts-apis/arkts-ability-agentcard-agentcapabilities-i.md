# AgentCapabilities

Defines optional capabilities supported by an agent.

@typedef AgentCapabilities

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## extendedAgentCard

```TypeScript
extendedAgentCard?: boolean
```

Indicates if the agent supports providing an extended agent card when authenticated.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## extension

```TypeScript
extension?: string
```

The protocol extension supported by the agent.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## pushNotifications

```TypeScript
pushNotifications?: boolean
```

Indicates if the agent supports sending push notifications for asynchronous task updates.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## stateTransitionHistory

```TypeScript
stateTransitionHistory?: boolean
```

If the Agent exposes task state change history.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## streaming

```TypeScript
streaming?: boolean
```

Indicates if the agent supports streaming responses.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core
