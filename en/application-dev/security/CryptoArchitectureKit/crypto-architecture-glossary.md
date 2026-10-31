# Glossary

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=99672258e158c110c5ee74a166a44dafda8d8dee translatedAt=2026-10-30T03:25:07.380Z pushedAt=2026-10-30T07:24:29.131Z nl=1 -->

## A

### Advanced Encryption Standard (AES)

The most common symmetric encryption algorithm, which is a block cipher algorithm. It has a block size of 128 bits and a key length of 128, 192, or 256 bits. Compared with 3DES, it offers higher security and faster processing speed, and is used to ensure the confidentiality of data in storage or transmission scenarios. It supports multiple encryption modes, including ECB, CBC, OFB, CFB, CTR, GCM, CCM, and XTS.

### AES-WRAP

A key wrapping encryption algorithm based on AES, used to securely store or transmit symmetric keys. Its primary purpose is to protect keys through encryption, preventing them from being leaked or tampered with during storage or transmission.

### Asymmetric Key

A key system that uses two keys, a public key and a private key, for algorithm operations. The public key is made public, while the private key is kept secret. For encryption and decryption, the public key is generally used for encryption and the private key for decryption. For signature verification, the private key is used for signing and the public key for verification, thereby verifying whether the data has been tampered with.

## B

### Block Cipher

A symmetric encryption algorithm that divides plaintext into fixed-length data blocks and encrypts each block separately. AES, DES, 3DES, SM4, RC2, Blowfish, and CAST are all block ciphers. When the last block of plaintext is shorter than the block size, it must be padded to the required length using a padding mode.

### Blowfish

A block cipher algorithm with a block size of 64 bits (8 bytes) and a key length from 32 to 448 bits (in multiples of 8), supporting block modes such as ECB, CBC, OFB, and CFB. It is an insecure algorithm and is not recommended for use.

## C

### CAST

A block cipher algorithm (such as CAST-128/CAST5) with a block size of 64 bits (8 bytes), a key length from 40 to 128 bits (which must be a multiple of 8), and support for block modes such as ECB, CBC, OFB, and CFB. This is an insecure algorithm and is not recommended.

### ChaCha20

A modern stream cipher symmetric encryption algorithm with a key length of 256 bits. The ChaCha20 algorithm can be used alone, but it provides only confidentiality. More commonly, it is combined with the Poly1305 authenticator as the ChaCha20-Poly1305 AEAD mode, which provides both confidentiality and integrity.

### Cipher-based Message Authentication Code (CMAC)

An algorithm that generates a message authentication code based on a block cipher (such as AES) and a key. It ensures the integrity and authenticity of messages and detects tampering during transmission.

### Compressed/Uncompressed Point Format

Two encoding formats for elliptic curve public key points. The uncompressed format stores both the x and y coordinates, while the compressed format stores only the x coordinate and a flag bit. ECC and SM2 public key point data can be converted between the compressed and uncompressed formats.

## D

### Data Encryption Standard (DES)

A block cipher algorithm that divides plaintext into 64-bit blocks for encryption. The encryption process consists of 16 rounds of the same encryption function, each round using a subkey generated from the original key through permutation and shifting, with a key length of 64 bits.

### Diffie-Hellman Key Exchange (DH)

A key agreement algorithm that negotiates a shared key by exchanging public keys, with the private key never leaving the local device. Ephemeral DH (DHE) provides forward secrecy, ensuring that the private keys of both parties are not exposed even if the communication channel is monitored. It supports well-known prime groups such as modp and ffdhe.

### Digital Signature Algorithm (DSA)

A public key cryptographic algorithm based on modular arithmetic and the discrete logarithm problem over finite fields of integers. It is commonly used for digital signatures and signature verification, and cannot be used for encryption or decryption.

## E

### Elliptic Curve Cryptography (ECC)

A public key cryptographic algorithm based on elliptic curve mathematics, which can be regarded as operations on numbers defined over a special set. All ECC keys supported by the current algorithm library are elliptic curves over the Fp field (prime field).

### Elliptic Curve Diffie-Hellman Key Exchange (ECDH)

A Diffie-Hellman key agreement algorithm based on elliptic curves. The algorithm library provides ECDH capabilities over multiple elliptic curves (such as ECC224, ECC256, the Brainpool series, and Secp256k1) for negotiating a shared key over an insecure channel.

### Elliptic Curve Digital Signature Algorithm (ECDSA)

A digital signature algorithm based on elliptic curve cryptography (ECC). Compared with public key cryptosystems based on the discrete logarithm problem (DLP) and the integer factorization problem (IFP), elliptic curve cryptography offers higher strength per bit and supports the OnlySign/OnlyVerify modes.

### Elliptic Curve Integrated Encryption Scheme (ECIES)

A hybrid encryption algorithm based on elliptic curve cryptography that combines key agreement (ECC), key derivation (X963KDF), and symmetric encryption (AES-GCM) to perform encryption and decryption.

### Ed25519: Digital Signature Algorithm Based on the Edwards Curve

Ed25519 is a digital signature algorithm based on the EdDSA algorithm and using the Edwards curve (Curve25519), with a key length of 256 bits.

## H

### Hardware Entropy

A hardware random number entropy source obtained from a secure environment (such as a TEE or a secure chip) through HUKS. It is used to generate secure random numbers with greater "true randomness", making the results harder to guess or reproduce.

### Hash-based Message Authentication Code (HMAC)

A hash-based message authentication code algorithm that takes a key shared by the communicating parties and a message as input to generate a fixed-length authentication code for verifying message integrity. It adds a key input on top of the message digest algorithm to ensure information correctness.

### HMAC-based Extract-and-Expand Key Derivation Function (HKDF)

A key derivation algorithm based on the HMAC message authentication code, used to derive a longer output key from a shorter input key. It includes three modes: extract (EXTRACT_ONLY), expand (EXPAND_ONLY), and extract and expand (EXTRACT_AND_EXPAND).

## K

### Key Derivation Function (KDF)

A function that derives one or more keys from a secret value using a pseudo-random function. It can be used to expand a key into a longer key.

### Key-Encapsulation Mechanism (KEM)

A mechanism for securely negotiating a shared key over an insecure channel. The encapsulating party uses a public key to generate a shared key and an encapsulated key, and the decapsulating party uses a private key and the encapsulated key to recover the same shared key.

### Key Agreement

A mechanism by which two communicating parties negotiate a secure shared key over an insecure channel without pre-sharing any secret. Corresponding algorithms include ECDH, X25519, and DH.

## M

### Message Authentication Code (MAC)

A code used to verify message integrity. It detects message spoofing, tampering, and other behaviors by using a key shared by both parties.

### Message Digest 5 (MD5)

A message digest algorithm that generates a fixed-length digest of 16 bytes (128 bits). It offers low security and is not suitable for scenarios with high security requirements.

### Message Digest

The process of mapping a message of arbitrary length to a fixed-length digest value through a hash algorithm, also known as cryptographic hashing. The digest length is determined by the algorithm.

### Module-Lattice-Based Digital Signature Algorithm (ML-DSA)

A post-quantum digital signature cryptographic algorithm based on module lattices, used for signature verification and supporting parameter sets such as ML-DSA-44, ML-DSA-65, and ML-DSA-87.

### Module-Lattice-Based Key-Encapsulation Mechanism (ML-KEM)

A post-quantum cryptographic algorithm based on the module-lattice-based key-encapsulation mechanism, used for key encapsulation and decapsulation, supporting parameter sets such as ML-KEM-512, ML-KEM-768, and ML-KEM-1024.

## P

### Password-Based Key Derivation Function 2 (PBKDF2)

A key derivation function defined in the PKCS series of standards with variable computational cost. It derives keys by feeding the password plaintext and a salt into a pseudorandom function (such as the hash-based HMAC) and repeating the operation multiple times.

### Public-Key Cryptography Standards #1 (PKCS#1) 

The PKCS#1 standard defines the format of RSA keys, the encryption schemes RSAES-OAEP and RSAES-PKCS1-v1_5, and the signature schemes RSASSA-PSS and RSASSA-PKCS1-v1_5.

### Public-Key Cryptography Standards #5 (PKCS#5)

PKCS#5 is a password-based encryption standard that also defines the PKCS5 padding algorithm, which supports only 8-byte padding.

### Public-Key Cryptography Standards #7 (PKCS#7)

PKCS#7 is a standard for encapsulating general messages. The padding rule defined in it is a generalized version of PKCS#5 padding (supporting any block size).

### Poly1305

Poly1305 is a high-speed, one-time message authentication code (MAC) algorithm. It is primarily used to verify the authenticity and integrity of messages between two parties sharing a key, ensuring that messages are not tampered with during transmission. A common use case is combining it with the stream cipher algorithm ChaCha20 to form the ChaCha20-Poly1305 AEAD mode, which provides both confidentiality and integrity.

### Probabilistic Signature Scheme (PSS)

The RSASSA-PSS mode defined in RFC 3447. PSS is a probabilistic padding scheme for RSA signatures. It requires two digests (md and mgf1_md) and allows an optional salt length.

## R

### RC2

A block cipher algorithm with a block size of 64 bits (8 bytes) and a key length from 8 to 1024 bits (in multiples of 8). It supports the ECB, CBC, OFB, and CFB block modes. This algorithm is insecure and not recommended.

### RC4

A stream cipher algorithm that requires no block division or padding, with a key length from 8 to 4096 bits (a multiple of 8). It is an insecure algorithm and is not recommended.

### Random Seed

Data used to initialize the internal state of a pseudo-random number generator, which generates a series of random sequences from the seed.

### RIPEMD160

A message digest algorithm that generates a fixed-length 20-byte (160-bit) digest. It is an insecure algorithm and is not recommended for use.

### Rivest-Shamir-Adleman (RSA)

An asymmetric encryption and signature verification algorithm. Its key specification is determined by the key length (in bits) and the number of prime factors, supporting 512 to 8192 bits and 2 to 5 prime factors. Encryption and decryption support the NoPadding, PKCS1, and PKCS1_OAEP padding modes, while signature verification supports the PKCS1 and PSS padding modes.

## S

### scrypt

A key derivation function that consumes substantial memory and computational resources to generate an encryption key from an input password and salt. Its main parameters include the iteration count n, block size r, and parallelism p, which can be adjusted and optimized based on security requirements and hardware performance.

### Secure Random Number

A random number used in scenarios such as temporary session key generation and asymmetric cryptographic algorithm key generation. It must possess randomness, unpredictability, and non-reproducibility, satisfying the requirements of cryptographically secure pseudo-randomness.

### Secure Hash Algorithm (SHA)

A family of secure hash digest algorithms, including SHA1, SHA224, SHA256, SHA384, and SHA512, which generate fixed-length digests of 20, 28, 32, 48, and 64 bytes, respectively.

### Secure Hash Algorithm 3 (SHA3)

The third generation of the SHA family of digest algorithms, including SHA3-256, SHA3-384, and SHA3-512, which generate fixed-length digests of 32, 48, and 64 bytes, respectively.

### SM2

A public key cryptographic algorithm based on elliptic curves (over the Fp field), used for asymmetric encryption/decryption and signature verification. The encryption result consists of three parts: C1 (an elliptic curve point), C2 (the ciphertext), and C3 (a digest value). Signatures support only the SM3 digest.

### SM3

A message digest algorithm that generates a fixed-length 32-byte (256-bit) digest. It is the default and only supported digest algorithm for SM2 signatures.

### SM4

A block cipher algorithm with a block size of 128 bits and a key length of 128 bits. Both the encryption and key expansion algorithms use a 32-round nonlinear iterative structure. The data decryption and encryption algorithms share the same structure, except that the round keys are used in reverse order.

### Stream Cipher

A symmetric algorithm that encrypts data in a streaming manner. The ciphertext length equals the plaintext length, and no padding is required. ChaCha20 and RC4 are both stream ciphers.

### Symmetric Key

A key system in which the same key is used by both the encryption and decryption parties to encrypt and decrypt data. That is, the sender uses a key and an algorithm to encrypt plaintext into ciphertext, and the receiver uses the same key and the inverse operation of the same algorithm to decrypt and recover the plaintext.

## T

### 3DES Triple Data Encryption Algorithm

Also known as 3DESede or TripleDES, it uses three 64-bit keys to encrypt, decrypt, and encrypt data (equivalent to performing DES three times on each data block). It has a longer key length and higher security than DES, but its processing speed is lower than that of DES. It is an insecure algorithm and is not recommended for use.

## X

### X25519

A Diffie-Hellman key exchange algorithm based on Curve25519, used for key agreement, with a key length of 256 bits.

### X963KDF

A key derivation function based on the X9.63 standard, typically used with elliptic curves to derive a key of a specified length from raw key material and shared information.
