# Key Derivation Overview and Algorithm Specifications

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=858505f536999bd946705d818d535cf8d7fec8f1 translatedAt=2026-08-07T03:31:15.955Z pushedAt=2026-08-10T09:27:45.882Z -->

A key derivation function (KDF) is a cryptographic algorithm that derives one or more secret keys from a secret value by using a pseudorandom function (PRF). It can be used to stretch keys into longer keys or to obtain keys in the required format.

## PBKDF2

Password-Based Key Derivation Function (PBKDF) is a key derivation function with a sliding computational cost. PBKDF2 is part of the PKCS series.

PBKDF2 applies a PRF, such as an [HMAC](crypto-compute-hmac.md), to an input password together with a salt value, and repeats the process multiple times to generate a derived key.

Key derivation can be performed using a string parameter, which is composed of the KDF algorithm and HMAC algorithm separated by a vertical bar (|). The string parameter is used to specify the algorithm specifications when the KDF generator is created.

| KDF Algorithm| HMAC Algorithm| String Parameter| API Version|
| -------- | -------- | -------- | -------- |
| PBKDF2 | SHA1 | PBKDF2\|SHA1 | 11+ |
| PBKDF2 | SHA224 | PBKDF2\|SHA224 | 11+ |
| PBKDF2 | SHA256 | PBKDF2\|SHA256 | 11+ |
| PBKDF2 | SHA384 | PBKDF2\|SHA384 | 11+ |
| PBKDF2 | SHA512 | PBKDF2\|SHA512 | 11+ |
| PBKDF2 | SHA3-256 | PBKDF2\|SHA3-256 | 26.0.0+ |
| PBKDF2 | SHA3-384 | PBKDF2\|SHA3-384 | 26.0.0+ |
| PBKDF2 | SHA3-512 | PBKDF2\|SHA3-512 | 26.0.0+ |
| PBKDF2 | SM3 | PBKDF2\|SM3 | 11+ |

## HKDF

The HMAC-based Extract-and-Expand Key Derivation Function (HKDF) is a simple key derivation algorithm based on [HMAC](crypto-compute-hmac.md).

It extracts keys from the input key material and salt value, and expands keys based on the input key material and extension information. It is a key derivation function used to derive longer output keys from shorter input keys.

HKDF has three modes: EXTRACT_ONLY, EXPAND_ONLY, and EXTRACT_AND_EXPAND.

- **EXTRACT_ONLY**: generates a pseudorandom key (PRK) from the input key material (IKM) and an optional salt.

- **EXPAND_ONLY**: expands a short key into a longer one. It uses the extracted pseudorandom key to expand a key of the specified length while preserving randomness.

- **EXTRACT_AND_EXPAND**: derives a pseudorandom key and expands it to a key of the specified length.

When creating a KDF generator, you need to specify the algorithm specifications in a string parameter. The string parameter consists of the KDF algorithm, HMAC algorithm, and mode with a vertical bar (|) in between.

As shown in the following table, you can select at most one value from each range (the content in []) to form the string parameter. The mode is optional and defaults to **EXTRACT_AND_EXPAND** if not specified. For example, when the key derivation algorithm is HKDF, the HMAC function digest algorithm is SHA1, and the mode is **EXTRACT_AND_EXPAND**, the string parameter is "HKDF|SHA1" or "HKDF|SHA1|EXTRACT_AND_EXPAND".

| KDF Algorithm| HMAC Algorithm| Mode| API Version|
| -------- | -------- | -------- | -------- |
| HKDF | SHA1 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 12+ |
| HKDF | SHA224 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 12+ |
| HKDF | SHA256 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 12+ |
| HKDF | SHA384 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 12+ |
| HKDF | SHA512 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 12+ |
| HKDF | SHA3-256 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 26.0.0+ |
| HKDF | SHA3-384 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 26.0.0+ |
| HKDF | SHA3-512 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 26.0.0+ |
| HKDF | SM3 | [EXPAND_ONLY\|EXTRACT_ONLY\|EXTRACT_AND_EXPAND] | 12+ |

## Scrypt

The scrypt algorithm is a key derivation function (KDF) primarily used to generate encryption keys from an input password and salt value. This algorithm has three main parameters: **n**, **r**, and **p**, where **n** is the iteration count, **r** is the block size, and **p** is the parallelism factor. By adjusting these parameters, you can optimize the algorithm for different security requirements and hardware performance.

Using scrypt to derive keys consumes memory and computing resources. You must pass in appropriate values based on the device hardware conditions.

You can use the following formula to calculate the memory:<br>Memory (in bytes) = p * 128 * r + 32 * r * (n + 2) * 4

| KDF Algorithm| String Parameter| API Version|
| -------- | -------- | -------- |
| SCRYPT | SCRYPT | 16+ |

## X963KDF

X963KDF is a key derivation function (KDF) based on HMAC. It is usually used with elliptic curves to generate keys.

| KDF Algorithm| HMAC Algorithm| String Parameter| API Version|
| -------- | -------- | -------- | -------- |
| X963KDF | SHA1 | X963KDF\|SHA1 | 22+ |
| X963KDF | SHA224 | X963KDF\|SHA224 | 22+ |
| X963KDF | SHA256 | X963KDF\|SHA256 | 22+ |
| X963KDF | SHA384 | X963KDF\|SHA384 | 22+ |
| X963KDF | SHA512 | X963KDF\|SHA512 | 22+ |
| X963KDF | SHA3-256 | X963KDF\|SHA3-256 | 26.0.0+ |
| X963KDF | SHA3-384 | X963KDF\|SHA3-384 | 26.0.0+ |
| X963KDF | SHA3-512 | X963KDF\|SHA3-512 | 26.0.0+ |
| X963KDF | SM3 | X963KDF\|SM3 | 22+ |