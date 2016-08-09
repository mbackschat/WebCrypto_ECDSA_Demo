# Web Crypto ECDSA Demo

This Javascript code demonstrates the following [Web Crypto](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API) operations:

1. **generateKey**: Generate a ECDSA private/public key pair for the NIST P-256 curve.
1. **exportKey (JWK)**: Export both keys to JSON Web Key format.
1. **importKey & sign**: Read private key back from JWK and sign a test message.
1. **importKey & verify**: Read public key back from JWK and verify the signature against
    1. original test message (which should succeed) and
    1. tampered test message (which should detect the tampering).

The code also demonstrates how to convert back and forth between [ArrayBuffers](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer), which are used for representing binary data with Web Crypto, and [Base64](https://en.wikipedia.org/wiki/Base64).

Author: [github.com/mbackschat](https://github.com/mbackschat)

## Output

```
------ generateKeys:
Public/private key generated.

------ exportKeys:
JWK Public key:
{"crv":"P-256","ext":true,"key_ops":["verify"],"kty":"EC","x":"ApLm8aljIuJZCr70JsSNUWuvXl9FfhenNYNyKvYA758","y":"NkKTXu7O8Ll6ZKEnxSDiQc0qC8J0CY5ccP4sPL5qjyQ"}

JWK Private key:
{"crv":"P-256","d":"_42O-lqXhcrbCzPnUnaNKPQa8XxH9nWvrF6ehQnwtjQ","ext":true,"key_ops":["sign"],"kty":"EC","x":"ApLm8aljIuJZCr70JsSNUWuvXl9FfhenNYNyKvYA758","y":"NkKTXu7O8Ll6ZKEnxSDiQc0qC8J0CY5ccP4sPL5qjyQ"}

Imported public and private keys into JWK JSON.

------ importPrivateKeyAndSign:
Signature: [object ArrayBuffer]
MbuBd4hO2EQotWbVpzVPoOAIh8MJJOd16Rrj1HgsApex/8WQAWZRnO8O9v7sttHDBrKrF8DccdUjrJ3/1tE3Rg==

------ importPublicKeyAndVerify:
Verified successfully.

------ importPublicKeyAndVerifyTamperedData:
Verification returned 'false'! That's OK since it's tampered data.
```

