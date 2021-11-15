### Data Flow Diagram and Threat Modeling

1. [BitWarden DFD](https://github.com/DoctorEww/software-assurance/blob/main/Design/readme.md)
2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/DoctorEww/software-assurance/blob/main/Design/BitWarden_Report.html)

### Observations

**1. Introduction**

In effort to best mitigate the highest impact threats, all automaitcally generated threats evaluated in review with a High priority were divided among the team and assessed for existing mitigations in the current BitWarden implementation. During individual threat review: (1) the threat is identified, (2) a justification is established, (3) existing mitigations are documented, and (4) notable gaps in identified threats and existing mitigations are highlighted. 

**2. Individual Threat Review**
  - *Threat ID:  14*
    - Threat Name: 1.0 Bitwarden Desktop Application may be able to impersonate the context of BitWarden API in order to gain additional privilege. (CL)
    - Threat Justification: authentication is required in order to gain additional privilege
    - Existing Mitigations: Bitwarden implements HTTP Strict Transport Security and forces all connections to use TLS.
    - Notable Gap: None
    
  - *Threat ID: 1*
    - Threat Name:  Spoofing of Source Data Store File System
    - Threat Justification: All returning data is signed.
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 2*
    - Threat Name: Risks from Logging
    - Threat Justification: Log reader uses input sanitization and validation.
    - Existing Mitigations:
    - Notable Gap:
    
  - *Threat ID: 3*
    - Threat Name: Weak Access Control for a Resource
    - Threat Justification: BitWarden Desktop Application only has permissions to read it&#39;s own file space.
    - Existing Mitigations:
    - Notable Gap:
 
  - *Threat ID: 5*
    - Threat Name: Potential Data Repudiation by 1.0 Bitwarden Desktop Application
    - Threat Justification: In the event of non-readable files, new files are written.
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 6*
    - Threat Name: Potential Process Crash or Stop for 1.0 Bitwarden Desktop Application
    - Threat Justification: Coding best practices utilized.
    - Existing Mitigations:
    - Notable Gap:
  
  - *Threat ID: 7*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 8*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 9*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 10*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 11*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 14*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 17*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 18*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 19*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 20*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 21*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 22*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 23*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 25*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 26*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 28*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 29*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 30*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 31*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:

  - *Threat ID: 32*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  
  - *Threat ID: 21*
    - Threat Name: Risks from Logging (CL)
    - Threat Justification: logs do not contain sensitive information
    - Existing Mitigations: the logs only contain a minimal amount of information that includes mainly unique IDs, timestamps, and ipaddresses.
    - Notable Gap: None
    
  - *Threat ID: 11*
    - Threat Name: Spoofing of the BitWarden API External Destination Entity (CL)
    - Threat Justification: Use of digital certificates would en ensure proper authentication
    - Existing Mitigations: Bitwarden uses Microsoft Azure manager to ensure that security is maintained as well as implementing one-way salted hashing measures.
    - Notable Gap: None
    
  - *Threat ID: 15*
    - Threat Name: - DON'T WORK ON/Potential Cut
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 16*
    - Threat Name: Potential Process Crash or Stop for 1.0 Bitwarden Desktop Application
    - Threat Justification: No logs or dumps produced following an application crash.
    - Existing Mitigations: There are no handlers or means for sensitive data to be leaked or logged on crash.
    - Notable Gap: None.
  - *Threat ID: 17*
    - Threat Name: - DON'T WORK ON/Potential Cut
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 18*
    - Threat Name: - DON'T WORK ON/Potential Cut
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 19*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 20*
    - Threat Name: Spoofing of Destination Data Store File System (JR)
    - Threat Justification: Nothing sensitive is written to the file system. File system requires user level authentication on the system.
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 21*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 22*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 23*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 28*
    - Threat Name: The File System Data Store Could Be Corrupted (JR)
    - Threat Justification: No sensitive data stored; risk Accepted
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 29*
    - Threat Name: Data Store Denies File System Potentially Writing Data (JR)
    - Threat Justification: Operating System error event is created.
    - Existing Mitigations:
    - Notable Gap:
  - *Threat Id: 38*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 39*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  
**3. Design Observations Summary**

**4. Reflection**

Working through the initial phases of this portion of the project proved slightly difficult due to the tendency to over complicate the Data Flow Diagrams. Upon meeting with Dr. Gandhi, however, the team grasped the essence of what information our DFD(s) are supposed to convey. We quickly reoriented, reestablished a Level 0 DFD for the overall application, and realized that most data flow in the program flowed through the UI to the BitWarden Online API. A limited number of local memory interactions added a single data store and pushed us to a Level 1 diagram. The team decided that further granularity was not necessary.

Upon the completion of the diagram, we were able to address all automatically identified threats and chose to have each member choose at least three of the high level threats for investigation. Each member posted their chosen threats to our project board in order to avoid replication of work, and pertinent details were evaluated and documented during OSS review.

The team continues to function well together. At this point in the semester, the roles are becoming well defined, and the processes supporting the execution of each section of the project are now well established. Each team member is adding valuable insight to the project and carrying out required responsibilities quickly and efficiently.
