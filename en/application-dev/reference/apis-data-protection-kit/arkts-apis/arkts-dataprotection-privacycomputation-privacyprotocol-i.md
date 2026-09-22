# PrivacyProtocol

```TypeScript
interface PrivacyProtocol
```

Defines the privacy protocol configuration, including the data set size and protocol type used for privacy-preserving computation.

**Since:** 26.0.1

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
```

## dataSetSize

```TypeScript
dataSetSize: DataSetSize
```

The data set size for the privacy protocol. Determines the number of comparisons that a single result ciphertext can contain. The total number of result ciphertexts generated is determined by elements.size / dataSetSize. Choose an appropriate data set size based on the number of elements in privacySearch and the acceptable size of each result ciphertext.

**Type:** [DataSetSize](arkts-dataprotection-privacycomputation-datasetsize-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

## protocolType

```TypeScript
protocolType: ProtocolType
```

The protocol type for the privacy computation. Determines the privacy-preserving computation method (PSI or PIR).

**Type:** [ProtocolType](arkts-dataprotection-privacycomputation-protocoltype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset
