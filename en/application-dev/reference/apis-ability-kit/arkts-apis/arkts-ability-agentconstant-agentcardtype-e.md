# AgentCardType

```TypeScript
export enum AgentCardType
```

The type of an AgentCard.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## APP

```TypeScript
APP = 0
```

Application-type agent card, applicable to traditional installable applications. The agent capability is installed and uninstalled along with the application, and users need to actively install the application before use.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## ATOMIC_SERVICE

```TypeScript
ATOMIC_SERVICE = 1
```

Atomic service-type agent card, applicable to installation-free atomic services. The agent capability can be used on demand without pre-installation, supporting quick experience and sharing.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AgentRuntime.Core
