# Community Graph Research
This repositry contains research data for community graph analysis performed on top of statistical debudding of functions found in call stack of system calls.

# Test Script:
The test script contains the C code which is used for generating the data. The C code works in 5 different settings based on probability of bugs happening in different functions. Folder names represents the probability of each bugs in the different functions.

# Datasets:
THe datasets contains statistical debugging on functions based on failure, context, increase. These are calculated based on length of system calls taking place. If a system call is longer than a mentioned threshold, then functions in the call stack during that system call is considered failed (present or observed - depending on position in the call stack).
The dataset also contains the caller callee directed lists for gephi to import and perform analysis. Lastly, we have the gephi community analysis parameters being applied on the statistical debugging. Eight such parameters were choosen.

# Procedure to generate:
1. Run C code with perf: sudo perf record -g -e 'syscalls:sys_*' ./c
2. Record enough data and then stop perf.
3. Get the perf data in readable format: sudo perf script > test.txt
4. Run script1: python step1.py
5. Import the newthing.csv into gephi.
6. Run the following in gephi maintaining the sequence: Avg Degree, Avg Weighted Degree, HITS, Pagerank.
7. Export from gephi, make sure to export the nodes page. Click on options during export to make sure of it.
8. Save it as gephi.csv
9. RUn script2: python step3.py
