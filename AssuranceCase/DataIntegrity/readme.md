## Assurance Claim 3: The system protects data integrity during transmission

[Back to Assurance Cases](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCases.md)

### Description:
As an application tasked with securing transmissions from both prying eyes and data contamination, the BitWarden Desktop application must reasonably assure the integrity of the data it transmits. More specifically, during password synchronization, any deprecation of the data can cause a number of significant security issues.

### Alignment Assessment

BitWarden currently provides the following evidence per the Assurance Case needs E1-E6 in the diagram below:

- **E1**: A review of the source code to verify that all send requests have a default time setting that will automatically delete the sent message after a predetermined amount of time as well as purging the data from the database once the set time or default time has occurred.

- **E2**: The crypto service used by the bitwarden app is abstracted in their js-lib. The only form of symmetric encryption declared for use within the app (and the bitwarden library as a whole) is AES ([lines 17-21](https://github.com/bitwarden/jslib/blob/542852a3be13328acac8019a5b358e2608883a43/common/src/abstractions/cryptoFunction.service.ts)). Furthermore, when these functions are brought out of abstract in the library the aesEncrypt function is hard coded into AES-256-CBC ([line 114](https://github.com/bitwarden/jslib/blob/542852a3be13328acac8019a5b358e2608883a43/node/src/services/nodeCryptoFunction.service.ts#L114)).

- **E3**: Bitwarden pulls bytes from Node's crypto library for salt. Bytes are generated psuedorandomly and it does not mention how or where, only that an entropy requirement must be hit before it will return a value. [Node claims that the generation is cryptographically strong.](https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback)

- **E4**: A review of the source code to ensure that the salt length is greater than 32 bytes.

- **E5**: PKDBF2_SHA256 is the RFC-8018 algorithm used in Bitwarden. [Bitwarden has it set to run a minimum of 5000 cycles.](https://github.com/bitwarden/jslib/blob/542852a3be13328acac8019a5b358e2608883a43/common/src/services/crypto.service.ts#L432)

- **E6**: A review of the source code to verify that password input hides the password as user is typing it in and allows for the user to toggle the visibility of the password.  As of this time, Bitwarden does not implement this type of security and only hides the sender's email address when the recipient opens the send request and it is protected with a password. 

### Diagram
![](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/DataIntegrity/DataIntegrityV2.jpg)

