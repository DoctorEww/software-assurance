## Assurance Claim 2: The system provides reasonable protection from malicious input

[Back to Assurance Cases](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCases.md)

### Description:

User input is regularly taken into this application. This user input has the potential to cause damage if not handled properly. Due to the critical nature of this security requirement, assurance is needed to mitigate doubts about input functionality in the application. 

### Alignment Assessment:

BitWarden currently provides the following evidences per the Assurance Case needs E1-E4 in the diagram below:

* E1: *Source Code Review: Not Executing User Input* - This application does not use the most common TypeScript insecure functions as described [here](https://snyk.io/blog/5-ways-to-prevent-code-injection-in-javascript-and-node-js/).

* E2: *Automated Code Check Report* - The software fails to include static code analysis as part of its build process. Instead, it has opted to use regular code audits shown [here](https://bitwarden.com/help/article/is-bitwarden-audited/). This may work, but it introduces gaps when new code is added. We recommended a static analysis tool be added to the build process.

* E3: *Review Code Certificate* - The code possess a valid certificate by DigiCert until late 2022 when it will need to renew its certificate. This was verified by using the Windows Certificate Manager while installing the application. 

* E4: *Unapproved Character testing report*  - This application does not prohibit any characters during login, rather it interprets all inputted characters as safe characters and relies on the non-execution of the code to stop this code from being executed [here](https://github.com/bitwarden/jslib/blob/2c892eb3a2a9aff1e238146b037e6f3eb5dacf9a/angular/src/components/login.component.ts).

### Diagram
![](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/MaliciousInput/MaliciousInputV2.jpg)
