# CYBR 8420 - Project Proposal
## Team Nemo

# Open-Source Project: BitWarden Desktop Application

## Hypothetical Operation Environment

With the flexibility available by the applications Bitwarden provides and the comprehensive business accounts, one could see Bitwarden applied in a business setting. Hypothetically examining this situation, it is important to understand that Bitwarden touches upon multiple different operational environments. It can operate through user interaction on their own devices and across the network of a business. The expectations of the software, among any environment, would ensure that the passwords and stored information of users or employees is securely contained. The data would be well protected in all three states; it would be protected while at rest, in motion, and in use without any potential exposure to a malicious or unintended recipient. From a business standpoint, it would also be expected that Bitwarden provides the tools and procedures necessary to integrate the software without weakening the overall security of the current infrastructure.

### Systems Engineering Diagram

![](Engineering%20View.jpg)

### Perceived Threats - Drew

- Threats
- Threats
- More Threats!

### Security Features - Jensen

- Feature 1
- Feature 2
- Feature 3

## Team Motivation

As we looked at the course syllabus, we focused out attention on projects that would provide our team with a good foundation for a security centered avenue of approach.  We found that there was no perfect scenario in which our selection would be in a language we were all 100% confortable with, existed with many real world uses, and wasn't already combed through by experts to the point that there were few issues remaining within the program.  With this in mind, we understood that we would have to focus on the security of a problem and find a program that allowed us to fully work through an issue and learn how the process of contributing to the open source communities worked.

After speaking with Dr. Gandhi, it was clear that we should select a project that would provide us with valuable experience that could be applied in both coorporate and individual environments. Our primary team motive for the selection of an open source project led in the desire to provide secure code for security based utilities with a coorporate minded focus.  We ended up selecting the Bitwarden Desktop Application as the focus of our open source project due to it's core mission of providing trusted security with open source transparency and global access.

## Open-Source Project Description

Bitwarden is a password manager designed with the interest of businesses and individuals in mind. The software has numerous features and applications, most notably: the cross-platform capabilities and end-to-end encryption used to securely store and access any number of passwords. Addressing the individual plans offered by Bitwarden, users are able to create a free plan capable of taking advantage of the two features mentioned previously. Free users are also entitled to several core features including unlimitied devices, stored items, a password generator, and more. Business plans offer more advanced core features that appeal to the systems administration level of IT networking. These include features such as audit logs, API access, user groups, technical support, and tools for integration. As an important distinction, Bitwarden business accounts receive all the features provided by Bitwarden's individual program.

The project being addressed by our team is primarily focused on Bitwarden's desktop application. The software itself is comprised of the following languages:

TypeScript (45%), HTML (34%), SCSS (14%), JavaScript (5%), and Powershell (2%)

The software's Github page has a list of 60 contributors, the three largest being: kspearrin, joseph-flinn, and Hinton. The Github page has seen a fair amount of activity throughout the year with heavy activity around the start of the year and in May and June. Looking at the contributions to the master branch, there appear to be very few entirely dead areas within the changes.

In terms of use and popularity, Bitwarden seems moderately popular. It has been featured in multiple web articles and is well regarded for its free individual user tier. Unlike some other password managers, the lack of a required fee to use and massive storage for free users has been a strong selling point for the software and its related applications. The paid tier has also been regarded as a fairly priced alternative to some of the other paid password managers in the market.

The platform listed for the desktop application applies to all three of the major desktop operating systems: Windows, MacOS, and Linux.

Finally, regarding the documentation on Bitwarden's applications, the information is also open source through the Bitwarden Help project. Valuable documentation can be found on Bitwarden's Help page on their, the [Bitwarden Help Center](https://bitwarden.com/help/ "Bitwarden's Help Center"). The information is regularly updated and offers tools for readers to find other means of communication or even suggest features and documentation changes.

## Licensing Information

Bitwarden Desktop is licensed under the [GNU General Public License v3.0](https://github.com/bitwarden/desktop/blob/master/LICENSE.txt). This license allows: commercial use, distribution, modification, patent use, and private use. To do any of these, one must include this license and copyright notice, state any changes made to licensed product, disclose the source code when distributing the licensed material, and use the exact same license. Finally, this license contains a limitation of liability and no warranty. More information about this license can be found [here](https://www.gnu.org/licenses/gpl-3.0.en.html). 

## Contributing

Bitwarden Desktop welcomes contributions. They request that all contributions be pull requests against the `master` branch following the [contribution guidelines](https://github.com/bitwarden/desktop/blob/master/CONTRIBUTING.md). These guidelines describe the many ways anyone can contribute to the project as well as a [community forum](https://community.bitwarden.com/) contributors can collaborate at. Common contribution requests include feature requests, bugs, documentation, and translations. Contributors must use a [npm linter](https://www.npmjs.com/package/lint) to format their code in the style Bit Warden Desktop uses.  Before contributing any code, users must sign a [Contributor Agreement](https://cla-assistant.io/bitwarden/desktop) which states you waive all rights to your contributions and profits Bitwarden makes off of your contributions. 

Bitwarden Desktop also welcomes security audits as detailed in their [security policy](https://github.com/bitwarden/desktop/blob/master/SECURITY.md). Bitwarden requests that security issues are disclosed promptly, discreetly, and performed in good faith. This security policy then details what is out-of-scope including self-xss, physical access, and current issues. The policy also outlines that security testers may not perform a denial of service, spamming, social engineering, or physical attempts on Bitwarden property. 

Not listed on Bitwarden Desktop’s GitHub is [their HackerOne profile](https://hackerone.com/bitwarden) where they outline even more contribution guidelines and offer HackerOne reputation for valid reports on all Bitwarden products. 



## Security Related History

The Bitwarden desktop app either suffers from being chronically forgotten in security documentation or is considered a lower priority in comparison to their web app and web extensions. The security policy does not reference the desktop application in any of the scope definition statements instead defining “current release of Bitwarden” as “web vault, browser extension, and mobile apps.” This is not a condemnation as it may simply be a poor turn of phrase since the desktop app appears to just be the “web vault” that has escaped the confines of a browser. 

Bitwarden themselves appear to be dedicated to security even going so far as to undergo a third-party audit yearly and disclosing the findings publicly. This started with a code audit in 2018 and then penetration tests following that (with a gap in 2019 where no audit was conducted). The only flaw mentioned in the code audit directly relating to the desktop application is a potential RCE vulnerability stemming from a *shell.openExternal* call that was mitigated in 2018. However, this yearly pen-test audit (post 2018) also seems to lack a reference to the desktop application with the scope of the audit being “Bitwarden product website, web vault application, and backend server systems.”

Bitwarden’s security bug reporting appears to take place mostly on private channels. Security flaws appear to be taken private on GitHub if they actually require addressing. Bitwarden hosts a bug bounty program on hackerone.com, and their response statistics are very good to the 38 reports they’ve recieved. Reports are vetted within an average of six hours and a patch released within a month. Their bug bounty program offers no rewards other than a “Thanks” at this time.


## Repo Link

https://github.com/DoctorEww/software-assurance

## Team Reflection

From the start, Adam Spanier acted as a great team lead. He gathered all members of the team together and ensured that information was distributed to every member and provided encouraged for the creation of a great working environment.  Initially there was an issue with communication where information was primarily sent through UNO registered emails.  Chris did not have access to his UNO email address during the day, which hindered him from keeping in contact with the team.  The team was able to quickly adjust and add non-UNO emails to the group email chain as well as implement a Discord server for the team's discussions. Further, Drew quickly created a GitHub repository for our team to use in project collaboration.

Our team so far is being led very professionally by Adam. The team is consistently providing input on what path forward to take as well as conducting the research to keep informed on what the next steps should be.  With a team that has work outside of school, scheduling was an issue that appeared early on when trying to figure out a good time to work on the project.  The team however was very flexible and quick in finding a time that worked with everyone.  
