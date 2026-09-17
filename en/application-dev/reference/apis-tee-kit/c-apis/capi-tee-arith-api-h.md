# tee_arith_api.h

## Overview

Provides APIs for operating big integers.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| TEE_BigIntSizeInU32(n) ((((n) + 31) / 32) + 2) | Obtains the size of the array of uint32_t values required to represent a <b>BigInt</b>.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [size_t TEE_BigIntFMMSizeInU32(size_t modulusSizeInBits)](#tee_bigintfmmsizeinu32) | Obtains the size of the array of uint32_t values. |
| [size_t TEE_BigIntFMMContextSizeInU32(size_t modulusSizeInBits)](#tee_bigintfmmcontextsizeinu32) | Obtains the size of an array of uint32_t values required to represent a fast modular context. |
| [void TEE_BigIntInit(TEE_BigInt *bigInt, size_t len)](#tee_bigintinit) | Initializes a <b>TEE_BigInt</b>. |
| [void TEE_BigIntInitFMMContext(TEE_BigIntFMMContext *context, size_t len, const TEE_BigInt *modulus)](#tee_bigintinitfmmcontext) | Calculates the necessary prerequisites for fast modular multiplication and stores them in a context. |
| [TEE_Result TEE_BigIntInitFMMContext1(TEE_BigIntFMMContext *context, size_t len, const TEE_BigInt *modulus)](#tee_bigintinitfmmcontext1) | Calculates the necessary prerequisites for fast modular multiplication and stores them in a context. |
| [void TEE_BigIntInitFMM(TEE_BigIntFMM *bigIntFMM, size_t len)](#tee_bigintinitfmm) | Initializes a <b>TEE_BigIntFMM</b> and sets its represented value to zero. |
| [TEE_Result TEE_BigIntConvertFromOctetString(TEE_BigInt *dest, const uint8_t *buffer, size_t bufferLen, int32_t sign)](#tee_bigintconvertfromoctetstring) | Converts an octet string buffer into the <b>TEE_BigInt</b> format. |
| [TEE_Result TEE_BigIntConvertToOctetString(void *buffer, size_t *bufferLen, const TEE_BigInt *bigInt)](#tee_bigintconverttooctetstring) | Converts the absolute value of an integer in <b>TEE_BigInt</b> format into an octet string. |
| [void TEE_BigIntConvertFromS32(TEE_BigInt *dest, int32_t shortVal)](#tee_bigintconvertfroms32) | Sets <b>dest</b> to the value <b>shortVal</b>. |
| [TEE_Result TEE_BigIntConvertToS32(int32_t *dest, const TEE_BigInt *src)](#tee_bigintconverttos32) | Sets <b>dest</b> to the value of <b>src</b>, including the sign of <b>src</b>. |
| [int32_t TEE_BigIntCmp(const TEE_BigInt *op1, const TEE_BigInt *op2)](#tee_bigintcmp) | Checks whether op1 > op2, op1 == op2, or op1 < op2. |
| [int32_t TEE_BigIntCmpS32(const TEE_BigInt *op, int32_t shortVal)](#tee_bigintcmps32) | Checks whether op > shortVal, op == shortVal, or op < shortVal. |
| [void TEE_BigIntShiftRight(TEE_BigInt *dest, const TEE_BigInt *op, size_t bits)](#tee_bigintshiftright) | Computes \|dest\| = \|op\| >> bits. |
| [bool TEE_BigIntGetBit(const TEE_BigInt *src, uint32_t bitIndex)](#tee_bigintgetbit) | Obtains the <b>bitIndex</b> bit of the natural binary representation of \|src\|. |
| [uint32_t TEE_BigIntGetBitCount(const TEE_BigInt *src)](#tee_bigintgetbitcount) | Obtains the number of bits in the natural binary representation of \|src\|, that is, the magnitude of <b>src</b>. |
| [TEE_Result TEE_BigIntSetBit(TEE_BigInt *op, uint32_t bitIndex, bool value)](#tee_bigintsetbit) | Sets the first bit of <b>bitIndex</b> in the natural binary representation of <b>op</b> to <b>1</b> or <b>0</b>. |
| [TEE_Result TEE_BigIntAssign(TEE_BigInt *dest, const TEE_BigInt *src)](#tee_bigintassign) | Assigns the value of <b>src</b> to <b>dest</b>. |
| [TEE_Result TEE_BigIntAbs(TEE_BigInt *dest, const TEE_BigInt *src)](#tee_bigintabs) | Assigns the value of <b>src</b> to <b>dest</b>. |
| [void TEE_BigIntAdd(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2)](#tee_bigintadd) | Computes dest = op1 + op2. |
| [void TEE_BigIntSub(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2)](#tee_bigintsub) | Computes dest = op1 – op2. |
| [void TEE_BigIntNeg(TEE_BigInt *dest, const TEE_BigInt *op)](#tee_bigintneg) | Negates an operand: dest = –op. |
| [void TEE_BigIntMul(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2)](#tee_bigintmul) | Computes dest = op1 * op2. |
| [void TEE_BigIntSquare(TEE_BigInt *dest, const TEE_BigInt *op)](#tee_bigintsquare) | Computes dest = op * op. |
| [void TEE_BigIntDiv(TEE_BigInt *dest_q, TEE_BigInt *dest_r, const TEE_BigInt *op1, const TEE_BigInt *op2)](#tee_bigintdiv) | Computes <b>dest_r</b> and <b>dest_q</b> to make op1 = dest_q* op2 + dest_r. |
| [void TEE_BigIntMod(TEE_BigInt *dest, const TEE_BigInt *op, const TEE_BigInt *n)](#tee_bigintmod) | Computes dest = op (mod n) to make 0 <= dest < n. |
| [void TEE_BigIntAddMod(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n)](#tee_bigintaddmod) | Computes dest = (op1 + op2) (mod n). |
| [void TEE_BigIntSubMod(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n)](#tee_bigintsubmod) | Computes dest = (op1 – op2) (mod n). |
| [void TEE_BigIntMulMod(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n)](#tee_bigintmulmod) | Computes dest = (op1* op2)(mod n). |
| [void TEE_BigIntSquareMod(TEE_BigInt *dest, const TEE_BigInt *op, const TEE_BigInt *n)](#tee_bigintsquaremod) | Computes dest = (op * op) (mod n). |
| [void TEE_BigIntInvMod(TEE_BigInt *dest, const TEE_BigInt *op, const TEE_BigInt *n)](#tee_bigintinvmod) | Computes <b>dest</b> to make dest* op = 1 (mod n). |
| [bool TEE_BigIntRelativePrime(const TEE_BigInt *op1, const TEE_BigInt *op2)](#tee_bigintrelativeprime) | Checks whether gcd(op1, op2) == 1. |
| [void TEE_BigIntComputeExtendedGcd(TEE_BigInt *gcd, TEE_BigInt *u, TEE_BigInt *v, const TEE_BigInt *op1, const TEE_BigInt *op2)](#tee_bigintcomputeextendedgcd) | Computes the greatest common divisor of <b>op1</b> and <b>op2</b>. |
| [int32_t TEE_BigIntIsProbablePrime(const TEE_BigInt *op, uint32_t confidenceLevel)](#tee_bigintisprobableprime) | Performs a probabilistic primality test on <b>op</b>. |
| [void TEE_BigIntConvertToFMM(TEE_BigIntFMM *dest, const TEE_BigInt *src, const TEE_BigInt *n, const TEE_BigIntFMMContext *context)](#tee_bigintconverttofmm) | Converts <b>src</b> into a representation suitable for doing fast modular multiplication. |
| [void TEE_BigIntConvertFromFMM(TEE_BigInt *dest, const TEE_BigIntFMM *src, const TEE_BigInt *n, const TEE_BigIntFMMContext *context)](#tee_bigintconvertfromfmm) | Converts <b>src</b> in the fast modular multiplication representation back to a <b>TEE_BigInt</b> representation. |
| [void TEE_BigIntComputeFMM(TEE_BigIntFMM *dest, const TEE_BigIntFMM *op1, const TEE_BigIntFMM *op2, const TEE_BigInt *n, const TEE_BigIntFMMContext *context)](#tee_bigintcomputefmm) | Computes dest = op1* op2 in the fast modular multiplication representation. |
| [TEE_Result TEE_BigIntExpMod(TEE_BigInt *des, TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n, TEE_BigIntFMMContext *context)](#tee_bigintexpmod) | Computes dest = (op1 ^ op2)(mod n). |

### Variable

| Name | Description |
| -- | -- |
| uint32_t TEE_BigInt | Defines the handle type representing a big integer.<br>**Since**: 20 |
| uint32_t TEE_BigIntFMM | Defines the handle of a big integer for Fast Modular Multiplication (FMM).<br>**Since**: 20 |
| uint32_t TEE_BigIntFMMContext | Defines the handle of a context container for FMM operations.<br>**Since**: 20 |

## Function description

### TEE_BigIntFMMSizeInU32()

```c
size_t TEE_BigIntFMMSizeInU32(size_t modulusSizeInBits)
```

**Description**

Obtains the size of the array of uint32_t values.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t modulusSizeInBits | Indicates the modulus size, in bits. |

**Returns**:

| Type | Description |
| -- | -- |
| size_t | Returns the number of bytes required to store a <b>TEE_BigIntFMM</b>,  given a modulus of length <b>modSizeInBits</b>. |

### TEE_BigIntFMMContextSizeInU32()

```c
size_t TEE_BigIntFMMContextSizeInU32(size_t modulusSizeInBits)
```

**Description**

Obtains the size of an array of uint32_t values required to represent a fast modular context.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t modulusSizeInBits | Indicates the modulus size, in bits. |

**Returns**:

| Type | Description |
| -- | -- |
| size_t | Returns the number of bytes required to store a <b>TEE_BigIntFMMContext</b>,  given a modulus of length <b>modSizeInBits</b>. |

### TEE_BigIntInit()

```c
void TEE_BigIntInit(TEE_BigInt *bigInt, size_t len)
```

**Description**

Initializes a <b>TEE_BigInt</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *bigInt | Indicates the pointer to the <b>TEE_BigInt</b> to initialize. |
| size_t len | Indicates the size of the memory pointed to by <b>TEE_BigInt</b>, in uint32_t. |

### TEE_BigIntInitFMMContext()

```c
void TEE_BigIntInitFMMContext(TEE_BigIntFMMContext *context, size_t len, const TEE_BigInt *modulus)
```

**Description**

Calculates the necessary prerequisites for fast modular multiplication and stores them in a context.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigIntFMMContext *context | Indicates the pointer to the <b>TEE_BigIntFMMContext</b> to initialize. |
| size_t len | Indicates the size of the memory pointed to by <b>context</b>, in uint32_t. |
| const TEE_BigInt *modulus | Indicates the pointer to the modulus. |

### TEE_BigIntInitFMMContext1()

```c
TEE_Result TEE_BigIntInitFMMContext1(TEE_BigIntFMMContext *context, size_t len, const TEE_BigInt *modulus)
```

**Description**

Calculates the necessary prerequisites for fast modular multiplication and stores them in a context.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigIntFMMContext *context | Indicates the pointer to the <b>TEE_BigIntFMMContext</b> to initialize. |
| size_t len | Indicates the size of the memory pointed to by <b>context</b>, in uint32_t. |
| const TEE_BigInt *modulus | Indicates the pointer to the modulus. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns other values if the operation fails. |

### TEE_BigIntInitFMM()

```c
void TEE_BigIntInitFMM(TEE_BigIntFMM *bigIntFMM, size_t len)
```

**Description**

Initializes a <b>TEE_BigIntFMM</b> and sets its represented value to zero.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigIntFMM *bigIntFMM | Indicates the pointer to the <b>TEE_BigIntFMM</b> to initialize. |
| size_t len | Indicates the size of the memory pointed to by <b>bigIntFMM</b>, in uint32_t. |

### TEE_BigIntConvertFromOctetString()

```c
TEE_Result TEE_BigIntConvertFromOctetString(TEE_BigInt *dest, const uint8_t *buffer, size_t bufferLen, int32_t sign)
```

**Description**

Converts an octet string buffer into the <b>TEE_BigInt</b> format.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result. |
| const uint8_t *buffer | Indicates the pointer to the buffer that holds the octet string representation of the integer. |
| size_t bufferLen | Indicates the buffer length, in bytes. |
| int32_t sign | Indicates the sign of <b>dest</b>, which is set to the sign of <b>sign</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OVERFLOW</b> if the memory allocated for <b>dest</b> is too small. |

### TEE_BigIntConvertToOctetString()

```c
TEE_Result TEE_BigIntConvertToOctetString(void *buffer, size_t *bufferLen, const TEE_BigInt *bigInt)
```

**Description**

Converts the absolute value of an integer in <b>TEE_BigInt</b> format into an octet string.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *buffer | Indicates the pointer to the output buffer that holds the converted octet string representation of the integer. |
| size_t *bufferLen | Indicates the pointer to the buffer length, in bytes. |
| const TEE_BigInt *bigInt | Indicates the pointer to the integer to convert. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_SHORT_BUFFER</b> if the output buffer is too small to hold the octet string. |

### TEE_BigIntConvertFromS32()

```c
void TEE_BigIntConvertFromS32(TEE_BigInt *dest, int32_t shortVal)
```

**Description**

Sets <b>dest</b> to the value <b>shortVal</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result. |
| int32_t shortVal | Indicates the value to set. |

### TEE_BigIntConvertToS32()

```c
TEE_Result TEE_BigIntConvertToS32(int32_t *dest, const TEE_BigInt *src)
```

**Description**

Sets <b>dest</b> to the value of <b>src</b>, including the sign of <b>src</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t *dest | Indicates the pointer to the <b> int32_t</b> that holds the result. |
| const TEE_BigInt *src | Indicates the pointer to the value to set. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OVERFLOW</b> if <b>src</b> does not fit within an <b> int32_t</b>. |

### TEE_BigIntCmp()

```c
int32_t TEE_BigIntCmp(const TEE_BigInt *op1, const TEE_BigInt *op2)
```

**Description**

Checks whether op1 > op2, op1 == op2, or op1 < op2.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>0</b> if op1 == op2.          Returns a positive number if op1 > op2. |

### TEE_BigIntCmpS32()

```c
int32_t TEE_BigIntCmpS32(const TEE_BigInt *op, int32_t shortVal)
```

**Description**

Checks whether op > shortVal, op == shortVal, or op < shortVal.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_BigInt *op | Indicates the pointer to the first operand. |
| int32_t shortVal | Indicates the pointer to the second operand. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>0</b> if op1 == shortVal.          Returns a positive number if op1 > shortVal. |

### TEE_BigIntShiftRight()

```c
void TEE_BigIntShiftRight(TEE_BigInt *dest, const TEE_BigInt *op, size_t bits)
```

**Description**

Computes \|dest\| = \|op\| >> bits.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the shifted result. |
| const TEE_BigInt *op | Indicates the pointer to the operand to be shifted. |
| size_t bits | Indicates the number of bits to shift. |

### TEE_BigIntGetBit()

```c
bool TEE_BigIntGetBit(const TEE_BigInt *src, uint32_t bitIndex)
```

**Description**

Obtains the <b>bitIndex</b> bit of the natural binary representation of \|src\|.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_BigInt *src | Indicates the pointer to the integer. |
| uint32_t bitIndex | Indicates the offset of the bit to read, starting from offset <b>0</b> of the least significant bit. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the Boolean value of <b>bitIndexth</b> in \|src\|. The value <b>true</b> represents a <b>1</b>,  and <b>false</b> represents a <b>0</b>. |

### TEE_BigIntGetBitCount()

```c
uint32_t TEE_BigIntGetBitCount(const TEE_BigInt *src)
```

**Description**

Obtains the number of bits in the natural binary representation of \|src\|, that is, the magnitude of <b>src</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_BigInt *src | Indicates the pointer to the integer. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns <b>0</b> if <b>src</b> is <b>0</b>.          Returns the number of bits in the natural binary representation of <b>src</b>. |

### TEE_BigIntSetBit()

```c
TEE_Result TEE_BigIntSetBit(TEE_BigInt *op, uint32_t bitIndex, bool value)
```

**Description**

Sets the first bit of <b>bitIndex</b> in the natural binary representation of <b>op</b> to <b>1</b> or <b>0</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *op | Indicates the pointer to the integer. |
| uint32_t bitIndex | Indicates the offset of the bit to set, starting from offset <b>0</b> of the least significant bit. |
| bool value | Indicates the bit value to set. The value <b>true</b> represents a <b>1</b>, and the value <b>false</b> represents a <b>0</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OVERFLOW bitIndexth</b> if the <b>bitIndexth</b> bit is larger than the allocated bit  length of <b>op</b>. |

### TEE_BigIntAssign()

```c
TEE_Result TEE_BigIntAssign(TEE_BigInt *dest, const TEE_BigInt *src)
```

**Description**

Assigns the value of <b>src</b> to <b>dest</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> to be assigned. |
| const TEE_BigInt *src | Indicates the pointer to the source operand. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OVERFLOW</b> if the <b>dest</b> operand cannot hold the value of <b>src</b>. |

### TEE_BigIntAbs()

```c
TEE_Result TEE_BigIntAbs(TEE_BigInt *dest, const TEE_BigInt *src)
```

**Description**

Assigns the value of <b>src</b> to <b>dest</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> to be assigned. |
| const TEE_BigInt *src | Indicates the pointer to the source operand. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OVERFLOW</b> if the <b>dest</b> operand cannot hold the value of <b>src</b>. |

### TEE_BigIntAdd()

```c
void TEE_BigIntAdd(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2)
```

**Description**

Computes dest = op1 + op2.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the sum of <b>op1</b> and <b>op2</b>. |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |

### TEE_BigIntSub()

```c
void TEE_BigIntSub(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2)
```

**Description**

Computes dest = op1 – op2.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the difference between <b>op1</b> and <b>op2</b>. |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |

### TEE_BigIntNeg()

```c
void TEE_BigIntNeg(TEE_BigInt *dest, const TEE_BigInt *op)
```

**Description**

Negates an operand: dest = –op.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result –op. |
| const TEE_BigInt *op | Indicates the pointer to the operand to be negated. |

### TEE_BigIntMul()

```c
void TEE_BigIntMul(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2)
```

**Description**

Computes dest = op1 * op2.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the product of <b>op1</b> and <b>op2</b>. |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |

### TEE_BigIntSquare()

```c
void TEE_BigIntSquare(TEE_BigInt *dest, const TEE_BigInt *op)
```

**Description**

Computes dest = op * op.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result op * op. |
| const TEE_BigInt *op | Indicates the pointer to the operand to be squared. |

### TEE_BigIntDiv()

```c
void TEE_BigIntDiv(TEE_BigInt *dest_q, TEE_BigInt *dest_r, const TEE_BigInt *op1, const TEE_BigInt *op2)
```

**Description**

Computes <b>dest_r</b> and <b>dest_q</b> to make op1 = dest_q* op2 + dest_r.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest_q | Indicates the pointer to the <b>TEE_BigInt</b> that holds the quotient. |
| TEE_BigInt *dest_r | Indicates the pointer to the <b>TEE_BigInt</b> that holds the remainder. |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand, which is the dividend. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand, which is the divisor. |

### TEE_BigIntMod()

```c
void TEE_BigIntMod(TEE_BigInt *dest, const TEE_BigInt *op, const TEE_BigInt *n)
```

**Description**

Computes dest = op (mod n) to make 0 <= dest < n.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result op (mod n). |
| const TEE_BigInt *op | Indicates the pointer to the operand to be reduced mod n. |
| const TEE_BigInt *n | [IN] Indicates the pointer to the modulus, which must be greater than 1. |

### TEE_BigIntAddMod()

```c
void TEE_BigIntAddMod(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n)
```

**Description**

Computes dest = (op1 + op2) (mod n).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result op (op1 + op2)(mod n). |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |
| const TEE_BigInt *n | Indicates the pointer to the modulus, which must be greater than 1. |

### TEE_BigIntSubMod()

```c
void TEE_BigIntSubMod(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n)
```

**Description**

Computes dest = (op1 – op2) (mod n).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result op (op1 – op2)(mod n). |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |
| const TEE_BigInt *n | Indicates the pointer to the modulus, which must be greater than 1. |

### TEE_BigIntMulMod()

```c
void TEE_BigIntMulMod(TEE_BigInt *dest, const TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n)
```

**Description**

Computes dest = (op1* op2)(mod n).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result op (op1 * op2)(mod n). |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |
| const TEE_BigInt *n | Indicates the pointer to the modulus, which must be greater than 1. |

### TEE_BigIntSquareMod()

```c
void TEE_BigIntSquareMod(TEE_BigInt *dest, const TEE_BigInt *op, const TEE_BigInt *n)
```

**Description**

Computes dest = (op * op) (mod n).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result op (op * op)(mod n). |
| const TEE_BigInt *op | Indicates the pointer to the operand. |
| const TEE_BigInt *n | [IN] Indicates the pointer to the modulus, which must be greater than 1. |

### TEE_BigIntInvMod()

```c
void TEE_BigIntInvMod(TEE_BigInt *dest, const TEE_BigInt *op, const TEE_BigInt *n)
```

**Description**

Computes <b>dest</b> to make dest* op = 1 (mod n).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result (op^–1)(mod n). |
| const TEE_BigInt *op | Indicates the pointer to the operand. |
| const TEE_BigInt *n | [IN] Indicates the pointer to the modulus, which must be greater than 1. |

### TEE_BigIntRelativePrime()

```c
bool TEE_BigIntRelativePrime(const TEE_BigInt *op1, const TEE_BigInt *op2)
```

**Description**

Checks whether gcd(op1, op2) == 1.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns <b>true</b> if gcd(op1, op2) == 1.          Returns <b>false</b> if gcd(op1, op2) != 1. |

### TEE_BigIntComputeExtendedGcd()

```c
void TEE_BigIntComputeExtendedGcd(TEE_BigInt *gcd, TEE_BigInt *u, TEE_BigInt *v, const TEE_BigInt *op1, const TEE_BigInt *op2)
```

**Description**

Computes the greatest common divisor of <b>op1</b> and <b>op2</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *gcd | Indicates the pointer to the <b>TEE_BigInt</b> that holds the greatest common divisor of <b>op1</b> and <b>op2</b>. |
| TEE_BigInt *u | Indicates the pointer to the <b>TEE_BigInt</b> that holds the first coefficient. |
| TEE_BigInt *v | Indicates the pointer to the <b>TEE_BigInt</b> that holds the second coefficient. |
| const TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |

### TEE_BigIntIsProbablePrime()

```c
int32_t TEE_BigIntIsProbablePrime(const TEE_BigInt *op, uint32_t confidenceLevel)
```

**Description**

Performs a probabilistic primality test on <b>op</b>.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_BigInt *op | Indicates the pointer to the candidate number that is tested for primality. |
| uint32_t confidenceLevel | Indicates the expected confidence level for a non-conclusive test. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns <b>0</b> if <b>op</b> is a composite number.          Returns <b>1</b> if <b>op</b> is a prime number.          Returns <b>–1</b> if the test is non-conclusive but the probability that <b>op</b> is composite is  less than 2^(-confidenceLevel). |

### TEE_BigIntConvertToFMM()

```c
void TEE_BigIntConvertToFMM(TEE_BigIntFMM *dest, const TEE_BigInt *src, const TEE_BigInt *n, const TEE_BigIntFMMContext *context)
```

**Description**

Converts <b>src</b> into a representation suitable for doing fast modular multiplication.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigIntFMM *dest | Indicates the pointer to an initialized <b>TEE_BigIntFMM</b> memory area. |
| const TEE_BigInt *src | Indicates the pointer to the <b>TEE_BigInt</b> to convert. |
| const TEE_BigInt *n | Indicates the pointer to the modulus. |
| const TEE_BigIntFMMContext *context | Indicates the pointer to the context that is previously initialized using [TEE_BigIntInitFMMContext1](capi-tee-arith-api-h.md#tee_bigintinitfmmcontext1). |

### TEE_BigIntConvertFromFMM()

```c
void TEE_BigIntConvertFromFMM(TEE_BigInt *dest, const TEE_BigIntFMM *src, const TEE_BigInt *n, const TEE_BigIntFMMContext *context)
```

**Description**

Converts <b>src</b> in the fast modular multiplication representation back to a <b>TEE_BigInt</b> representation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *dest | Indicates the pointer to an initialized <b>TEE_BigIntFMM</b> memory area to store the converted result. |
| const TEE_BigIntFMM *src | Indicates the pointer to a <b>TEE_BigIntFMM</b> holding the value in the fast modular multiplication representation. |
| const TEE_BigInt *n | Indicates the pointer to the modulus. |
| const TEE_BigIntFMMContext *context | Indicates the pointer to the context that is previously initialized using [TEE_BigIntInitFMMContext1](capi-tee-arith-api-h.md#tee_bigintinitfmmcontext1). |

### TEE_BigIntComputeFMM()

```c
void TEE_BigIntComputeFMM(TEE_BigIntFMM *dest, const TEE_BigIntFMM *op1, const TEE_BigIntFMM *op2, const TEE_BigInt *n, const TEE_BigIntFMMContext *context)
```

**Description**

Computes dest = op1* op2 in the fast modular multiplication representation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigIntFMM *dest | Indicates the pointer to the <b>TEE_BigIntFMM</b> that holds the result op1* op2. |
| const TEE_BigIntFMM *op1 | Indicates the pointer to the first operand. |
| const TEE_BigIntFMM *op2 | Indicates the pointer to the second operand. |
| const TEE_BigInt *n | Indicates the pointer to the modulus. |
| const TEE_BigIntFMMContext *context | Indicates the pointer to the context that is previously initialized using [TEE_BigIntInitFMMContext1](capi-tee-arith-api-h.md#tee_bigintinitfmmcontext1). |

### TEE_BigIntExpMod()

```c
TEE_Result TEE_BigIntExpMod(TEE_BigInt *des, TEE_BigInt *op1, const TEE_BigInt *op2, const TEE_BigInt *n, TEE_BigIntFMMContext *context)
```

**Description**

Computes dest = (op1 ^ op2)(mod n).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_BigInt *des | Indicates the pointer to the <b>TEE_BigInt</b> that holds the result (op1 ^ op2)(mod n). |
| TEE_BigInt *op1 | Indicates the pointer to the first operand. |
| const TEE_BigInt *op2 | Indicates the pointer to the second operand. |
| const TEE_BigInt *n | Indicates the pointer to the modulus. |
| TEE_BigIntFMMContext *context | Indicates the pointer to the context that is previously initialized using [TEE_BigIntInitFMMContext1](capi-tee-arith-api-h.md#tee_bigintinitfmmcontext1) or initialized to null. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_NOT_SUPPORTED</b> if the value of <b>n</b> is not supported. |


