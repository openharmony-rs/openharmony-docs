# @ohos.arkui.WithEnv(Define the WithEnv component that allows setting environment properties for child components.)

## Modules to Import

```TypeScript
import { WithEnv, WithEnvAttribute} from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [WithEnvAttribute](arkts-arkui-arkui-withenv-withenvattribute-c.md) | Define the WithEnv attribute functions. |

### Types

| Name | Description |
| --- | --- |
| [WithEnvInterface](arkts-arkui-withenvinterface-t.md) | Define the WithEnv component's type. |

### Constants

| Name | Description |
| --- | --- |
| [WithEnv](arkts-arkui-arkui-withenv-con.md) | Define the WithEnv component that allows setting environment properties for child components. |
| [WithEnvInstance](arkts-arkui-arkui-withenv-con.md#withenvinstance) | Define WithEnv Logic Component Instance. |

## Examples

```TypeScript
### Example 1: Setting Local Font Scale

This example uses  to set a local font scale for components within the scope.

Since API version 26.0.0, the env attribute and the key WritableEnvKey.FONT_SCALE are added.
```

```TypeScript
### Example 2: Setting Local Layout Direction

This example uses  to set the local layout direction for components within the scope.

Since API version 26.0.0, the env attribute and the key WritableEnvKey.DIRECTION are added.
```
