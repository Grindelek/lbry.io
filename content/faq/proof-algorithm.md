---
title: What is LBRY's proof algorithm?
category: mining
---

## What is LBRY's proof algorithm?

LBRY uses [proof of work](https://en.bitcoin.it/wiki/Proof_of_work) the same way that Bitcoin does. The
only difference is the hash function. LBRY uses a sligthly different algorithm that achieves the same 
ends but slightly delayed the development of a GPU miner and gave early adopters a chance to 
mine without specialized hardware.

LBRY's algorimth is

```python
intermediate = sha512(sha256(sha256(data)))  # compute the sha512() of the double-sha256() of the data
left = ripemd(intermediate[:len(intermediate)/2])  # separately ripemd160 the left half
right = ripemd(intermediate[len(intermediate)/2:]) # and the right half
proof = sha256(sha256(left + right))  # concatenate the two halves, and double-sha256() it again
```

For comparison, Bitcoin's algorimth is 

```python
proof = sha256(sha256(data))
```
