## Use Case: Add a Member to Group

[Back to Security Requirements](https://github.com/DoctorEww/software-assurance/blob/main/SecurityRequirements.md)

### Description:
BitWarden allows the creation and modification of user level groups for the sharing of accounts, logins, messages, and other secure features. To expand a group, privileged users must add other BitWarden members. To ensure the security of the BitWarden group accounts, the security requirements for the group functionality must be considered.

### Alignment Analysis:

I. After developing and analyzing the use/misuse case diagram, a few key components that could bolster security were identified. They include the following:

* *Input Validation* - With numerous input fields involved in the process, it is critical that the input supplied to the Bitwarden application be verified. This would ensure proper functionality of the application, even when there is unexpected input.

* *Input Sanitation* - After input has been verified, it is important that the input be sanitized in order to prevent any malicious attacks. A weak input field would be enough to act as an attack vector. Sanitation further prevents any situation in which an attacker may seek to escape input validation measures.

* *Encrypting Communications* - Involving communication between users would require encrypted communications. It is important that the intended recipient is securely able to receive and view the contents of the information being sent. Encryption would ensure a malicious user cannot listen in on the network and grab the information before the true recipient acquires it.

* *Use Strong Encryption* - Bolstering the encryption of communications, it would be critical that the encryption used is strong. While encrypted communications provide security from viewing, they also need to be resilient to being broken down by a malicious user. Strong encryption ensures that an attack could not exploit weak encryption algorithms and view the contents of the encrypted message.

II. Security features currently implemented in the BitWarden Desktop Application in regards to the requirements above:

* When it comes to adding a member, there seems to be a good grasp of input validation, however, the input sanitation seems to be improperly implemented. When submitting an unexpected input such as "<script>alert(1)</script>" or "<script>", the application will throw a few errors and forcibly sign the user out. "\<a>" on the other hand is recognized during the input validation phase and the program prompts the user to enter a valid email.
  
* *[End to End AES 256](https://github.com/bitwarden/desktop/blob/64da326be359d6e4b878ad2647e2eedbbb2cf01d/stores/chocolatey/bitwarden.nuspec)* - Data is encrypted using AES 256 in CBC with keys generated from salted PBKDF2 SHA256 hashes.

### Diagram:
![](https://github.com/DoctorEww/software-assurance/blob/main/usecase/add_member_org/AddMemberV3.jpg)

