Check in - Nov 10, 2021

Is our process good?
Are we achieving enough granularity?


Can't just add process to the end of it

We will be using the UI, UX (Maybe this is our only DFD)
All of these data flows will be coming in through the same UI and going to the same Database
We might end up with quite a bit of overlap
It is okay to abstract that down and consolidate the processes

Processes are code based, not function based.
If the process shares the same memory space, there's no need to separate processes out.

Because the bit warden application 
If process is out of our control, then we have an external interactor.
Undue complication?

Use use cases to tell us what threats there are.
This is what WE want, not what Bitwarden currently provides
We are creatinga  DFD the way we think it should work.
We are building software we think would be implemented correctly.
Do this analysis SEPARATE from what currently exists in Bitwarden.
Don't get carried away with threat boundaries

Unless we see different processes being spawned

Explicitly build a Level 0 for WHOLE systems, then deep dive into single scenarios.
What kind of mitigations for these SPECIFIC threats?
Is this actually implemented in our application.
Creating more DFD's is really helping much architecturally.
