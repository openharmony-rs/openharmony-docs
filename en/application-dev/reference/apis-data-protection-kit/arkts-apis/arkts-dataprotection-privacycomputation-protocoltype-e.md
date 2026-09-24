# ProtocolType

```TypeScript
enum ProtocolType
```

Enumerates the privacy protocol types. The protocol type determines the privacy-preserving computation method used for the search operation.

**Since:** 26.0.1

**System capability:** SystemCapability.Security.Asset

## PSI_PROTOCOL

```TypeScript
PSI_PROTOCOL = 0
```

Private Set Intersection (PSI) protocol. Used to check whether a target element exists in the dataset without revealing the element or the dataset contents.

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

## PIR_PROTOCOL

```TypeScript
PIR_PROTOCOL = 1
```

Private Information Retrieval (PIR) protocol. Used to retrieve the value associated with a matched key in the dataset without revealing the key or the retrieved value.

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset
