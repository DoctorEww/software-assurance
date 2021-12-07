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
  * [Deepscan Site](https://deepscan.io/)
  * [Results](https://github.com/DoctorEww/software-assurance/tree/main/AutomatedScan/DeepScan)
* LGTM (Looks Good To Me)
  * [LGTM Site](https://lgtm.com/)
  * [Results](https://github.com/DoctorEww/software-assurance/tree/main/AutomatedScan/LGTM)
* Embold
  * [Embold](https://app.embold.io/)
  * [Results](https://github.com/DoctorEww/software-assurance/tree/main/AutomatedScan/Embold)
* SonarCloud
  * [SonarCloud](https://sonarcloud.io/)
  * [Results](https://github.com/DoctorEww/software-assurance/tree/main/AutomatedScan/SonarCloud)


### 3. Selected Common Weakness Enumerations

* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
  * **Files Analyzed:** 
    * [login.component.html](https://github.com/bitwarden/desktop/blob/b83058ecab843a443a048e1a57ab20650e0b4516/src/app/accounts/login.component.html)
    * [lock.component.html](https://github.com/bitwarden/desktop/blob/b83058ecab843a443a048e1a57ab20650e0b4516/src/app/accounts/lock.component.html)
    * [view.component.html](https://github.com/bitwarden/desktop/blob/c385efdbd2f38149132ab1251c4f02bb088ac200/src/app/vault/view.component.html)
    * [login.component.html](https://github.com/bitwarden/desktop/blob/master/src/app/accounts/login.component.html)

  * **Automated Scan Issues:** No relateive automated scan issues encountered.

  * **Code Review Summary:** The application minimizes the exposure of sensitive data to unauthorized users.
    * During [logging](https://github.com/DoctorEww/software-assurance/blob/main/Utility/log.jpg), very little sensitive data is logged.
    * When an incorrect authentication attempt is made, server scripts vendor.js and api.service.js respond as follows, ["Username or password is incorrect. Try again."](https://github.com/DoctorEww/software-assurance/blob/main/Utility/BadAuth.jpg) This response reveals no data about the error that occured in authentication.
    * The only potentially sensitive data revealed to unathorized users is the email address of the user that last logged in. This potentially reveals a slight amount risk to personal data, however doesn't pose a significant threat to the security of the application.
 
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html) 
  * **Files Analyzed:**
    * [cipher.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/cipher.service.ts)
    * [nodeCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/node/src/services/nodeCryptoFunction.service.ts)
    * [webCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/webCryptoFunction.service.ts)
  * **Automated Scan Issues:** No related automated scan issues encountered.
  * **Code Review Summary:**  We have concluded that BitWarden Desktop correctly uses a sufficiently complex password hashing algorithm. The application uses PBKDF2 SHA-256 to store passwords securely. PBKDF2 SHA-256 includes a local 100,001 rounds of password hashing with the email address as a salt and 100,000 rounds of password hashing on the server-side by default. The number of rounds the password is hashed is configurable. This process is detailed [here](https://bitwarden.com/help/article/what-encryption-is-used/). We are able to observe that the documentation is correctly followed within the code. We can see the login cryptography code [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/auth.service.ts#L124), [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/crypto.service.ts#L480), and [here](https://github.com/bitwarden/jslib/blob/cb00604617a3d38fb450d900dbdf63b636ae01f6/common/src/services/webCryptoFunction.service.ts#L26). This code is sparsely commented, but easy to follow. The cryptographic functions are eventually preformed in browser by [SubtleCrypto](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto) which has its own code review and cryptographic review process. 

* [CWE-326: Inadequate Encryption Strength (Code and Documentation)](https://cwe.mitre.org/data/definitions/326.html)
  * **Files Analyzed:** 
    * [cipher.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/cipher.service.ts)
    * [nodeCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/node/src/services/nodeCryptoFunction.service.ts)
    * [webCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/webCryptoFunction.service.ts)
  * **Automated Scan Issues:** No related automated scan issues encountered.
  * **Code Review Summary:**
    * The handshaking and enciphering that takes place within *cipher.service.ts* is strong and correctly verifies signatures. The only funtion that I'd like to see improved is the saveNeverDomain(). As it is currently it appears to handle a blacklist function for bad domains. I'd prefer to see a whitelist system in place but it is possible that it is simply a ironically named function. The code is well formatted and clearly named.
    * *nodeCryptoFunction.service.ts* handles the heavy lifting for all of the main crypto needs of the application. It's a well defined service list that uses well known algorithms that match best practices currently in use. It relies on the nodeJS crypto library which is in good standing and capability. Rounds of pbkdf2 are correctly configured and incorrectly generated keys will be errored out. The only potential weakness of the library is the RSA-OAEP function being reliant on SHA-1, but nodeJS does not support SHA-256 RSA-OAEP currently. While this is a shortcoming, in the grand scheme this is not a active issue since there are no current attacks on SHA-1 that are currently known to effect RSA-OAEP. There are benefits to moving to a stronger algorithm in case an attack is found in the future, but there is no active danger at this time. 
 
* [CWE-338: Use of Cryptographically Weak Pseudo-Random Number Generator (PRNG)](https://cwe.mitre.org/data/definitions/338.html)
  * **Files Analyzed:**
    * [cipher.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/cipher.service.ts)
    * [nodeCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/node/src/services/nodeCryptoFunction.service.ts)
    * [webCryptoFunction.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/webCryptoFunction.service.ts)
  * Automated Scan Issues: No related automated scan issues encountered.
  * Code Review Summary: Throughout our manual review process, we have concluded that BitWarden Desktop correctly uses a sufficiently random number generator. Bitwarden uses these random numbers to generate passwords users can execute on their site. To generate these random numbers, BitWarden Desktop calls low level browser functions that have been approved for cryptographic uses as shown [here](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/getRandomValues). We can see how the BitWarden code uses these random values [here](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/passwordGeneration.service.ts#L157), [here](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/crypto.service.ts#L666
), and [here](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/webCryptoFunction.service.ts#L300). After the generation of the random values, BitWarden correctly handles the random number by not reducing its entropy nor having bias in the generation technique. This code is sparsely commented, but easy to follow. 
 
* [CWE-347: Improper Verification of Cryptographic Signature](https://cwe.mitre.org/data/definitions/347.html)
  * **Files Analyzed:** 
    * [api.service.ts](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/api.service.ts)
    * [auth.service.ts](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/auth.service.ts)
    * [userVerification.service.ts](https://github.com/bitwarden/jslib/blob/5db94cc9d06ba478a29e9b625993108dfa0d7ec8/common/src/services/userVerification.service.ts)
  * **Automated Scan Issues:** No related automated scan issues encountered. 
  * **Code Review Summary:** 
    * The crypto services that reach outside the local host all properly retrieve signatures and encipher them using public key based algorithms. Signature caching is disabled forcing the application to retrive a new set each time. This could potentially open the application to a fringe case DNS poisoning attack, but the supporting requirements for this attack to take place would require a pre-compromised host (where a different attack would be much faster and more succesful) or a user willingly negligent enough to ignore doomsday-like warning messages to install a bad certificate. Overall the verification services are water-tight and strongly resist compromise.
 
* [CWE-532: Insertion of Sensitive Information into Log File](https://cwe.mitre.org/data/definitions/532.html)
  * **Files Analyzed:** 
    * [main.ts](https://github.com/bitwarden/desktop/blob/master/src/main.ts)
    * [log.service.ts](https://github.com/bitwarden/jslib/blob/master/electron/src/services/electronLog.service.ts)
    * [electronLog.service.ts](https://github.com/bitwarden/jslib/blob/master/electron/src/services/electronLog.service.ts)
  * Automated Scan Issues: No related automated scanning information.
  * Code Review Summary: Analyzing the log services of the application, there appears to be no indication or usage of the services to write anything beyond standard informational, error, warnings, and debugger messages if necessary. Sensitive user information containing usernames, names, password, or other PII is not stored/written to any of the log files that are accessible to the user.
 
* [CWE-613: Insufficient Session Expiration](https://cwe.mitre.org/data/definitions/613.html)
  * **Files Analyzed:** 
    * [vaultTimeout.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/vaultTimeout.service.ts)
    * [vault-timeout-input.component.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/angular/src/components/settings/vault-timeout-input.component.ts)
    
  * **Automated Scan Issues:** There were a few items on the vaultTimeout.service.ts file that were of HIGH importance which included avoid-return-await errors and avoid-floating-promises errors.  These errors did not affect the application's security, however it could cause unexpected behaviors such as resolving at unexpected times.  Other issues were avoid-return await issues in which it could potentially add extra time to resolving the code.  In the vault-timeout-input.compontents.ts file, there was only an issue of avoiding implicit dependencies.  These were not highly critical to the program's security.  
  
  * **Code Review Summary:** The automated scans did not result in revealing any critical issues with the security of the code.  There were just some minor coding issues that did not pose a severe threat to the security of the program or the data that it holds.  The vault-timeout.service.ts code checks to ensure that the session is valid every 10 seconds and the amount of time to wait is established in the policy of the program to 20 minutes.  The default timeout time is set to 0 minutes and then the time is then set to 60 minutes.  This ensures that the session can not stay on indefinitely.
 
* [CWE-732: Incorrect Permission Assignment for Critical Resource](https://cwe.mitre.org/data/definitions/732.html)
  * **Files Analyzed:** 
    * [biometric.windows.main.ts](https://github.com/bitwarden/jslib/blob/master/electron/src/biometric.windows.main.ts)
    * [tray.main.ts](https://github.com/bitwarden/jslib/blob/master/electron/src/tray.main.ts)
    * [utils.ts](https://github.com/bitwarden/jslib/blob/master/electron/src/utils.ts)
  * Automated Scan Issues: No related automated scanning information.
  * Code Review Summary: Bitwarden does not frequently make use of critical resources or assign permissions to clientside resouces. When it does seem to use external or system resources, the interaction is performed through the proper channels and well managed.
 
* [CWE-1286: Improper Validation of Syntactic Correctness of Input](https://cwe.mitre.org/data/definitions/1286.html)
  * **Files Analyzed:** 
    * [userVerification.service.ts](https://github.com/bitwarden/jslib/blob/78429aa7201989ad74a9ca36cc6832fcce0d4aee/common/src/services/userVerification.service.ts)
    
  * **Automated Scan Issues:** The automated scan found two issues of medium criticality.  The first was a prefer type cast issue that found as-cast instead of type-cast.  The second issue was a binary expression operand order issue.  This meant that the literal expression should be on the right-hand side of a binary expression.
  
  * **Code Review Summary:** The program does a good job of verifying and validating input when needed.  The majority of the time, the data that is inputed from the user does not go anywhere and thus does not pose a threat to the program.
 
* [CWE-1288: Improper Validation of Consistency within Input](https://cwe.mitre.org/data/definitions/1288.html)
  * **Files Analyzed:** 
    * [validation.service.ts](https://github.com/bitwarden/jslib/blob/1016bbfb9eb28c220de8d2ab86d1f2757328f254/angular/src/services/validation.service.ts)

  * **Automated Scan Issues:** No pertinent automated scan issues encountered.

  * **Code Review Summary:** BitWarden currently allows all types of input, yet executes none.
    * While ALL input is allow, both inconsistent and containing special characters, not user input is executed via server calls. The BitWarden Desktop Application simply stores a large number of strings and ensures that none of the strings stored are ever exectued.

### 4. Summary

Initial code review activities of the BitWarden Desktop Application centered around the analysis and understanding of the cumulative discoveries found during the previous portions of this project. Most notably, these potential weaknesses fell into two primary categories: (1) input and (2) cryptography. From these potential weaknesses a collection of 10 Common Weakness Enumerations were gathered and divided by teammate in order to manually traverse specific, identified weakness potentialities. Further, each automated code review carried out on the BitWarden Desktop Application would be focused into the same CWE’s. These 10 CWE’s are as follows:

* CWE-200: Exposure of Sensitive Information to an Unauthorized Actor
* CWE-261: Weak Encoding for Password
* CWE-326: Inadequate Encryption Strength (Code and Documentation
* CWE-338: Use of Cryptographically Weak Pseudo-Random Number Generator (PRNG)
* CWE-347: Improper Verification of Cryptographic Signature
* CWE-532: Insertion of Sensitive Information into Log File
* CWE-613: Insufficient Session Expiration
* CWE-732: Incorrect Permission Assignment for Critical Resource
* CWE-1286: Improper Validation of Syntactic Correctness of Input
* CWE-1288: Improper Validation of Consistency within Input

From the Code Review carried out:

1. All input is permitted by the application. This includes special characters, code, inconsistent input, and potentially harmful malformed inputs.
2. While all input is permitted, not user input is allowed to execute at any time in the code.
3. Strong cryptography is utilized for Password encoding and message encryption
4. The BitWarden Desktop Application implements a strong and sufficiently random Pseudo Random Number Generator.
5. Session tokens and expiration are effectively managed, however some minor coding issues did present a slight threat.

While the input issues appear to find mitigation in a lack of all user input execution, it is likely that rigid input validation and whitelisting would reduce the chances of weakness exploitations simply by decreasing the domain of allowable input characters and formats.

In terms of encryption, the BitWarden Desktop Application exhibits no concerning flaws. Each cryptographic protocol analyzed revealed a well designed, well planned, security minded code base. Passwords are hashed using PBKDF2 SHA-256 with 100,001 rounds of hashing and a suitable Pseudo Random Number Generator is used to generate randomness. The only minimal flaw discovered is the reliance of the RSA-OAEP function on SHA-1 hashing. While this indicates a slight issue, no current attacks on SHA-1 are known to effect RSA-OAEP implementations.

As a means to reduce the accidental breaching of personally identifiable information, the BitWarden Desktop Application reveals no sensitive information in either logging, on screen prompts, or in the communication of errors. When attempting to login, unauthorized credentials simply indicate that either the username or the password was incorrect. All other errors are handled internally and withheld from local logs. The data included in these logs generally includes timestamp information or data already accessible to the Operating System account.

### 5. OSS Contributions

Given the continuation of this open source security engineering project, the following open source project contributions and interactions are deemed likely to benefit the BitWarden Desktop Application codebase: (1) the communication of all findings discovered during the course of this project to pertinent open source managers, (2) addressing input validation concerns discovered in the execution of the engineering activities carried out by this team, (3) reaffirmation and validation of strong encryption processes utilized within and between the BitWarden Desktop Application and the BitWarden servers, and (4) the introduction of input sanitization and validation protections into the BitWarden Desktop Application user interface.

### 6. Reflection

Our approach to this portion of the assignment started off as with a lot of discussion and interactions between one another. Before meeting with professor Gandhi, we wanted to be sure we at least had some initial results that could be presented and discussed. We used a cloud-based automated review tool for our first scan set. Potential problems and vulnerabilities were discussed and distributed among the group. Communication was really fluid and each team member was encouraged to share scan results from their own automated scans. Manual code review questions and concerns were quickly addressed by fellow group members and resolved. Compared to other phases in the project, this phase was very organized compared to the first phase of the project when we all began.
