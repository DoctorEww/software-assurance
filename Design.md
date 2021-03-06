### i. Contents

1. [Data Flow Diagram and Threat Modeling](#1-Data-Flow-Diagram-and-Threat-Modeling)
2. [Introduction](#2-Introduction)
3. [Individual Threat Review](#3-Individual-Threat-Review)
4. [Design Observations Summary](#4-Design-Observations-Summary)
5. [Reflection](#5-Reflection)
6. [Project Collaboration](#6-Collaboration)

### 1. Data Flow Diagram and Threat Modeling

1. [BitWarden DFD](https://github.com/DoctorEww/software-assurance/blob/main/Design/readme.md)
2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/DoctorEww/software-assurance/blob/main/Design/BitWarden_Report.html)

### 2. Introduction

In effort to best mitigate the highest impact threats, all automatically generated threats evaluated in review with a high priority were divided among the team and assessed for existing mitigations in the current BitWarden implementation. During individual threat review: (1) the threat is identified, (2) a justification for the mitigation of the threat is established, (3) existing, *implemented* mitigations are documented, and (4) notable gaps in identified threats and existing mitigations are highlighted. 

### 3. Individual Threat Review
    
  - *Threat ID: 1*
    - Threat Name:  Spoofing of Source Data Store File System
    - Justification: All returning data is signed and authenticated.
    - Existing Mitigations: All synchronizations to and from the BitWarden server are *carefully* and *consistently* [authenticated](https://github.com/bitwarden/jslib/blob/8f177e2d3a879b854db5c6e6d7d386b24d637a66/common/src/services/sync.service.ts#L288) and the codebase is [signed](https://github.com/DoctorEww/software-assurance/blob/main/Utility/Signed.jpg).
    - Notable Gap: None

  - *Threat ID: 2*
    - Threat Name: Risks from Logging
    - Justification: Log reader uses input sanitization and validation.
    - Existing Mitigations: BitWarden currently trusts all file system operations.
    - Notable Gap: **BitWarden does not check incoming data from the file system for potential malicious input.**
    
  - *Threat ID: 3*
    - Threat Name: Weak Access Control for a Resource
    - Justification: BitWarden Desktop Application only has permissions to read its own file space.
    - Existing Mitigations: BitWarden runs as a user process which has permissions to read and write all user files.
    - Notable Gap: **BitWarden has elevated permissions to read and write files; these permissions are unnecessary.**
 
  - *Threat ID: 5*
    - Threat Name: Potential Data Repudiation by 1.0 Bitwarden Desktop Application
    - Justification: In the event of non-readable files, new files are written.
    - Existing Mitigations: BitWarden replaces non-existing files. Files that have been [tampered with](https://github.com/DoctorEww/software-assurance/blob/main/Utility/corrupted_file.PNG) cause a crash.
    - Notable Gap: **BitWarden crashes when local files are tampered with.**

  - *Threat ID: 6*
    - Threat Name: Potential Process Crash or Stop for 1.0 Bitwarden Desktop Application
    - Justification: Coding best practices utilized.
    - Existing Mitigations: BitWarden [crashes](https://github.com/DoctorEww/software-assurance/blob/main/Utility/corrupted_file.PNG) throwing an error message.
    - Notable Gap: **BitWarden does not crash gracefully**
  
  - *Threat ID: 7*
    - Threat Name: Data Flow Application Data Is Potentially Interrupted
    - Justification: Application functions without the explicit need for the file system
    - Existing Mitigations: Application recreates files that are missing
    - Notable Gap: **BitWarden *requires* the file system to function correctly.**

  - *Threat ID: 8*
    - Threat Name: Data Store Inaccessible
    - Justification: Application functions without the explicit need for the file system
    - Existing Mitigations: Application recreates files that are missing
    - Notable Gap: **BitWarden *requires* the file system to function correctly.**
 
  - *Threat ID: 9*
    - Threat Name: 1.0 Bitwarden Desktop Application May be Subject to Elevation of Privilege Using Remote Code Execution
    - Justification: Input validation and sanitization is used to disallow local code execution.
    - Existing Mitigations: BitWarden currently trusts all file system operations.
    - Notable Gap: **BitWarden does not check incoming data from the file system for potential malicious input.**

  - *Threat ID: 10*
    - Threat Name: Elevation by Changing the Execution Flow in 1.0 Bitwarden Desktop Application
    - Justification: Input validation and sanitization is used to ensure data is sanitized before entering the program flow.
    - Existing Mitigations: BitWarden currently trusts all file system operations.
    - Notable Gap: **BitWarden does not check incoming data from the file system for potential malicious input.**

  - *Threat ID: 11*
    - Threat Name: Spoofing of the BitWarden API External Destination Entity
    - Justification: Use of digital certificates ensures proper authentication
    - Existing Mitigations: Bitwarden uses Microsoft Azure manager to ensure that security is maintained as well as implementing one-way salted hashing measures.
    - Notable Gap: None

  - *Threat ID: 14*
    - Threat Name: 1.0 Bitwarden Desktop Application may be able to impersonate the context of BitWarden API in order to gain additional privilege
    - Justification: Authentication is required in order to gain additional privilege
    - Existing Mitigations: Bitwarden implements HTTP Strict Transport Security and forces all connections to use TLS.
    - Notable Gap: None

  - *Threat ID: 16*
    - Threat Name: Potential Process Crash or Stop for 1.0 Bitwarden Desktop Application
    - Threat Justification: No logs or dumps produced following an application crash.
    - Existing Mitigations: There are no handlers or means for sensitive data to be leaked or logged on crash.
    - Notable Gap: None

  - *Threat ID: 17*
    - Threat Name: Data Flow Encrypted Response Is Potentially Interrupted
    - Justification: Re-request data
    - Existing Mitigations: BitWarden implements the JSLib function [async/await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) combination to ensure the request is fulfilled with acceptable promises. Should responses be delayed, the await function will suspend execution until the returned promise is fulfilled or rejected.
    - Notable Gap: None

  - *Threat ID: 18*
    - Threat Name: 1.0 Bitwarden Desktop Application May be Subject to Elevation of Privilege Using Remote Code Execution
    - Justification: Input sanitization and validation is used to sanitize all input coming from remote sources.
    - Existing Mitigations: While synchronizations to and from the BitWarden server are *carefully* and *consistently* [authenticated](https://github.com/bitwarden/jslib/blob/8f177e2d3a879b854db5c6e6d7d386b24d637a66/common/src/services/sync.service.ts#L288), the codebase is [signed](https://github.com/DoctorEww/software-assurance/blob/main/Utility/Signed.jpg) to ensure tampering is minimized, and Azure [upload sanitization](https://github.com/bitwarden/jslib/blob/8f177e2d3a879b854db5c6e6d7d386b24d637a66/common/src/services/azureFileUpload.service.ts) is used to put information on the server, it appears the BitWarden assumes data *returning* from the server is trustworthy. The only exhibition of server data validation occurs when a [vault timeout](https://github.com/bitwarden/jslib/blob/32774561f37bdcf9abb80276c5d1958b7ec192de/angular/src/components/settings/vault-timeout-input.component.ts) occurs.
    - Notable Gap: **All data going to the server is trustworthy and the codebase is signed, but direct downloads aren't sanitized.**

  - *Threat ID: 19*
    - Threat Name: Elevation by Changing the Execution Flow in 1.0 Bitwarden Desktop Application
    - Justification: Input validation and sanitization is used to ensure all code entering the application is scrubbed.
    - Existing Mitigations: BitWarden uses a [validation Service](https://github.com/bitwarden/jslib/blob/1016bbfb9eb28c220de8d2ab86d1f2757328f254/angular/src/services/validation.service.ts) via JSLib to validate input.
    - Notable Gap: **While user input is scrubbed, the validation process is not explicit, thus, due to a lack of clarity, flaws could exist.**

  - *Threat ID: 20*
    - Threat Name: Spoofing of Destination Data Store File System
    - Justification: Nothing sensitive is written to the file system. File system requires user level authentication on the system.
    - Existing Mitigations: The logs written contain only a minimal amount of [information](https://github.com/DoctorEww/software-assurance/blob/main/Utility/log.jpg). It's composed of mostly unique IDs, timestamps, and IPs. The file system requires the system defined user trust level.
    - Notable Gap: None.

  - *Threat ID: 21*
    - Threat Name: Risks from Logging
    - Justification: Logs do not contain sensitive information
    - Existing Mitigations: The logs only contain a minimal amount of [information](https://github.com/DoctorEww/software-assurance/blob/main/Utility/log.jpg) that includes mainly unique IDs, timestamps, and IP addresses.
    - Notable Gap: None

  - *Threat ID: 22*
    - Threat Name: Lower Trusted Subject Updates Logs 
    - Justification: Logging adheres to system defined user trust levels.
    - Existing Mitigations: Logging service runs at a user level and are stored under the user's profile protected by file permissions.
    - Notable Gap: None.

  - *Threat ID: 23*
    - Threat Name: Data Logs from an Unknown Source
    - Justification: Logging adheres to system defined user trust levels.
    - Existing Mitigations: Logged data fields are limited to system and application ID's. Outside input beyond IP addresses are not stored in logs. 
    - Notable Gap: None.

  - *Threat ID: 25*
    - Threat Name: Potential Weak Protections for Audit Data
    - Justification: No sensitive information stored in the local logs.
    - Existing Mitigations: Logs are not application readable. In order to read logs, the user must locate them and access them with a utility. Bitwarden does not extend any protections to the logs beyond the given system R/W protections.
    - Notable Gap: **No log protections beyond limited Read/Write control.** 

  - *Threat ID: 26*
    - Threat Name: Authorization Bypass
    - Justification: Logging adheres to system defined user trust levels.
    - Existing Mitigations: Files are stored under a system defined user's profile.
    - Notable Gap: None.

  - *Threat ID: 28*
    - Threat Name: The File System Data Store Could Be Corrupted
    - Justification: No sensitive data stored; risk accepted
    - Existing Mitigations: The application [crashes](https://github.com/DoctorEww/software-assurance/blob/main/Utility/corrupted_file.PNG) if the files are corrupted.
    - Notable Gap: **BitWarden crashes when files are corrupted**

  - *Threat ID: 29*
    - Threat Name: Data Store Denies File System Potentially Writing Data
    - Justification: Operating System error event is created
    - Existing Mitigations: BitWarden [crashes](https://github.com/DoctorEww/software-assurance/blob/main/Utility/corrupted_file.PNG) and does not actually handle any errors itself.
    - Notable Gap: **BitWarden needs the file system to function correctly.**

  - *Threat ID: 30*
    - Threat Name: Data Flow Sniffing
    - Justification: No sensitive data is stored locally.
    - Existing Mitigations: All traffic to and from Bitwarden Desktop across a sniff-able vector is encrypted with an industry standard symmetric suite. Key exchanges are also handled utilizing current best practices.
    - Notable Gap: None.

  - *Threat ID: 31*
    - Threat Name: Data Flow User Data Is Potentially Interrupted
    - Justification: An operating System error event is created. Application can function without the file system.
    - Existing Mitigations: Application recreates files that are missing
    - Notable Gap: **BitWarden needs the file system to function correctly.**

  - *Threat ID: 32*
    - Threat Name: Data Store Inaccessible
    - Justification: Application can function without the explicit use of the file system
    - Existing Mitigations: Application recreates files that are missing
    - Notable Gap: **BitWarden needs the file system to function correctly.**

  - *Threat ID: 34*
    - Threat Name: Spoofing the 1.0 Bitwarden Desktop Application Process
    - Justification: The local codebase is signed
    - Existing Mitigations: BitWarden currently [signs](https://github.com/DoctorEww/software-assurance/blob/main/Utility/Signed.jpg) all distributions.
    - Notable Gap: None

  - *Threat ID: 35*
    - Threat Name: Potential Lack of Input Validation for 1.0 Bitwarden Desktop Application
    - Justification: The application enforces user input validation and sanitization.
    - Existing Mitigations: BitWarden uses a [validation Service](https://github.com/bitwarden/jslib/blob/1016bbfb9eb28c220de8d2ab86d1f2757328f254/angular/src/services/validation.service.ts) via JSLib to validate input. User input is never executed.
    - Notable Gap: **While user input is scrubbed, the validation process is not *explicit*. Due to a simple lack of clarity, flaws could exist.**

  - *Threat ID: 38*
    - Threat Name: Potential Process Crash or Stop for 1.0 Bitwarden Desktop Application
    - Justification: Coding best practices utilized
    - Existing Mitigations: BitWarden crashes throwing an [error message](https://github.com/DoctorEww/software-assurance/blob/main/Utility/invalid_permissions.PNG).
    - Notable Gap: **BitWarden does not gracefully handle crashes**
    
  - *Threat ID: 40*
    - Threat Name: 1.0 Bitwarden Desktop Application May be Subject to Elevation of Privilege Using Remote Code Execution
    - Justification: Input validation and sanitization is implemented to ensure clean input.
    - Existing Mitigations: BitWarden uses a [validation Service](https://github.com/bitwarden/jslib/blob/1016bbfb9eb28c220de8d2ab86d1f2757328f254/angular/src/services/validation.service.ts) via JSLib to validate input. User input is never executed.
    - Notable Gap: **While user input is scrubbed, the validation process is not *explicit*. Due to a simple lack of clarity, flaws could exist.**

  - *Threat ID: 41*
    - Threat Name: Elevation by Changing the Execution Flow in 1.0 Bitwarden Desktop Application
    - Justification: Input validation and sanitization is used to sterilize all incoming data.
    - Existing Mitigations: BitWarden uses a [validation Service](https://github.com/bitwarden/jslib/blob/1016bbfb9eb28c220de8d2ab86d1f2757328f254/angular/src/services/validation.service.ts) via JSLib to validate input. User input is never executed.
    - Notable Gap: **While user input is scrubbed, the validation process is not *explicit*. Due to a simple lack of clarity, flaws could exist.**
  
### 4. Design Observations Summary

By outlining the overall data flow of the 1.0 BitWarden Desktop Application and identifying potential trust boundaries, automatic threat generation revealed a number of potential security threats. In general, the 1.0 BitWarden Desktop Application facilitates the transfer of data between two (2) External Interactors (EI) and one (1) Data Store (DS). Information is relayed to and from the application by the following EIs: (1) the user, and (2) the online BitWarden API. A single, local DS is located on the file system of the local computer.

With these entities in mind, trust boundaries were established between the User and the 1.0 BitWarden Desktop Application, the 1.0 BitWarden Desktop Application and the external BitWarden API, and the 1.0 BitWarden Desktop Application and the local File System. From these trust boundaries, the Microsoft Threat Modeling tool recognized a large number of automatically generated threats. From these threats, 30 were evaluated by the team as *High Priority*.

From these 30 established, high priority threats, mitigations were formulated and justified. From these justifications, the actual 1.0 BitWarden Desktop Application was canvassed for comparative flaws. While the existing 1.0 BitWarden Desktop Application generally ensures authentication and encryption security, there are a number of gaps that became evident throughout the analysis. 

### 4.1 Notable Gaps:
1. BitWarden Desktop Application (BDA) exhibits a strict requirement that the file system be accessible. 
    - Should the file system be unavailable, BDA fails to function.
2. In conjunction with the gap above, BDA relies on the file system *without* performing any file system input validation or sanitization.
    - With such an explicitly required Data Store, an overt lack of input validation or sanitization from the Data Store increases the likelihood of application crashes and errors.
3. This lack of input validation and sanitization results in a large number of BDA crashes.
4. These crashes are inadequately handled by BDA, causing system errors and operating system crash events.
5. BDA allows log and configuration data to be tampered with, while exhibiting no input validation and sanitization from this data.
6. When accessing the BitWarden Server, direct downloads from the server aren???t sanitized.
    - All uploads to the server are carefully authenticated and sanitized, creating an assumption that all downloads are safe.
7. BDA appears to provide user input and sanitization, yet the process is unclear. 


### 5. Reflection

Working through the initial phases of this portion of the project proved slightly difficult due to the tendency to over complicate the Data Flow Diagrams. Upon meeting with Dr. Gandhi, however, the team grasped the essence of what information our DFD(s) are supposed to convey. We quickly reoriented, reestablished a Level 0 DFD for the overall application, and realized that most data flow in the program flowed through the UI to the BitWarden Online API. A limited number of local memory interactions added a single data store and pushed us to a Level 1 diagram. The team decided that further granularity was not necessary.

Upon the completion of the diagram, we were able to address all automatically identified threats and chose to have each member choose at least three of the high-level threats for investigation. Each member posted their chosen threats to our project board to avoid replication of work, and pertinent details were evaluated and documented during OSS review.

The team continues to function well together. At this point in the semester, the roles are becoming well defined, and the processes supporting the execution of each section of the project are now well established. Each team member is adding valuable insight to the project and carrying out required responsibilities quickly and efficiently.

### 6. Collaboration

[Project Collaboration Link](https://github.com/DoctorEww/software-assurance/projects/6)
