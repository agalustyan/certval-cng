# Changelog
This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html), except that
an increase to the minimum supported Rust version is not treated as a breaking change.

## [0.1.0-rc.1]

Initial release. Calculates SHA-1/256/384/512 digests and verifies RSA PKCS #1 v1.5, RSASSA-PSS and
ECDSA (P-256/384/521) certificate signatures through Windows CNG, through all three of certval's
hashing and verification interfaces. `CngCrypto::fips_mode_enabled` reports the system's FIPS policy.

A `cms` feature implements certval-cms's AES-CBC and AES-GCM content encryption and decryption and
RSA key transport by BCrypt, with `CngRecipientKey` and `CngSigningKey` decrypting and signing with
NCrypt keys, `CertStoreIdentities` finding them in the current user's certificate store and
listing them with `certificates()`, and `import_pkcs8` importing a key into the Microsoft Software
Key Storage Provider. Key agreement uses CNG's ECDH and certval-cms's X9.63 KDF and key wrap, CNG
having no X9.63 KDF.

MSRV 1.89.
