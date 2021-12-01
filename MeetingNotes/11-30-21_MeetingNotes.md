**Team Meeting: Code Review**

*Code Review Strategy:*

The code review strategy proposed will incorporate the following elements: (1) automated code scanning tools will be used to scan the BitWarden Desktop Application for known code based weaknesses, (2) autoscan results will be checked via manual review, and (3) further manual review will be carried out in identified problem areas. Some notable targets for deeper manual code scanning include: (1) input validation and sanitization processes, (2) cryptographic operations, and (3) security documentation.

*Initial Findings:*

Based on initial automated code scans, 9 weaknesses were identified. Most notably, two switch statement fall throughs, a type mismatch, and multiple unused imports. Upon a cursory investigation, the findings indicate no weaknesses to the program.


**Team Meeting: Notes**

Scan the repo with auto tools
Manually review auto scans
Check identified problem areas such as:

*Areas*
    • Input validation and sanitization
    • Cryptography
    • Security Documentation

*Autoscanning tools*

    • Linters
    • Auto tool to hook to repo
    • Deepscan.io
        ◦ Switch Case Fall Through, no break (CopyToTp)
        ◦ Switch Case Fall Through, no break (removeOpenAtLogin)
            ▪ Break statement removed, then added, then removed.


*Questions:*

How many findings is he looking for?
How comprehensive?
What if we don’t really find anything?
	
