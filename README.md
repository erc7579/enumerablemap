# Libraries for ERC-4337 compatible dynamic arrays in storage.

## Motivation
Dynamic array are not easily compatible with ERC-4337 [associated storage](https://eips.ethereum.org/EIPS/eip-7562#validation-rules) access rules. Even if they are a value in a mapping, where the Smart Account address is the key, the final keccak won't be `keccak(A||x)+n` as it would be for a static array, but `keccak(keccak(A||x))+n` instead.

## What's included
- AssociatedArrayLib.sol: Library for dynamic arrays that are associated with an address as per [ERC-7562](https://eips.ethereum.org/EIPS/eip-7562). It is achieved by using `keccak(A||x)` as the starting slot for the array.
- EnumerableSet4337.sol: Fork of OZ's EnumerableSet that makes all storage access ERC-4337 compliant via associated storage. Stores indexes in a mapping making access to a given value easier.
- EnumerableMap4337.sol: Library for managing an enumerable variant of Solidity's [`mapping`](https://solidity.readthedocs.io/en/latest/types.html#mapping-types) type.

## Disclaimer
These libraries are provided as-is, without any warranty or guarantee of any kind. Use them at your own risk.
