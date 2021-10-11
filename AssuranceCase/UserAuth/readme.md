## Assurance Claim 5: The system ensures proper user authentication

[Back to Assurance Cases](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCases.md)

### Description:

Before utilizing any of the password management or messaging functionality of the BitWarden Desktop application, each user must authenticate themselves to the system. Due to the critical nature of this security requirement, assurance is needed to mitigate doubts about authentication functionality in the application. 

### Alignment Assessment:

I. To reasonably assure software security per the Assurance case above, the supporting arguments derived from this top level claim require the following evidence:

	* E1: Password Policy Review
	* E2: Source Code Review: Salt
	* E3: Hardware Randomness Library
	* E4: 2FA Policy Review
	* E5: Password Recovery Report
	* E6: Source Code Review: Login Attempts
	* E7: Source Code Review: Hashing

II. BitWarden currently provides the following evidence per the Assurance Case needs above:

	* E1: Password Policy Review
	* E2: Source Code Review: Salt
	* E3: Hardware Randomness Library – The BitWarden Desktop Application pulls bytes from Node's crypto library for salt. Bytes are generated psuedorandomly and it does not mention how or where, only that a entropy requirement must be hit before it will return a value. ![Node claims that the generation is cryptographically strong.](https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback)
	* E4: 2FA Policy Review
	* E5: Password Recovery Report
	* E6: Source Code Review: Login Attempts
	* E7: Source Code Review: Hashing

### Diagram

![](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/AuthenticationV2.jpg)
