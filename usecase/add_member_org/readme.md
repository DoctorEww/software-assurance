## Use Case: Add a Member to Group

### Description:
BitWarden allows the creation and modification of user level groups for the sharing of accounts, logins, messages, and other secure features. To expand a group, privileged users must add other BitWarden members. To ensure the security of the BitWarden group accounts, the security requirements for the group functionality must be considered.

### Alignment Analysis:

After developing and analyzing the use/misuse case diagram, a few key weaknesses were derived that could damage secure operations. They are the following:

#### *Providing Malicious Input*
With a number of various input fields, there is the potential risk for malicious input to be provided. The team recommends input validation and this can be seen as already implemented by Bitwarden. Because adding a member takes place through both the web and desktop portals, it is critical that both are seamlessly secured. Malicious input through the desktop application is only handled and displayed as text. Transitioning to the web version, attempting to submit malicious input to interact with the desktop app from there seems to result in the user being forcibly logged out of the application.

#### *Escaping Input Validation*

#### *Eavesdropping on the Network*

#### *Exploiting Weak Crypto*

### Summary of Findings:
In its current state, the Bitwarden Desktop application does a really great job of already securing a number of features and capabilities. 

### Diagram:
![](https://github.com/DoctorEww/software-assurance/blob/main/usecase/add_member_org/AddMemberV3.jpg)

