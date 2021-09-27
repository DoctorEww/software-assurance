# Security Requirements Report
Project Wiki - [wiki](https://github.com/DoctorEww/software-assurance/wiki)
## Team Nemo
### Essential Interactions, Diagrams, and Alignment Analysis

* [Login to Account](https://github.com/DoctorEww/software-assurance/blob/main/usecase/login/readme.md)
* [Export Vault](https://github.com/DoctorEww/software-assurance/blob/main/usecase/export_vault/readme.md)
* [Use Password Generator](https://github.com/DoctorEww/software-assurance/blob/main/usecase/password_generator/readme.md)
* [Send Text](https://github.com/DoctorEww/software-assurance/blob/main/usecase/send_text/readme.md)
* [Add Member](https://github.com/DoctorEww/software-assurance/blob/main/usecase/add_member_org/readme.md)

### Use/Misuse Case Diagrams

* [Login to Account](https://github.com/DoctorEww/software-assurance/blob/main/usecase/login/login_use_case_V4.jpg)
* [Export Vault](https://github.com/DoctorEww/software-assurance/blob/main/usecase/export_vault/VaultExportV3.jpg)
* [Use Password Generator](https://raw.githubusercontent.com/DoctorEww/software-assurance/main/usecase/password_generator/Password_V4.jpg)
* [Send Text](https://github.com/DoctorEww/software-assurance/blob/main/usecase/send_text/SendText_V2.drawio.jpg)
* [Add Member](https://github.com/DoctorEww/software-assurance/blob/main/usecase/add_member_org/AddMemberV3.jpg)

### Findings Summary

**1 - Introduction**

As a password manager meant to increase the security of user systems, the essential interactions carried out within the BitWarden Desktop Application by users within the password management system must be appropriately understood. Should these essential interactions be improperly understood, the likelihood of embedded security flaws becomes significant. Toward the goal of better comprehending the threats posed to the BitWarden Desktop Applications we chose the following five essential interactions for the development of security requirements: (1) Login to a BitWarden account, (2) Export a BitWarden vault, (3) Use the password generator within the BitWarden desktop application, (4) Send a secure text from one user to another, and (5) Add a member to a BitWarden Group.

**2 - Commonalities**

In working through the above stated use/misuse case scenarios, we quickly recognized a number of consistently important security requirements within the Bitwarden Desktop Software. These include: weak crypto attacks, network eavesdropping, malicious input, and improperly formed input from users. The mitigations and preventions for each of these common elements include: the use of strong cryptographic functions, the encryption of data both at rest and in motion, input validation and sanitization, and enforced code signing.

**3 - Use Case Summaries**

The findings of each use case are included below.

**3.1 - Login to Account**

Login summary here

**3.2 - Export Vault**

Export summary here

**3.3 - Use Password Generator**

The required security components within the password generator use case include: (1) use strong encryption, (2) use strong random number generator, (3) choose password complexity, (4) star out visible password, and (5) enforce code signing. Strong encryption *mitigates* the exploitation of weak crypto and the accessing previously generated password strings. The use of a strong random number generator *mitigates* standard attacks on weak random number generations that allow an attacker to predict the next generated strings. Choosing password complexity *mitigates* easy to guess strings, while allowing strength to be either increased or decreased based on user discretion. Starring out visible strings *mitigates* screen capture attacks. Finally, the enforcement of code signing *mitigate*s the injection of that malicious code into the software that can bypass security features. 

The BitWarden Desktop application currently provides the following features in *direct reference* to the above stated security requirements: (1) AES-256 encryption, salted hashing, and PDBDF2 SHA-256 *implements* strong encryption, (2) the Electronic Frontier Foundation Open Wireless Random Number Generator *implements* a random number generator, (3)(4) password complexity and on-screen anonymity are *implemented* using the password functionalities in the passwordGeneration JavaScript class, and (5) enforced code signing is *implemented* by the sign.js class.

After the evaluation of existing features against the developed requirements, we reached the following conclusions: (1) AES-256 is adequate encryption, (2) the EFF Open Wireless random number generator *could* be considered a strong random number generator, (3) default password complexity requires at least a 14 character length, but doesn’t require the use of special characters, uppercase letters, or multiple numbers, and could be applied in a stronger sense, (4) on-screen password anonymity is enabled by default and adequately meets minimum requirements, and (5) code signing is enforced via the software.

The only potential weaknesses within the password generation functionality of the BitWarden Desktop Application lie in the potential weakness of the random number generator and the minimal requirements in the default password constraints.

**3.4 - Send Text**

Send Text summary here

**3.5 - Add Member to Group**

Add member summary here

### Reflection
