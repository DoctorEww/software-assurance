

# DeepScan

We preformed one automated scan using DeepScan. This tool is capable of scanning public GitHub repos for code flaws. The results of our scan can be found [here](https://deepscan.io/dashboard/#view=project&tid=16140&pid=19350&bid=500664&prid=&subview=issues). This scan reported 7 issues total. 1 issue was labeled medium and 6 issues were labeled low. 

## Medium

There was one issue labeled medium. This issue claimed a function needed an integer rather than a null value. However, after further research, we found that this was incorrect and that a null value is handled as intended. 

## Low

There were 3 import errors displayed. Each of these imports were noted as unused. However, upon manual review we assessed that these imports were used in other locations in the file. 

There were two switch statements without a break statement. This could potentially have a negative impact on the execution flow. However, in these cases there was no change in execution flow. If the authors wanted to make the code more clear. 

There was one unused variable. However, there is a comment above this variable detailing why it was unused. 

Upon manual review of these issues we were able to conclude that all of these issues were false positives, and that no changes were needed as a result of our DeepScan report. 