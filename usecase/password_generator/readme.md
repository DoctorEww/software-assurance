## Use Case: Use Password Generator

### Description:
BitWarden provides a password generator for the dynamic generation of passwords. The generator offers multiple modifiable security parameters to strengthen or weaken the generated password.

### Alignment Analysis:

The security requirements derived through the use/misuse case diagramming process generated the following necessary security-based components:
* *Use Strong Encryption* - Strong encryption is necessary to ensure that previously generated strings cannot be easily accessed by a malicious agent.
* *Use Strong Random Number Generator* - The implementation of a strong random number generator will help mitigate predictable number generation and patterns within generated passwords.
* *Choosing Password Complexity* - The complexity of the password ensures that passwords cannot be easily guessed or cracked.
* *Enforcing Code Signing* - In order to ensure the use of established password complexity functions, enforced code signing will ensure that malicious code does not bypass security features.
* *Starring Out Visible Password* - After an auto-generated password is calculated, the plaintext string is displayed in the clear on-screen. To mitigate threats posed by screen capture malware, the password needs to be starred out.

Security features currently implemented in the BitWarden Desktop Application in regards to the requirements above:
* End to End AES 256
* [zxcvbn Password Checking](https://github.com/dropbox/zxcvbn) - Zxcvbn is a low-cost password checking library that, through pattern matching and complexity calculations, allows for the streamlined estimation of password strength.
* [EFFOrg Open Wireless Random Number Generator](https://github.com/EFForg/OpenWireless/blob/master/app/js/diceware.js) - BitWarden implements the OpenWireless random number generation process originally used by the Electronic Frontier Foundation in their open-source wireless router development project.
* Password complexity is ensured through the 

NOTES
* Max passwords in history: 100
* Defaults 
  * Length: 14
  * One number required
  * No uppercase required

### Diagram:
![](https://raw.githubusercontent.com/DoctorEww/software-assurance/main/usecase/password_generator/Password_V4.jpg)

