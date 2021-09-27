## Use Case: Use Password Generator

### Description:
BitWarden provides a password generator for the dynamic generation of passwords. The generator offers multiple modifiable security parameters to strengthen or weaken the generated password.

### Alignment Analysis:

I. The security requirements derived through the use/misuse case diagramming process generated the following necessary security-based components:
* *Use Strong Encryption* - Strong encryption is necessary to ensure that previously generated strings cannot be easily accessed by a malicious agent.
* *Use Strong Random Number Generator* - The implementation of a strong random number generator will help mitigate predictable number generation and patterns within generated passwords.
* *Choosing Password Complexity* - The complexity of the password ensures that passwords cannot be easily guessed or cracked.
* *Starring Out Visible Password* - After an auto-generated password is calculated, the plaintext string is displayed in the clear on-screen. To mitigate threats posed by screen capture malware, the password needs to be starred out.
* *Enforcing Code Signing* - In order to ensure the use of established password complexity functions, enforced code signing will ensure that malicious code does not bypass security features.

II. Security features currently implemented in the BitWarden Desktop Application in regards to the requirements above:
* *[End to End AES 256](https://github.com/bitwarden/desktop/blob/64da326be359d6e4b878ad2647e2eedbbb2cf01d/stores/chocolatey/bitwarden.nuspec)* - AES-256 bit encryption, salted hashing and PDBDF2 SHA-256 are utilized to seal data within the BitWarden Desktop Application.
* *[zxcvbn Password Checking](https://github.com/dropbox/zxcvbn)* - Zxcvbn is a low-cost password checking library that, through pattern matching and complexity calculations, allows for the streamlined estimation of password strength.
* *[EFFOrg Open Wireless Random Number Generator](https://github.com/EFForg/OpenWireless/blob/master/app/js/diceware.js)* - BitWarden implements the OpenWireless random number generation process originally used by the Electronic Frontier Foundation in their open-source wireless router development project.
* *Password complexity* **and** *on-screen anonymity* is ensured through the Password Complexity functions within the [passwordGeneration](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/passwordGeneration.service.ts#L157) JavaScript class.
  Defaults:
  * Length: 14
  * One number required
  * No uppercase required
  * No minimum lowercase
  * Special Characters disabled
  * Input Type: password

* Input Sanitization is accomplished in the [passwordGeneartion](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/passwordGeneration.service.ts#L157) class through the removal of characters based on specific input parameters like: minimum number of lowercase and uppercase characters, minimum numbers, and the allowance and minimum of special characters.
* Code verification is currently implemented utilizing new feature requests, push requests, code review, and approval by the community. Code signing is accomplished using the [sign](https://github.com/bitwarden/desktop/blob/c99a543030148ff7d0647007971ca4271730f46f/sign.js) JavaScript class.

### Diagram
![]()
