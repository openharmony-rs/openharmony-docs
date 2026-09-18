# WantAgentFlags

Enumerates the flags used by the WantAgent objects.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ONE_TIME_FLAG

```TypeScript
ONE_TIME_FLAG = 0
```

The WantAgent object can be used only once.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## NO_BUILD_FLAG

```TypeScript
NO_BUILD_FLAG
```

The WantAgent object does not exist and hence it is not created. In this case, &lt;code&gt;null&lt;/code&gt; is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CANCEL_PRESENT_FLAG

```TypeScript
CANCEL_PRESENT_FLAG
```

The existing WantAgent object should be canceled before a new object is generated.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UPDATE_PRESENT_FLAG

```TypeScript
UPDATE_PRESENT_FLAG
```

Extra information of the existing WantAgent object is replaced with that of the new object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CONSTANT_FLAG

```TypeScript
CONSTANT_FLAG
```

The WantAgent object is immutable.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ELEMENT

```TypeScript
REPLACE_ELEMENT
```

The element property in the current Want can be replaced by the element property in the Want passed in WantAgent.trigger().This processing is not supported yet.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ACTION

```TypeScript
REPLACE_ACTION
```

The action property in the current Want can be replaced by the action property in the Want passed in WantAgent.trigger().This processing is not supported yet.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_URI

```TypeScript
REPLACE_URI
```

The uri property in the current Want can be replaced by the uri property in the Want passed in WantAgent.trigger().This processing is not supported yet.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ENTITIES

```TypeScript
REPLACE_ENTITIES
```

The &lt;code&gt;entities&lt;/code&gt; property in the current Want can be replaced by the &lt;code&gt;entities&lt;/code&gt; property in the Want passed in WantAgent.trigger().This processing is not supported yet.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_BUNDLE

```TypeScript
REPLACE_BUNDLE
```

The &lt;code&gt;bundleName&lt;/code&gt; property in the current Want can be replaced by the &lt;code&gt;bundleName&lt;/code&gt; property in the Want passed in WantAgent.trigger().This processing is not supported yet.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
