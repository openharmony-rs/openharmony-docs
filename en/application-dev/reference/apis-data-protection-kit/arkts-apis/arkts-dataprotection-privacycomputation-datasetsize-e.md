# DataSetSize

Enumerates the data set sizes supported by the privacy protocol. The data set size defines the number of comparisons that a single result ciphertext can contain. The total number of result ciphertexts generated is determined by elements.size / dataSetSize. Choose an appropriate data set size based on the number of elements in privacySearch and the acceptable size of each result ciphertext.

**Since:** 26.1.0

**System capability:** SystemCapability.Security.Asset

## SIZE_128

```TypeScript
SIZE_128 = 0
```

A single result ciphertext can contain 128 comparisons.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset

## SIZE_256

```TypeScript
SIZE_256 = 1
```

A single result ciphertext can contain 256 comparisons.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset

## SIZE_512

```TypeScript
SIZE_512 = 2
```

A single result ciphertext can contain 512 comparisons.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset
