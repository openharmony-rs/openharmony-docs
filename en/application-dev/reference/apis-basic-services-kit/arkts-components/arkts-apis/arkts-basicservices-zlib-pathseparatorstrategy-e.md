# PathSeparatorStrategy

```TypeScript
export enum PathSeparatorStrategy
```

Defines **PathSeparatorStrategy**, a property of [Options](arkts-basicservices-zlib-options-i.md), used to specify the separator strategy for the file path in the compressed package specified for decompression.

**Since:** 21

<!--Device-zlib-export enum PathSeparatorStrategy--><!--Device-zlib-export enum PathSeparatorStrategy-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## PATH_SEPARATOR_STRATEGY_DEFAULT

```TypeScript
PATH_SEPARATOR_STRATEGY_DEFAULT = 0
```

Default value, indicating that separators in the file path of the compressed package are not processed.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_DEFAULT = 0--><!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_DEFAULT = 0-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH

```TypeScript
PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH = 1
```

Backslashes () in the file path of the package are replaced with slashes (/).

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH = 1--><!--Device-PathSeparatorStrategy-PATH_SEPARATOR_STRATEGY_REPLACE_BACKSLASH = 1-End-->

**System capability:** SystemCapability.BundleManager.Zlib
