# PQC FIPS (General Questions)

## Q:Are cryptographic modules implementing FIPS 203 or FIPS 204 allowed to use seeds as the default key format instead of expanded keys? For example, in FIPS 203, can a cryptographic module store a 64-byte seed (d, z) instead of the output (dk, ek) of Algorithm 19 (ML-KEM.KeyGen), and compute (dk, ek) as needed via (dk, ek) <-- ML-KEM.KeyGen_internal(d, z)?
(Last revised: January 30, 2025)

For both FIPS 203 and FIPS 204, a KeyGen seed is considered an acceptable alternative format for a key-pair, or for the private (i.e., decapsulation or signing) key. In particular, generating the seed in one cryptographic module and then importing or exporting it into another cryptographic module is allowed. The internal key generation functions ML-KEM.KeyGen_Internal(d, z) and ML-DSA.KeyGen_internal(ξ) can be accessed for this purpose. 

## Q: FIPS 204 Section 6 states that the internal interfaces in this section should not be made available to applications, and that the interfaces in Section 5 should be used instead. The interfaces in Section 5 are not sufficient to allow an implementation to compute mu externally and provide it to the signing implementation. Will the Cryptographic Module Validation Program allow this in FIPS validated modules, and how? (Last Revised: March 19, 2025)

Please see NIST's response [PDF]