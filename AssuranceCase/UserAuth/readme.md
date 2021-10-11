[BACK](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCases.md)
### Claim 5 - The system ensures proper user authentication

### Diagram
![](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/AuthenticationV2.jpg)

### Alignment Assessment

- **E1**: 

- **E2**: 

- **E3**: Bitwarden pulls bytes from Node's crypto library for salt. Bytes are generated psuedorandomly and it does not mention how or where, only that a entropy requirement must be hit before it will return a value. ![Node claims that the generation is cryptographically strong.](https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback)

- **E4**: 

- **E5**:

- **E6**:  

- **E7**: SHA256