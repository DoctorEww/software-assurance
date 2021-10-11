## Assurance Claim 5: The system ensures proper user authentication

[Back to Assurance Cases](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCases.md)

### Description:

Before utilizing any of the password management or messaging functionality of the BitWarden Desktop application, each user must authenticate themselves to the system. Due to the critical nature of this security requirement, assurance is needed to mitigate doubts about authentication functionality in the application. 

### Alignment Assessment:

I. To reasonably assure software security per the Assurance case above, the supporting arguments derived from this top level claim require the following evidence:

* E1: *Password Policy Review*
* E2: *Source Code Review: Salt*
* E3: *Hardware Randomness Library*
* E4: *2FA Policy Review*
* E5: *Password Recovery Report*
* E6: *Source Code Review: Login Attempts*
* E7: *Source Code Review: Hashing*

II. BitWarden currently provides the following evidence per the Assurance Case needs above:

* E1: *Password Policy Review* - The system uses a password generation [protocol](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/passwordGeneration.service.ts#L204) that requires the following default characteristics:
  * Minimum Length: 14
  * At least one number
  * No upper or lower case requirements
  * There must be at least one special character.

  Further, the application uses [Zxcvbn](https://github.com/dropbox/zxcvbn) to measure password strength per the user's input, but also as a means to ensure passwords are effectively hashed to mitigate collisions. 
  
  There is a gap in the assurance required to reduce doubts per the strength of the password. To meet assurance needs, the password must require special characters outside the first and last politions, as well as at least one special, upper, and lower characters.
* E2: *Source Code Review: Salt* - The system utilizes the Node [pbkdf2](https://nodejs.org/api/crypto.html#crypto_crypto_pbkdf2_password_salt_iterations_keylen_digest_callback) function for key derivation. As such, a salt length is required and is *recommended* to be at least 16 bytes long, however, the length is not enforced. This indicates a slight *gap* between the necessary assurance requirements and the implemented features of the system in that a sufficient length salt is *recommended* rather than *enforced*.
* E3: *Hardware Randomness Library* – The BitWarden Desktop Application pulls random bytes from Node's crypto library using the randomBytes callback. Per the claims of Node [documentation](https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback), the randomBytes function will not complete until there is sufficient entropy. Bytes are generated psuedorandomly and it does not mention how or where. While Node documentation indicates the existence sufficient entropy, further documentation is unavailable. This creates a *gap* due to insufficient evidence of entropy.
* E4: *2FA Policy Review*
* E5: *Password Recovery Report*
* E6: *Source Code Review: Login Attempts*
* E7: *Source Code Review: Hashing*

### Diagram

![](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/AuthenticationV3.jpg)
