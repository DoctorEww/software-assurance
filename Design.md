### Data Flow Diagram and Threat Modeling

1. [BitWarden DFD](https://github.com/DoctorEww/software-assurance/blob/main/Design/readme.md)
2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/DoctorEww/software-assurance/blob/main/Design/BitWarden_Report.html)

### Observations

**1. Introduction**

In effort to best mitigate the highest impact threats, all automaitcally generated threats evaluated in review with a High priority were divided among the team and assessed for existing mitigations in the current BitWarden implementation. During individual threat review: (1) the threat is identified, (2) a justification is established, (3) existing mitigations are documented, and (4) notable gaps in identified threats and existing mitigations are highlighted. 

**2. Individual Threat Review**
  - *Threat ID:  2*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
    
  - *Threat ID: 12*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 14*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 15*
    - Threat Name:
    - Threat Justification:
    - Existing Mitigations:
    - Notable Gap:
  - *Threat ID: 16*
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
