## Use Case: Login to Account

[Back to Security Requirements](https://github.com/DoctorEww/software-assurance/blob/main/SecurityRequirements.md)

### Description:
To utilize the BitWarden password manager, each user must first login to an account. While logging in, the software design must mitigate security threats to ensure the use of the software remains secure.

### Alignment Analysis:

I. The security requirements derived through the use/misuse case diagramming process generated the following necessary security-based components:
* *Use Strong Encryption* - Strong encryption is necessary to ensure that an attacker can not intercept information and view it while syncing the database.
* *Use Computationally Complex Password Hashing* - The implementation of computationally complex password hashing will help reduce the risk of database theft. These measures significantly increase the time it takes to obtain a user's master password if the hash is stolen. Although, this is no substitute for a complex password. 
* *Use Input Validation and Sanitation* - Using input validation and sanitation ensures that a malicious user would not be able to exploit the login function to execute code or bypass authentication. 
* *Use Two Factor Authentication* - Using two-factor authentication reduces the impact of a master password being compromised. 

II. Security features currently implemented in the BitWarden Desktop Application in regards to the requirements above:
* The application uses RSA-2048 to share the key with the authentication server as detailed [here](https://bitwarden.com/help/article/what-encryption-is-used/).
* The application uses PBKDF2 SHA-256 to store passwords securely.  PBKDF2 SHA-256 includes a local 100,001 rounds of password hashing with the email address as a salt and 100,000 rounds of password hashing on the server-side by default. The number of rounds the password is hashed is configurable. This process is detailed [here](https://bitwarden.com/help/article/what-encryption-is-used/). We can see the login cryptography code [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/auth.service.ts#L124) and [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/crypto.service.ts#L480).
* This application offers several different methods of two-factor authentication, including Authenticator app (ex. Google Authenticator), Email, Duo Security, YubiKey, FIDO as detailed [here](https://bitwarden.com/help/article/setup-two-step-login/). 
These options can be viewed in the codebase [here](https://github.com/bitwarden/desktop/blob/a76f8749ca38e0f2de702a67b0588296c17b1f56/src/app/accounts/two-factor.component.html).

* This application does not use any insecure functions for code injection to execute as shown [here](https://github.com/bitwarden/jslib/blob/2c892eb3a2a9aff1e238146b037e6f3eb5dacf9a/angular/src/components/login.component.ts). This application verifies that an email contains a @ sign [here](https://github.com/bitwarden/jslib/blob/2c892eb3a2a9aff1e238146b037e6f3eb5dacf9a/angular/src/components/hint.component.ts). 

### Diagram:


![](https://github.com/DoctorEww/software-assurance/blob/main/usecase/login/login_use_case_V4.jpg)

