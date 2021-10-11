# Assurance Case Report

## Team Nemo

### Claims, Arguments, and Detailed Alignment Assessments

* Claim 1 - [The system minimizes information disclosure during communication](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/InfoDisclosure/readme.md)
* Claim 2 - [The system provides reasonable protection from malicious input](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/MaliciousInput/readme.md)
* Claim 3 - [The system protects data integrity during transmission](https://github.com/DoctorEww/software-assurance/tree/main/AssuranceCase/DataIntegrity#readme)
* Claim 4 - [The system mitigates the impact of database theft](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/DatabaseTheft/readme.md)
* Claim 5 - [The system ensures proper user authentication](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/readme.md)

### Alignment Assesment Summary

* Assurance Claim 1 - Assesment
* Assurance Claim 2 - Assesment
* Assurance Claim 3 - Assesment
* Assurance Claim 4 - Assesment
* Assurance Cliam 5 - [The system ensures proper user authentication](https://github.com/DoctorEww/software-assurance/blob/main/AssuranceCase/UserAuth/readme.md)

  The system exhibits a number of characteristics that mitigate doubts concerning user authentication. A moderate password policy is enforced, however, more complexity would increase the strength of passwords significantly. The system uses salts, yet only *recommends* salts of over 16bytes. Randomness is achieved through the PRG included in the Node library. As indicated by Node documentation, the salt is only returned when sufficient entropy is achieved, however, details of the process are obscure. The two-factor authentication process meets security requirements with a high level of assurance. Password recovery is disallowed, circumventing recovery attacks and 2FA attacks. Login attempts aren't limited, but Captchas are used to a limited extent. Industry standard encryption SHA256 is utilized in hashing.


### Reflection

We started this assignment off, in contrast to the last one, by working on the assurance cases collaboratively. Discussions were very thorough and everyone was welcome to introduce their own ideas. Very early on with this assignment, one of the main challenges we also faced was making sure we understood what is and isn't valid. The team felt that that this was something that needed to be tackled first, so we met in a collaborative environment and designed our first assurance case regarding information disclosure. This ensured we could get a rough draft prepared and examined. When the draft of the first assurance case was complete and reviewed, the feedback we received was perfect in allowing us to build a foundational piece for the remaining diagrams of the assignment.

Working though the diagram portions of the assignment, we worked to create starting points individually before meeting with others to complete the rest of the diagram. This allowed us to work through the diagrams together while we tossed ideas amongst each other. Comparing diagrams on their first draft, the assurance case diagrams were much cleaner and comprehensive than the security requirements diagrams. One of the main challenges during the design of these diagrams was availability. While we wanted to work on the diagrams all together or in small groups, our varying schedules occasionally caused problems, much like previous assignments. However, the team has been extraordinary about preventing a challenge such as this from affecting the quality of our work. Where we could not meet as full groups, smaller groups were formed instead to complete the work that was distributed. Our assurance case diagrams were then further fine tuned when we could best accomodate everyone's schedule to ensure each diagram was reviewed and any errors were resolved.

Every member of the team continues to put in their best effort and looks forward to tackling the next assignment. All objectives were completed effectively and in good quality.
