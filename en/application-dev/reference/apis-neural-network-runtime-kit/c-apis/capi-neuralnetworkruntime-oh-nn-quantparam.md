# OH_NN_QuantParam

```c
typedef struct OH_NN_QuantParam {...} OH_NN_QuantParam
```

## Overview

Quantization information.<br> In quantization scenarios, the 32-bit floating-point data type is quantized into the fixed-point data type according to the following formula: \f[<br> q = clamp(round(\frac{r}{s}+z), q_{min}, q_{max})<br> \f]<br>s and z are quantization parameters, which are stored by <b>scale</b> and <b>zeroPoint</b><br>in {@link OH_NN_QuantParam}.<br>r is a floating point number, q is the quantization result, q_min is the lower bound of the quantization result, and<br>q_max is an upper bound of a quantization result. The calculation method is as follows:<br> \f[<br> \text{clamp}(x,min,max) =<br> \begin{cases}<br> q_{min} = -(1 << (numBits - 1)) \ q_{max} = (1 << (numBits - 1)) \ \end{cases}<br> \f]<br>The clamp function is defined as follows:<br> \f[<br> \text{clamp}(x,min,max) =<br> \begin{cases}<br> \text{max} & \text{ if } x > \text{ max } \ \text{min} & \text{ if } x < \text{ min } \ x & \text{ otherwise } \ \end{cases}<br> \f]

**System capability**: SystemCapability.AI.NeuralNetworkRuntime

**Since**: 9

**Deprecated**: 11

**Replaced by**: {@link NN_QuantParam}

**Related module**: [NeuralNetworkRuntime](capi-neuralnetworkruntime.md)

**Header file**: [neural_network_runtime_type.h](capi-neural-network-runtime-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t quantCount |  |
| const uint32_t *numBits | Number of quantization bits |
| const double *scale | Pointer to the scale data in the quantization formula |
| const int32_t *zeroPoint | Pointer to the zero point data in the quantization formula |


