[back](https://github.com/DoctorEww/software-assurance)

# Code Review Report

## Team Nemo

### Code Review

### 1. Introduction

As one of the most essential elements in Software Security Engineering, a dilligent effort must be made to verify the security of the source code used in any given 
application. To accomplish this process, engineering efforts directed at code reivew must be formulated, outlined, and executed. Code review, in general, is best accomplished via the use of both manual and automated processes.

### 2. Code Review Strategy

The code review strategy for the BitWarden Desktop Application is proposed as follows: (1) a selection of [Common Weakness Enumerations](https://cwe.mitre.org/) (CWE) will be selected based on their relevance to discovered weaknesses and flaws within the design of the OSS project (2) these CWEs will be delegated among the team members for individual, manual code review, (3) automated code checking will be employed on the OSS repository, (4) the selected CWEs will inform areas of concern within the automated scan results, and (5) the team will investigate areas of concern related to both the selected CWEs and the automated scan results. 

### 3. Selected Common Weakness Enumerations

* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor]() - Adam
* [CWE-261: Weak Encoding for Password]() - Drew
* [CWE-326: Inadequate Encryption Strength (Code and Documentation)]() - Jensen
* [CWE-338: Use of Cryptographically Weak Pseudo-Random Number Generator (PRNG)]() - Drew
* [CWE-347: Improper Verification of Cryptographic Signature]() - Jensen
* [CWE-532: Insertion of Sensitive Information into Log File]() - Justin
* [CWE-613: Insufficient Session Expiration]() - Chris
* [CWE-732: Incorrect Permission Assignment for Critical Resource]() - Justin
* [CWE-1286: Improper Validation of Syntactic Correctness of Input]() - Chris
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor]() - Adam

### 4. Code Review Outcomes

### 5. Summary

### 6. OSS Contributions

### 7. Reflection
