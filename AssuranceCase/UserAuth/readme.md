## Assurance Claim 5: The system ensures proper user authentication

[Back to Assurance Cases](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCases.md)

### Description:

Before utilizing any of the password management or messaging functionality of the BitWarden Desktop application, each user must authenticate themselves to the system. Due to the critical nature of this security requirement, assurance is needed to mitigate doubts about authentication functionality in the application. 

### Alignment Assessment:

BitWarden currently provides the following evidences per the Assurance Case needs E1-E7 in the diagram below:

* E1: *Password Policy Review* - The system uses a password generation [protocol](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/passwordGeneration.service.ts#L204) that requires the following default characteristics:
  * Minimum Length: 14
  * At least one number
  * No upper or lower case requirements
  * There must be at least one special character.

  Further, the application uses [Zxcvbn](https://github.com/dropbox/zxcvbn) to measure password strength per the user's input, but also as a means to ensure passwords are effectively hashed to mitigate collisions. 
  
  There is a gap in the assurance required to reduce doubts per the strength of the password. To meet assurance needs, the password must require special characters outside the first and last politions, as well as at least one special, upper, and lower characters.
* E2: *Source Code Review: Salt* - The system utilizes the Node [pbkdf2](https://nodejs.org/api/crypto.html#crypto_crypto_pbkdf2_password_salt_iterations_keylen_digest_callback) function for key derivation. As such, a salt length is required and is *recommended* to be at least 16 bytes long, however, the length is not enforced. This indicates a slight *gap* between the necessary assurance requirements and the implemented features of the system in that a sufficient length salt is *recommended* rather than *enforced*.
* E3: *Hardware Randomness Library* – The BitWarden Desktop Application pulls random bytes from Node's crypto library using the randomBytes callback. Per the claims of Node [documentation](https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback), the randomBytes function will not complete until there is sufficient entropy. Bytes are generated psuedorandomly, however, the mechanics of the pseudorandom generation are obscure. While Node documentation indicates the existence sufficient entropy, further documentation is unavailable. This creates a *gap* due to insufficient evidence of entropy.
* E4: *2FA Policy Review* - BitWarden provides a two-factor authentication [protocol](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/angular/src/components/two-factor.component.ts). This protocol allows two forms of 2FA access: (1) email, and (2) the use of web authorizations like Duo or Google Authenticator. While sending and receiving 2FA requests, BitWarden utilizes a [two-factor component](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/angular/src/components/two-factor.component.ts) and an [authorization component](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/auth.service.ts#L79) that enforce proper encryption and authentication.
* E5: *Password Recovery Report* - By way of risk avoidance, the BitWarden Desktop Applicattion disallows any master password recovery. Available documentation can be found [here](https://github.com/bitwarden/desktop/blob/004f18e04d62155327236ed74ed3554914404bb7/src/locales/en_IN/messages.json).
* E6: *Source Code Review: Login Attempts* - The BitWarden login [process](https://github.com/bitwarden/jslib/blob/16e998e66495a159df3678202c75c6eb035864ff/angular/src/components/login.component.ts) does no currently utilize any security measures aimed at reducing repeated, failed login attempts. This establishes a wide *gap* between the assurance requirements for the software and the actual implementations available. 
* E7: *Source Code Review: Hashing* - SHA256 or SHA512 are both available for use within the scope of the BitWarden application. The SHA256 option remains the default used by the system. Supporting evidence can be found [here](https://github.com/bitwarden/jslib/blob/d7682cde3bac4f4a8403b5573bf5feaa4c47172c/node/src/services/nodeCryptoFunction.service.ts#L224).

### Diagram

![](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/AuthenticationV3.jpg)
