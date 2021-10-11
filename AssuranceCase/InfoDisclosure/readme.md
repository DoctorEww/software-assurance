## Assurance Claim 1: The system minimizes information disclosure during communication

[Back to Assurance Cases](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCases.md)

### Alignment Assessment:

BitWarden currently provides the following evidences per the Assurance Case needs E1-E4 in the diagram below:

- **E1**: The crypto service used by the bitwarden app is abstracted in their js-lib. The only form of symmetric encryption declared for use within the app (and the bitwarden library as a whole) is AES (![lines 17-21](https://github.com/bitwarden/jslib/blob/542852a3be13328acac8019a5b358e2608883a43/common/src/abstractions/cryptoFunction.service.ts)). Furthermore, when these funtions are brought out of abstract in the library the aesEncrypt function is hard coded into AES-256-CBC (![line 114](https://github.com/bitwarden/jslib/blob/542852a3be13328acac8019a5b358e2608883a43/node/src/services/nodeCryptoFunction.service.ts#L114)).

- **E2**: Bitwarden pulls bytes from Node's crypto library for salt. Bytes are generated psuedorandomly and it does not mention how or where, only that a entropy requirement must be hit before it will return a value. ![Node claims that the generation is cryptographically strong.](https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback)

- **E3**: Salt is used, not sure how much yet. Appears to be made during runtime since there is no util function made I can find yet.

- **E4**: PKDBF2_SHA256 is the RFC-8018 algoritm used in Bitwarden. ![Bitwarden has it set to run a minimum of 5000 cycles.](https://github.com/bitwarden/jslib/blob/542852a3be13328acac8019a5b358e2608883a43/common/src/services/crypto.service.ts#L432)

### Diagram
![](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/InfoDisclosure/InfoDisclosureV2.jpg)
