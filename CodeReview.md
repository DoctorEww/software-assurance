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

The automated scan strategy employed in this project is as follows: (1) each team member uses a distinct automated scan tool, (2) automated scan results are posted to the [*automated scan*](https://github.com/DoctorEww/software-assurance/tree/main/AutomatedScan) directory, (3) during CWE code evaluation, each member checks all automated scan results for correlation to the CWE under review. Any issues found within an automated scan that correlate to a CWE below will be evaluted in section 3.

3.1. Automated Scan Tools

* [Deepscan.io](https://deepscan.io/)
* Tool 2
* Tool 3
* Tool 4
* Tool 5

### 3. Selected Common Weakness Enumerations

* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html) - Adam 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html) - Drew 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 

* [CWE-326: Inadequate Encryption Strength (Code and Documentation)](https://cwe.mitre.org/data/definitions/326.html) - Jensen 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-338: Use of Cryptographically Weak Pseudo-Random Number Generator (PRNG)](https://cwe.mitre.org/data/definitions/338.html) - Drew 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-347: Improper Verification of Cryptographic Signature](https://cwe.mitre.org/data/definitions/347.html) - Jensen 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-532: Insertion of Sensitive Information into Log File](https://cwe.mitre.org/data/definitions/532.html) - Justin 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-613: Insufficient Session Expiration](https://cwe.mitre.org/data/definitions/613.html) - Chris 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-732: Incorrect Permission Assignment for Critical Resource](https://cwe.mitre.org/data/definitions/732.html) - Justin 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-1286: Improper Validation of Syntactic Correctness of Input](https://cwe.mitre.org/data/definitions/1286.html) - Chris 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 
 
* [CWE-1288: Improper Validation of Consistency within Input](https://cwe.mitre.org/data/definitions/1288.html) - Adam 
  * Files Analyzed: [FileName1](http://url.to.file), [FileName2](http://url.to.file)
  * Automated Scan Issues: Be sure to link to the automated scan in question. i.e. Per [Deepscan.io][url.to.scan] blah, blah, blah.
  * Code Review Summary: 

### 4. Summary

### 5. OSS Contributions

### 6. Reflection
