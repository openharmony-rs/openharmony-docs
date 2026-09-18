# PathPreference

```TypeScript
export type PathPreference = 'auto' | 'primaryCellular' | 'secondaryCellular'
```

Enumerates the types of networks specified in an HTTP request.

> **NOTE:** 
> 
> It is recommended that this parameter be used in scenarios such as network concurrency.

> If the specified network is not activated, the system uses the default network.

**Since:** 23

**System capability:** SystemCapability.Communication.NetStack

| Type | Description |
| --- | --- |
| 'auto' | Specifies the default network connection in an HTTP request. |
| 'primaryCellular' | Specifies the default cellular network connection in an HTTP request when the cellular network is activated. |
| 'secondaryCellular' | Specifies the cellular network connection of the secondary SIM card in an HTTP request when dual cellular networks are activated. |
