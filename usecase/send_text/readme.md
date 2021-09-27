## Use Case: Send a Text Message

### Description:
While using BitWarden, each user has the opportunity to send secure messages to other BitWarden users. As an essential function within the BitWarden desktop application, a full analysis of the security requirements when sending texts will help secure the overall program.

### Alignment Analysis:

Disable Security Feature:
Team’s Recommended Mitigation: Enforce Code Signing
Bitwarden’s Implemented Mitigation: Every sent item uses a new 128-bit secret key and a 512-bit encryption key is derived from that secret key.  The derived key is then used to encrypt the sent file using AES-256 including the file/text data and metadata.
Steal URL:
Team’s Recommended Mitigation: Set Security Features
Bitwarden’s Implemented Mitigation: The URL that is sent is encrypted using AES-256 during the send process.  The send is uploaded to Bitwarden servers and it contains a unique ID that is used to decrypt.  The encryption key is never included in the network requests.  A password protected send can also require additional authentication prior to decryption.
Network Eavesdrop:
Team’s Recommended Mitigation: Encrypt Communications
Bitwarden’s Implemented Mitigation: Bitwarden uses end to end encryption and each sent file is encrypted using AES-256.  
1.	The web browser requests a Send access page from Bitwarden servers.
2.	Bitwarden servers return the Send access page as a Web Vault client.
3.	The Web Vault client locally parses the URL fragment containing the Send ID and encryption key.
4.	The Web Vault client requests data from the server based on the parsed Send ID. The encryption key is never included in network requests.
5.	Bitwarden servers return the encrypted Send to the Web Vault client.
6.	The Web Vault client locally decrypts the Send using the encryption key.
Exploit Weak Crypto: 
Team’s Recommended Mitigation: Implement Strong Encryption Algorithm
Bitwarden’s Implemented Mitigation: Bitwarden uses AES-256 encryption
Malicious Input:
Team’s Recommended Mitigation: Input Validation and Sanitation
Bitwarden’s Implemented Mitigation: The entirety of the send request is encrypted and stored on Bitwarden servers.  Bitwarden takes the responsibility of encrypting the sent text, however does very little in terms of validating the text as it become encrypted as soon as it is sent and does not get decrypted until it reaches the recipient.
Escape Input Validation:
Team’s Recommended Mitigation: Enforce Whitelists
Bitwarden’s Implemented Mitigation: This process goes along the same lines of the input validation and sanitation.  Bitwarden does not deal with the actual text sent in a send, it just deals with the encryption of said text.


### Diagram:
![](https://github.com/DoctorEww/software-assurance/blob/main/usecase/send_text/SendText_V2.drawio.jpg)
