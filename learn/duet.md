# Field notes: Duet

**RSA mathematics and modular arithmetic**

## When an RSA modulus is reused

RSA encryption computes a modular power. If the same message is encrypted under one modulus with two public exponents, the ciphertexts are related. When the exponents are coprime, Bézout’s identity supplies integers whose weighted sum is one. Raising the ciphertexts to those powers reconstructs the original message modulo the shared modulus. One coefficient may be negative; modular inversion handles it when the ciphertext is invertible.

Raw RSA is intentionally used here so the relationship stays visible. Real protocols need randomized, well-reviewed padding such as OAEP. Reusing a modulus across applications is also a serious key-management failure. This lab’s capture includes damaged and unrelated rows, so pair the records by modulus, test exponent gcds, then use the inventory’s key commitment to identify the accepted capsule. Preserve leading zero bytes when converting the integer back to bytes.

Try a tiny example with hand-sized primes, compute the greatest common divisor of the exponents, and verify the result by re-encrypting. Then apply the same algebra to the supplied transcripts and decrypt the authenticated envelope.

Learning reference: [Python modular exponentiation](https://docs.python.org/3/library/functions.html#pow) and [RSA guidance](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/rsa/).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
