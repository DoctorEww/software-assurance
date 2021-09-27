# Security Requirements Report
Project Wiki - [wiki](https://github.com/DoctorEww/software-assurance/wiki)
## Team Nemo
### Essential Interactions, Diagrams, and Alignment Analysis

* [Login to Account](https://github.com/DoctorEww/software-assurance/blob/main/usecase/login/readme.md)
* [Export Vault](https://github.com/DoctorEww/software-assurance/blob/main/usecase/export_vault/readme.md)
* [Use Password Generator](https://github.com/DoctorEww/software-assurance/blob/main/usecase/password_generator/readme.md)
* [Send Text](https://github.com/DoctorEww/software-assurance/blob/main/usecase/send_text/readme.md)
* [Add Member](https://github.com/DoctorEww/software-assurance/blob/main/usecase/add_member_org/readme.md)

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

The required security components within the Send Text use case include: (1) enforcing code signing, (2) set security features, (3) encrypt communications, (4) use a strong encryption, (5) require input validation and sanitization, and (6) enforce whitelists.  The enforcement of code signing would *mitigate* the chance of security features being disabled and if the security features are enabled, the possibility of stealing the URL would be *mitigated*.  Using a strong encryption algorithm would *mitigate* any exploits of weak encryption algorithms, and by making sure all communicaiton across the network is encrypted, the sender can ensure that any network eavesdropping is *mitigated*.  Contained within the send text operation, a sender has several free text blocks that should require input validation and an enforced whitelist in order to *mitigate* any malicious input or attempts to escape input validation.

As it pertains to the request to Send Text, the BitWarden Desktop application addresses the security issues through (1) enforcement of code signing by using sign.js class as well as (2)(3)(4) the use and implementation of AES-256 which is adequately secure.  

When looking at potential weaknesses we discovered that due to the nature of what BitWarden was designed to do, they do not provide much effort in (5)(6) conducting whitelists and input validation and sanitization on the actual message portion of the send text.

**3.5 - Add Member to Group**

Add member summary here

### OSS Project Documentation Review

Review OSS project documentation for security-related configuration and installation issues. Summarize your observations.

### Reflection

While the timeline for this assignment was laborious, the team worked well together in arranging meetings, dividing up tasks, and working together to flesh out ideas. In the initial phases, as we planned out speculated duties and requirements, we chose to develop use cases separately then merge them together and refine each case. As the project progressed, however, we discovered that working individually in this portion of the assignment was less effective. Upon this realization, we pivoted to a more unified approach to developing use and misuse case diagrams and split up for the documentation tasks later on.

Though the amount of work needed to effectively complete this assignment was significant, each member carried out the tasks they were given to the best of their abilities, all the while providing good, high quality of feedback and corrective input to ensure that the team stayed on the correct course moving forward. While there were failures in the initial approach to use case diagramming, the team’s corrective response quickly evened out the course and helped keep the team on track to meet the deadline. 

After carrying out this exercise, our team can confidently state that each member effectively met their objectives, good, corrective feedback occurred regularly, the strengths of each team member helped the team as a whole to reach the objectives required by this project, and the overall progress of the work was steady, high quality, and productive.

