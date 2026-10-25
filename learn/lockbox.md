# Field notes: Lockbox

**Packed variables, mappings and Ethereum Keccak**

## Private storage is still public chain data

In Solidity, `private` controls visibility in the contract language. It does not encrypt a state variable or hide it from blockchain readers. Storage is a sequence of 32-byte words. Small adjacent values can be packed into one word, and mappings use a hash of the padded key and the mapping’s declared slot.

Use the source declaration order to locate each variable. A 96-bit integer occupies 12 bytes; the following address fills the remaining 20 bytes of that slot. The mapping starts at the next slot. To locate a mapping value, encode the key as a 32-byte left-padded value, append the mapping slot as a 32-byte word, then compute Ethereum Keccak-256. Ethereum Keccak is not NIST SHA3-256 despite their shared ancestry.

The supplied storage snapshot is synthetic and offline. Extract the raw 32-byte value, derive the documented key, and authenticate the sealed note. No wallet, RPC provider, token, or funds are required.

Learning reference: [Solidity storage layout](https://docs.soliditylang.org/en/latest/internals/layout_in_storage.html).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
