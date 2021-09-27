## Use Case: Export BitWarden Vault

### Description:
Each BitWarden user maintains a vault of secure logins, credit cards, messages, and files. To extract data, BitWarden allows each users' vault to be exported into various formats. The essential security functionality provided by the exporting of sensitive data necessitates the analysis of security requirements needed to facilitate a sufficiently secure environment.

### Alignment Analysis:

I. The security requirements derived through the use/misuse case diagramming process generated the following necessary security-based components:
* *SSL/TLS Restrictions* - Previous versions of SSL and TLS have been broken or bame cryptographically weak and should no longer be used. TLS 1.3 should be enabled and all previous versions disabled.
* *Transport Layer Security* - When communicating with remote servers to sync credentials communications should not take place in the clear. TLS should be used to prevent tampering or theft while in transit.
* *Credential Hashing* - Credentials being used as keys should be hashed before being transported over the wire. 
* *Vault Encryption* - The exported vault should be encrypted or password protected.
* *Strong Cryptography* - A robust encryption suite should be used for all sensitive data.

II. Security features currently implemented in the BitWarden Desktop Application in regards to the requirements above:
* *[End to End AES 256](https://github.com/bitwarden/desktop/blob/64da326be359d6e4b878ad2647e2eedbbb2cf01d/stores/chocolatey/bitwarden.nuspec)* - To encrypt credentials and data within Bitwarden Desktop, AES 256 in CBC mode is used with keys generated from salted PBKDF2_SHA256 hashes.
* *[TLS v1.2+ required(https://bitwarden.com/images/resources/bitwarden-network-security-assessment-report-2021.pdf)]* Bitwarden requires TLS 1.2 or 1.3 across their whole domain as of June 2021. This is set up through their service provider Cloudflare.
* *[Vault Encryption Option](https://bitwarden.com/help/article/encrypted-export/)* - User has the option of exporting encrypted vaults in JSON format. Credentials are AES-256 encrypted using the account masterkey similar to how they are stored in the Desktop application’s files. This is not the default selection.

III. Observations:
The only option that does not fall into line would be export vault not defaulting to encrypted file format. The JSON and CSV options will export in plaintext unless the user chooses not to, which poses a security risk since there will be a free-floating plain file with all credentials in it. This toes the line of accessibility vs security. A user might want to export their credentials to a different utility where they would have to have them in plaintext. Bitwarden surely doesn’t want to make an API for competitors to get the credentials securely from, and the encrypted JSON file can only be encrypted by Bitwarden’s utilities. Perhaps an option to export a zip or similar file might be proposed instead.

### Diagram:
![](https://github.com/DoctorEww/software-assurance/blob/main/usecase/export_vault/VaultExportV3.jpg)

