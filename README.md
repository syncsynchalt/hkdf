# hkdf

This tool is used to demonstrate how the HKDF expand and extract
functions are derived from the HMAC and SHA256 cryptographic
primitives.

This tool relies on the `openssl` command line utility.

## Usage

```
  hkdf extract hexsalt hexkey
    - perform the HKDF-Extract function to concentrate key material
  hkdf expand hexprk hexinfo length
    - perform the HKDF-Expand function to generate keys
  hkdf expandlabel hexprk label hexcontext length
    - perform the HKDF-Expand-Label function as defined in RFC 8446 (TLS 1.3)
```

## Examples

```
### example from TLS 1.3 of deriving a handshake secret

$ hkdf extract 00 0000000000000000000000000000000000000000000000000000000000000000
33ad0a1c607ec03b09e6cd9893680ce210adf300aa1f2660e1b22e10f170f92a

$ hkdf expandlabel 33ad0a1c607ec03b09e6cd9893680ce210adf300aa1f2660e1b22e10f170f92a \
  derived e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 32
6f2615a108c702c5678f54fc9dbab69716c076189c48250cebeac3576c3611ba
```
