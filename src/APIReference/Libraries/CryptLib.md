# Crypt Library

## Hash:

### SHA-384 Hash:
```lua
<string> sha384_hash(<string> Data)
Aliases: Krnl.crypt.hash
```
Hashes `Data` with SHA-384.

### MD5 Hash:
```lua
<string> crypt_hash(<string> Data, <string> Unknown)
```
Hashes `Data` with MD5.

You must provide a second argument as a string or the function will error. (Af of June 10, 2022)

---

## Base64:

### Encode:
```lua
<string> base64_encode(<string> Data)
Aliases: Krnl.Base64.Encode
```
Encodes `Data` with Base64.

### Decode:
```lua
<string> base64_decode(<string> Data)
Aliases: Krnl.Base64.Decode
```
Decodes `Data` with Base64.

---

## LZ4 Compress:
```lua
<string> lz4compress(<string> Data)
```
Compresses `Data` with LZ4.