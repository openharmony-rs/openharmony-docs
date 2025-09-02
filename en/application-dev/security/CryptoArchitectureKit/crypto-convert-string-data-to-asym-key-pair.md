# Converting a PEM String into an Asymmetric Key Pair (ArkTS)

This topic walks you through on how to convert a string in PEM format into an RSA asymmetric key pair (**KeyPair**).

> **NOTE**
>
> The **convertPemKey** operation must comply with the following requirements: 
>
> - The public key must comply with X.509 specifications, PKCS\#1 specifications, and PEM encoding format.
>
> - The private key must comply with the PKCS\#8, PKCS\#1 specifications, and the PEM encoding format.
>
> - Currently, only RSA asymmetric keys can be converted.

## Converting a String in PEM Format into an RSA Key Pair

For details about the algorithm specifications, see [RSA](crypto-asym-key-generation-conversion-spec.md#rsa).

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) with the string parameter **'RSA1024'** to create an asymmetric key generator (**AsyKeyGenerator**) object for a 1024-bit RSA key with two primes.

   The default number of primes for creating an RSA asymmetric key is **2**. The **PRIMES_2** parameter is omitted in the string parameter here.

2. Call [AsyKeyGenerator.convertPemKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertpemkey12) to convert the binary data into an asymmetric key pair (**KeyPair**).
3. Call [AsyKeyGenerator.getEncodedPem](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencodedpem12) to convert the public key in the asymmetric key object into the PKCS #1 or X509 format and the private key into the PKCS #1 or PKCS #8 format.

- Example: Convert a string in PEM format into an RSA key pair (using promise-based APIs).

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';

  let priKeyPkcs1Str1024: string  =
    "-----BEGIN RSA PRIVATE KEY-----\n"
    + "MIICXQIBAAKBgQCwIN3mr21+N96ToxnVnaS+xyK9cNRAHiHGgrbjHw6RAj3V+l+W\n"
    + "Y68IhIe3DudVlzE9oMjeOQwkMkq//HCxNlIlFR6O6pa0mrXSwPRE7YKG97CeKk2g\n"
    + "YOS8YEh8toAvm7xKbiLkXuuMlxrjP2j/mb5iI/UASFSPZiQ/IyxDr0AQaQIDAQAB\n"
    + "AoGAEvBFzBNa+7J4PXnRQlYEK/tvsd0bBZX33ceacMubHl6WVZbphltLq+fMTBPP\n"
    + "LjXmtpC+aJ7Lvmyl+wTi/TsxE9vxW5JnbuRT48rnZ/Xwq0eozDeEeIBRrpsr7Rvr\n"
    + "7ctrgzr4m4yMHq9aDgpxj8IR7oHkfwnmWr0wM3FuiVlj650CQQDineeNZ1hUTkj4\n"
    + "D3O+iCi3mxEVEeJrpqrmSFolRMb+iozrIRKuJlgcOs+Gqi2fHfOTTL7LkpYe8SVg\n"
    + "e3JxUdVLAkEAxvcZXk+byMFoetrnlcMR13VHUpoVeoV9qkv6CAWLlbMdgf7uKmgp\n"
    + "a1Yp3QPDNQQqkPvrqtfR19JWZ4uy1qREmwJALTU3BjyBoH/liqb6fh4HkWk75Som\n"
    + "MzeSjFIOubSYxhq5tgZpBZjcpvUMhV7Zrw54kwASZ+YcUJvmyvKViAm9NQJBAKF7\n"
    + "DyXSKrem8Ws0m1ybM7HQx5As6l3EVhePDmDQT1eyRbKp+xaD74nkJpnwYdB3jyyY\n"
    + "qc7A1tj5J5NmeEFolR0CQQCn76Xp8HCjGgLHw9vg7YyIL28y/XyfFyaZAzzK+Yia\n"
    + "akNwQ6NeGtXSsuGCcyyfpacHp9xy8qXQNKSkw03/5vDO\n"
    + "-----END RSA PRIVATE KEY-----\n";
  let publicPkcs1Str1024: string  =
    "-----BEGIN RSA PUBLIC KEY-----\n"
    + "MIGJAoGBALAg3eavbX433pOjGdWdpL7HIr1w1EAeIcaCtuMfDpECPdX6X5ZjrwiE\n"
    + "h7cO51WXMT2gyN45DCQySr/8cLE2UiUVHo7qlrSatdLA9ETtgob3sJ4qTaBg5Lxg\n"
    + "SHy2gC+bvEpuIuRe64yXGuM/aP+ZvmIj9QBIVI9mJD8jLEOvQBBpAgMBAAE=\n"
    + "-----END RSA PUBLIC KEY-----\n";
  async function TestPkcs1ToPkcs8ByPromise() {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
    let keyPair = await asyKeyGenerator.convertPemKey(publicPkcs1Str1024, priKeyPkcs1Str1024);
    let priPemKey = keyPair.priKey;
    let pubPemKey = keyPair.pubKey;
    let priString = priPemKey.getEncodedPem('PKCS8');
    let pubString = pubPemKey.getEncodedPem('X509');
    console.info("[promise]TestPkcs1ToPkcs8ByPromise priString output is " + priString);
    console.info("[promise]TestPkcs1ToPkcs8ByPromise pubString output is " + pubString);
  }
  ```

- Example: Convert a string in PEM format into an RSA key pair (using the synchronous API [convertPemKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertpemkeysync12)).

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';

  let priKeyPkcs1Str1024: string  =
    "-----BEGIN RSA PRIVATE KEY-----\n"
    + "MIICXQIBAAKBgQCwIN3mr21+N96ToxnVnaS+xyK9cNRAHiHGgrbjHw6RAj3V+l+W\n"
    + "Y68IhIe3DudVlzE9oMjeOQwkMkq//HCxNlIlFR6O6pa0mrXSwPRE7YKG97CeKk2g\n"
    + "YOS8YEh8toAvm7xKbiLkXuuMlxrjP2j/mb5iI/UASFSPZiQ/IyxDr0AQaQIDAQAB\n"
    + "AoGAEvBFzBNa+7J4PXnRQlYEK/tvsd0bBZX33ceacMubHl6WVZbphltLq+fMTBPP\n"
    + "LjXmtpC+aJ7Lvmyl+wTi/TsxE9vxW5JnbuRT48rnZ/Xwq0eozDeEeIBRrpsr7Rvr\n"
    + "7ctrgzr4m4yMHq9aDgpxj8IR7oHkfwnmWr0wM3FuiVlj650CQQDineeNZ1hUTkj4\n"
    + "D3O+iCi3mxEVEeJrpqrmSFolRMb+iozrIRKuJlgcOs+Gqi2fHfOTTL7LkpYe8SVg\n"
    + "e3JxUdVLAkEAxvcZXk+byMFoetrnlcMR13VHUpoVeoV9qkv6CAWLlbMdgf7uKmgp\n"
    + "a1Yp3QPDNQQqkPvrqtfR19JWZ4uy1qREmwJALTU3BjyBoH/liqb6fh4HkWk75Som\n"
    + "MzeSjFIOubSYxhq5tgZpBZjcpvUMhV7Zrw54kwASZ+YcUJvmyvKViAm9NQJBAKF7\n"
    + "DyXSKrem8Ws0m1ybM7HQx5As6l3EVhePDmDQT1eyRbKp+xaD74nkJpnwYdB3jyyY\n"
    + "qc7A1tj5J5NmeEFolR0CQQCn76Xp8HCjGgLHw9vg7YyIL28y/XyfFyaZAzzK+Yia\n"
    + "akNwQ6NeGtXSsuGCcyyfpacHp9xy8qXQNKSkw03/5vDO\n"
    + "-----END RSA PRIVATE KEY-----\n";
  let publicPkcs1Str1024: string  =
    "-----BEGIN RSA PUBLIC KEY-----\n"
    + "MIGJAoGBALAg3eavbX433pOjGdWdpL7HIr1w1EAeIcaCtuMfDpECPdX6X5ZjrwiE\n"
    + "h7cO51WXMT2gyN45DCQySr/8cLE2UiUVHo7qlrSatdLA9ETtgob3sJ4qTaBg5Lxg\n"
    + "SHy2gC+bvEpuIuRe64yXGuM/aP+ZvmIj9QBIVI9mJD8jLEOvQBBpAgMBAAE=\n"
    + "-----END RSA PUBLIC KEY-----\n";
  function TestPkcs1ToPkcs8BySync() {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
    try {
      let keyPairData = asyKeyGenerator.convertPemKeySync(publicPkcs1Str1024, priKeyPkcs1Str1024);
      if (keyPairData !== null) {
        console.info('[Sync]: convert pem key pair success');
      } else {
        console.error("[Sync]: convert pem key pair result fail!");
      }
      let priPemKey = keyPairData.priKey;
      let pubPemKey = keyPairData.pubKey;
      let priString = priPemKey.getEncodedPem('PKCS8');
      let pubString = pubPemKey.getEncodedPem('X509');
      console.info("[Sync]TestPkcs1ToPkcs8BySync priString output is " + priString);
      console.info("[Sync]TestPkcs1ToPkcs8BySync pubString output is " + pubString);
    } catch (e) {
      console.error(`Sync error, ${e.code}, ${e.message}`);
    }
  }
  ```
