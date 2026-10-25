# Field notes: Guestbook

**JWT algorithm confusion and verifier policy**

## A token header is input, not a policy

A JSON Web Token (JWT) carries a header, claims, and a signature. The header travels with the token, so a verifier must choose allowed algorithms from server policy. Letting an untrusted `alg` value choose the verification routine can cross key types: public key bytes intended for asymmetric verification can accidentally become an HMAC secret.

This failure pattern is called algorithm confusion. Inspect the captured token’s claims and the service’s verification path. Compare the legitimate RSA configuration with the legacy preview branch. A safe verifier pins one algorithm, uses a key of the expected type, validates issuer and audience, and rejects unexpected headers. It should rely on a maintained JWT library instead of a home-grown parser.

The lab binds only to localhost. Construct the token for this synthetic preview desk and submit it to the local endpoint; no real account or website is involved.

Learning reference: [PortSwigger Web Security Academy: JWT algorithm confusion](https://portswigger.net/web-security/jwt/algorithm-confusion).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
