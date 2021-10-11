# Assurance Case Report

## Team Nemo

### Claims, Arguments, and Detailed Alignment Assessments

* Claim 1 - [The system minimizes information disclosure during communication](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/InfoDisclosure/readme.md)
* Claim 2 - [The system provides reasonable protection from malicious input](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/MaliciousInput/readme.md)
* Claim 3 - [The system protects data integrity during transmission](https://github.com/DoctorEww/software-assurance/tree/main/AssuranceCase/DataIntegrity#readme)
* Claim 4 - [The system mitigates the impact of database theft](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/DatabaseTheft/readme.md)
* Claim 5 - [The system ensures proper user authentication](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/readme.md)

### Alignment Assesment Summary

* **Assurance Claim 1** - [The system minimizes information disclosure during communication](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/InfoDisclosure/readme.md)
   
  *Overview*: BitWarden takes a number of steps to minimize the disclosure of information during communication. AES encryption is utilized for all in transit communications. Salts are generated via the use of Node's PRG. Though the Node documentation indicates that a sufficient level of entropy is required to return a given salt, the process remains abstract as more documentation is unavailable. Salt is utilized, however, a sufficient length is not required, only highly *recommended*. This creates a slight *gap* in assurance vs. implementation. Finally, BitWarden implements the PKDBF2 SHA256 algorithm for sufficient key stretching strength. 
  
  *Conclusion*: Per assurance claim 1, the BitWarden Desktop Application exhibits high alignment with the assurance cases with the assurance cases developed during this study.

* **Assurance Claim 2** - [The system provides reasonable protection from malicious input](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/MaliciousInput/readme.md)

  *Overview*: Any user input within the confines of a system represents a potential threat. The BitWarden Desktop Application takes a number of steps to ensure protection from malicious user input. The application does not use common TypeScript *insecure* functions, but rather uses only functions that are known to be secure. Static code analysis and automated code checking are currently not implemented in the BitWarden Desktop Application. Instead, the development team has opted for regular code audits. Though the code audits can mitigate malicious insider code threats, the lack of an automated code verification system creates a significant gap between implementation and assurance requirements. A valid code certificate exists for the code until 2022. Finally, special characters are not disallowed within the scope of the login system. Instead, the code interprets all inputted text as safe, and relies on the non-execution of code. 
  
  *Conclusion*: Per assurance claim 2, the BitWarden Desktop Application maintains a moderate level of alignment with the assurance cases developed during this study.

* **Assurance Claim 3** - [The system protects data integrity during transmission](https://github.com/DoctorEww/software-assurance/tree/main/AssuranceCase/DataIntegrity#readme)

  *Overview*: The BitWarden Desktop application utilizes a number of information transfer protocols to communicate data between users. To ensure data integrity during transmission, the system takes a number of steps to assure security. All messages are encrypted using the AES 256 algorithm, effectively mitigating encryption attacks. Salt is generated using the Node PRG, yet details of the process remain relatively unknown as sufficient functional descriptions are unavailable. The use of salt is enforced, however, a sufficient length is simply *recommended* and isn't enforced. The PKDBF2 SHA256 key stretching algorithm is used in the application for sufficient and security key expansion. Finally, passwords are hidden by default so as to aid in the protection of sensitive data.
  
  *Conclusion*: Per assurance claim 3, the BitWarden Desktop Application maintains a high level of alignment with the assurance cases developed during this study.

* **Assurance Claim 4** - [The system mitigates the impact of database theft](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/DatabaseTheft/readme.md)

  *Overview*: The password database creates the kernel around which the BitWarden Desktop Application is wrapped. Due to the critical nature of the password database, assurances must be created so as to reduce the doubts about the security of the database. The system takes a number of steps to mitigate the impact of database theft. All communications to and from the database is encrypted via AES 256. Salt is generated via the Node PRG (See above concerns). The PKDBF2 SHA 256 key stretching algorithm ensures secure key expansion. 
  
  *Conclusion*: Per assurance claim 4, the BitWarden Desktop Application maintains a high level of alignment with the assurance cases developed during this study.

* **Assurance Cliam 5** - [The system ensures proper user authentication](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/readme.md)

  *Overview*: The system exhibits a number of characteristics that mitigate doubts concerning user authentication. A moderate password policy is enforced, however, more complexity would increase the strength of passwords significantly. The system uses salts, yet only *recommends* salts of over 16 bytes. Randomness is achieved through the PRG included in the Node library. As indicated by Node documentation, the salt is only returned when sufficient entropy is achieved, however, details of the process are obscure. The two-factor authentication process meets security requirements with a high level of assurance. Password recovery is disallowed, circumventing recovery attacks and 2FA attacks. Login attempts aren't limited, but Captchas are used to a limited extent. Industry standard encryption SHA256 is utilized in hashing.
  
  *Conclusion*: Per assurance claim 5, the BitWarden Desktop Application maintains a moderate level of alignment with the assurance cases developed during this study.

### Reflection

We started this assignment off, in contrast to the last one, by working on the assurance cases collaboratively. Discussions were very thorough and everyone was welcome to introduce their own ideas. Very early on with this assignment, one of the main challenges we also faced was making sure we understood what is and isn't valid. The team felt that that this was something that needed to be tackled first, so we met in a collaborative environment and designed our first assurance case regarding information disclosure. This ensured we could get a rough draft prepared and examined. When the draft of the first assurance case was complete and reviewed, the feedback we received was perfect in allowing us to build a foundational piece for the remaining diagrams of the assignment.

Working though the diagram portions of the assignment, we worked to create starting points individually before meeting with others to complete the rest of the diagram. This allowed us to work through the diagrams together while we tossed ideas amongst each other. Comparing diagrams on their first draft, the assurance case diagrams were much cleaner and comprehensive than the security requirements diagrams. One of the main challenges during the design of these diagrams was availability. While we wanted to work on the diagrams all together or in small groups, our varying schedules occasionally caused problems, much like previous assignments. However, the team has been extraordinary about preventing a challenge such as this from affecting the quality of our work. Where we could not meet as full groups, smaller groups were formed instead to complete the work that was distributed. Our assurance case diagrams were then further fine tuned when we could best accomodate everyone's schedule to ensure each diagram was reviewed and any errors were resolved.

Every member of the team continues to put in their best effort and looks forward to tackling the next assignment. All objectives were completed effectively and in good quality.
