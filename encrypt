#!/usr/bin/env python

import base64

def encrypt(data, key):
    newdata = [bin(ord(ch)) for ch in data]
    keybin = [bin(ord(ch)) for ch in key]

    result = []
    for i in range(0, len(newdata)):
        x = int(newdata[i], 2)
        y = int(keybin[i % len(keybin)], 2)

        result.append(x ^ y)

    return base64.b64encode(bytes(result)).decode()

def decrypt(data, key):
    decoded = base64.b64decode(data)

    result = []
    for i in range(len(decoded)):
        x = decoded[i]
        y = ord(key[i % len(key)])

        result.append(x ^ y)

    decrypt = ""
    for i in result:
        decrypt += chr(i)

    return decrypt

data = input("Enter data: ")
key = "secret"

# => hello
# => ... encrypted result
enc = encrypt(data, key)
print(enc)

# we have the key
# => ... encrypted result
# => hello
print(decrypt(enc, key))

# we don't have the key
# => ... encrypted result
# => some gibberish output
