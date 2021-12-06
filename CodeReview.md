[back](https://github.com/DoctorEww/software-assurance)

# Code Review Report

## Team Nemo

### Code Review

### 1. Introduction

As one of the most essential elements in Software Security Engineering, a dilligent effort must be made to verify the security of the source code used in any given 
application. To accomplish this process, engineering efforts directed at code reivew must be formulated, outlined, and executed. Code review, in general, is best accomplished via the use of both manual and automated processes.

### 2. Code Review Strategy

The code review strategy for the BitWarden Desktop Application is proposed as follows: (1) a selection of [Common Weakness Enumerations](https://cwe.mitre.org/) (CWE) will be selected based on their relevance to discovered weaknesses and flaws within the design of the OSS project (2) these CWEs will be delegated among the team members for individual, manual code review, (3) automated code checking will be employed on the OSS repository, (4) the selected CWEs will inform areas of concern within the automated scan results, and (5) the team will investigate areas of concern related to both the selected CWEs and the automated scan results. 

### 3. Automated Scan Strategy

The automated scan strategy employed in this project is as follows: (1) each team member uses a distinct automated scan tool (if available), (2) automated scan results are posted to the [*automated scan*](https://github.com/DoctorEww/software-assurance/tree/main/AutomatedScan) directory, (3) during CWE code evaluation, each member checks all automated scan results for correlation to the CWE under review. Any issues found within an automated scan that correlate to a CWE below will be evaluted in section 3.

3.1. Automated Scan Tools

* Deepscan.io
  * [Deeptscan Site](https://deepscan.io/)
  * [Results]()
* LGTM (Looks Good To Me)
  * [LGTM Site](https://lgtm.com/)
  * [Results](https://github.com/DoctorEww/software-assurance/tree/main/AutomatedScan/LGTM)
* Embold - Chris
  * [Embold](https://app.embold.io/)
  * [Results]()
* Tool 4
  * [Tool 4 Site]()
  * [Results]()
* Tool 5
  * [Tool 5 Site]()
  * [Results]()

### 3. Selected Common Weakness Enumerations

* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html) - Adam 
  * **Files Analyzed:** [Main Login Directory](https://github.com/bitwarden/desktop/tree/master/src/app/accounts), [login.component.html](https://github.com/bitwarden/desktop/blob/b83058ecab843a443a048e1a57ab20650e0b4516/src/app/accounts/login.component.html), [lock.component.html](https://github.com/bitwarden/desktop/blob/b83058ecab843a443a048e1a57ab20650e0b4516/src/app/accounts/lock.component.html), [view.component.html](https://github.com/bitwarden/desktop/blob/c385efdbd2f38149132ab1251c4f02bb088ac200/src/app/vault/view.component.html), [login.component.html](https://github.com/bitwarden/desktop/blob/master/src/app/accounts/login.component.html)

  * **Automated Scan Issues:** No relateive automated scan issues encountered.

  * **Code Review Summary:** The application minimizes any exposure of sensitive data to unauthroized users.
    * During [logging](https://github.com/DoctorEww/software-assurance/blob/main/Utility/log.jpg), very little sensitive data is logged.
    * When an incorrect authentication attempt is made, server scripts vendor.js and api.service.js respond as follows, "Username or password is incorrect. Try again." - [Response Link](https://github.com/DoctorEww/software-assurance/blob/main/Utility/BadAuth.jpg) This response reveals no data about the error that occured in authentication.
    * The only data revealed to unathorized users is the password of the user that last logged in. This potentially reveals a slight amount of personal data.
 
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html) - Drew 
  * **Files Analyzed:** [auth.service.ts](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/auth.service.ts#L124), [crypto.service.ts](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/crypto.service.ts#L480), [webcryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/webCryptoFunction.service.ts#L26)
  * **Automated Scan Issues:** No related automated scan issues encountered.
  * **Code Review Summary:**  We have concluded that BitWarden Desktop correctly uses a sufficiently complex password hashing algorithm. The application uses PBKDF2 SHA-256 to store passwords securely. PBKDF2 SHA-256 includes a local 100,001 rounds of password hashing with the email address as a salt and 100,000 rounds of password hashing on the server-side by default. The number of rounds the password is hashed is configurable. This process is detailed [here](https://bitwarden.com/help/article/what-encryption-is-used/). We are able to observe that the documentation is correctly followed within the code. We can see the login cryptography code [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/auth.service.ts#L124), [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/crypto.service.ts#L480), and [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/webCryptoFunction.service.ts#L26). This code is sparsely commented, but easy to follow. The cryptographic functions are eventually preformed in browser by [SubtleCrypto](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto) which has its own code review and cryptographic review process. 

* [CWE-326: Inadequate Encryption Strength (Code and Documentation)](https://cwe.mitre.org/data/definitions/326.html) - Jensen 
  * Files Analyzed: [cipher.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/cipher.service.ts), [nodeCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/node/src/services/nodeCryptoFunction.service.ts), [webCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/webCryptoFunction.service.ts)
  * Automated Scan Issues: No related automated scan issues encountered.
  * **Code Review Summary:**
  * The handshaking and enciphering that takes place within *cipher.service.ts* is strong and correctly verifies signatures. The only funtion that I'd like to see improved is the saveNeverDomain(). As it is currently it appears to handle a blacklist function for bad domains. I'd prefer to see a whitelist system in place but it is possible that it is simply a ironically named function. 
  * *nodeCryptoFunction.service.ts* handles the heavy lifting for all of the main crypto needs of the application. It's a well defined service list that uses well known algorithms that matches best practices currently in use. It relies on the nodeJS crypto library which is in good standing and capability. Rounds of pbkdf2 are correctly configured and incorrectly generated keys will be errored out. The only potential weakness of the library is the RSA-OAEP function being reliant on SHA-1, but nodeJS does not support SHA-256 RSA-OAEP currently. While this is a shortcoming, in the grand scheme this is not a problem since there are no current attacks on SHA-1 that are currently know to effect RSA-OAEP. There are benefits to moving to a stronger algorithm in case an attack is found in the future, but there is no active danger at this time. 
 
* [CWE-338: Use of Cryptographically Weak Pseudo-Random Number Generator (PRNG)](https://cwe.mitre.org/data/definitions/338.html) - Drew 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io](url.to.scan) blah, blah, blah.
  * **Code Review Summary:** Throughout our manual review process, we have concluded that BitWarden Desktop correctly uses a sufficiently random number generator. Bitwarden uses these random numbers to generate passwords users can execute on their site. To generate these random numbers, BitWarden Desktop calls low level browser functions that have been approved for cryptographic uses as shown [here](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/getRandomValues). We can see how the BitWarden code uses these random values [here](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/passwordGeneration.service.ts#L157), [here](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/crypto.service.ts#L666
), and [here](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/webCryptoFunction.service.ts#L300). After the generation of the random values, BitWarden correctly handles the random number by not reducing its entropy nor having bias in the generation technique. This code is sparsely commented, but easy to follow. 
 
* [CWE-347: Improper Verification of Cryptographic Signature](https://cwe.mitre.org/data/definitions/347.html) - Jensen 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io](url.to.scan) blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-532: Insertion of Sensitive Information into Log File](https://cwe.mitre.org/data/definitions/532.html) - Justin 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io](url.to.scan) blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-613: Insufficient Session Expiration](https://cwe.mitre.org/data/definitions/613.html) - Chris 
  * **Files Analyzed:** [vaultTimeout.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/vaultTimeout.service.ts), [vault-timeout-input.component.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/angular/src/components/settings/vault-timeout-input.component.ts)
    
  * **Automated Scan Issues:** There were a few items on the vaultTimeout.service.ts file that were of HIGH importance which included avoid-return-await errors and avoid-floating-promises errors.  These errors did not affect the application's security, however it could cause unexpected behaviors such as resolving at unexpected times.  Other issues were avoid-return await issues in which it could potentially add extra time to resolving the code.  In the vault-timeout-input.compontents.ts file, there was only an issue of avoiding implicit dependencies.  These were not highly critical to the program's security.  
  
  * **Code Review Summary:** The automated scans did not result in revealing any critical issues with the security of the code.  There were just some minor coding issues that did not pose a severe threat to the security of the program or the data that it holds.  The vault-timeout.service.ts code checks to ensure that the session is valid every 10 seconds and the amount of time to wait is established in the policy of the program to 20 minutes.  The default timeout time is set to 0 minutes and then the time is then set to 60 minutes.  This ensures that the session can not stay on indefinitely.
 
* [CWE-732: Incorrect Permission Assignment for Critical Resource](https://cwe.mitre.org/data/definitions/732.html) - Justin 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io](url.to.scan) blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-1286: Improper Validation of Syntactic Correctness of Input](https://cwe.mitre.org/data/definitions/1286.html) - Chris 
  * **Files Analyzed:** [userVerification.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/userVerification.service.ts)
    
  * **Automated Scan Issues:** The automated scan found two issues of medium criticality.  The first was a prefer type cast issue that found as-cast instead of type-cast.  The second issue was a binary expression operand order issue.  This meant that the literal expression should be on the right-hand side of a binary expression.
  
  * **Code Review Summary:** The program does a good job of verifying and validating input when needed.  The majority of the time, the data that is inputed from the user does not go anywhere and thus does not pose a threat to the program.
 
* [CWE-1288: Improper Validation of Consistency within Input](https://cwe.mitre.org/data/definitions/1288.html) - Adam 
  * **Files Analyzed:** [validation.service.ts](https://github.com/bitwarden/jslib/blob/1016bbfb9eb28c220de8d2ab86d1f2757328f254/angular/src/services/validation.service.ts)

  * **Automated Scan Issues:** No pertinent automated scan issues encountered.

  * **Code Review Summary:** BitWarden currently allows all types of input, yet executes none. While ALL input is permissible in the context of the BitWarden Desktop Applications (this includes inconsistent input, special characters,a nd lines of code), all user input is sanitizd and kept from all forms of server or local client processing. The BitWarden Desktop Application simply stores a large number of strings and ensures that none of the strings stored are ever exectued.

### 4. Summary

### 5. OSS Contributions

### 6. Reflection

### 7. Project Collaboration Documentation

Find the Code Review Project [here](https://github.com/DoctorEww/software-assurance/projects/7)
