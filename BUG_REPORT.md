### UNIT TESTS

## Initial Unit Test Coverage Report

File             | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
-----------------|---------|----------|---------|---------|-------------------
All files        |   40.29 |    21.33 |   61.53 |   34.42 |                   
 src             |       0 |        0 |       0 |       0 |                   
  app.js         |       0 |        0 |       0 |       0 | 1-22              
 src/routes      |       0 |        0 |       0 |       0 |                   
  tasks.js       |       0 |        0 |       0 |       0 | 1-72              
 src/services    |     100 |    94.11 |     100 |     100 |                   
  taskService.js |     100 |    94.11 |     100 |     100 | 22                
 src/utils       |       0 |        0 |       0 |       0 |                   
  validators.js  |       0 |        0 |       0 |       0 | 1-36              
-----------------|---------|----------|---------|---------|-------------------
Test Suites: 1 failed, 1 total
Tests:       3 failed, 19 passed, 22 total
Snapshots:   0 total
Time:        0.72 s, estimated 1 s
Ran all test suites.

## 3 BUGS

---------------------
# completeTask() service

EXPECTED BEHAVIOR : calling completeTask service providing a task's id should only change the status to 'done' and not affect any other field in the task

WHAT ACTUALLY HAPPENS : calling the completeTask service changes the status to done, but also changes the priority to medium everytime its called

DISCOVERY : via manual testing and code overview at first, confirmed while running tests

FIX : remove the line that changes the priority everytime the service is called

----------------------

# getByStatus() service

EXPECTED BEHAVIOR : calling getByStatus service providing a valid status argument should return every task that has that status

WHAT ACTUALLY HAPPENS : providing a portion of a valid status still returns data. In worst possible scenarios, it may provide tasks from 2 or all valid status

DISCOVERY : via manual testing and code overview at first, confirmed while running tests

FIX : instead of using .includes(), it is better to have an array or object that contains all valid status and check if the status that was provided is also existing in the status container

---------------------

# getPaginated() service

EXPECTED BEHAVIOR : returns a specific group of tasks which was retrieved via the split method from the main tasks array using the limit and page values that are provided by the user

WHAT ACTUALLY HAPPENS : setting the page query to 1 does not return the first 2 items of task array and is offsetted

DISCOVERY : via manual testing and code overview at first, confirmed while running tests

FIX : subtract the page value by 1 so it matches with the actual tasks that the user is trying to find (this is what I fixed)

----------------------

## Coverage Report after fixing Bug 3

File             | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
-----------------|---------|----------|---------|---------|-------------------
All files        |   40.29 |    21.33 |   61.53 |   34.42 |                   
 src             |       0 |        0 |       0 |       0 |                   
  app.js         |       0 |        0 |       0 |       0 | 1-22              
 src/routes      |       0 |        0 |       0 |       0 |                   
  tasks.js       |       0 |        0 |       0 |       0 | 1-72              
 src/services    |     100 |    94.11 |     100 |     100 |                   
  taskService.js |     100 |    94.11 |     100 |     100 | 22                
 src/utils       |       0 |        0 |       0 |       0 |                   
  validators.js  |       0 |        0 |       0 |       0 | 1-36              
-----------------|---------|----------|---------|---------|-------------------
Test Suites: 1 failed, 1 total
Tests:       2 failed, 20 passed, 22 total
Snapshots:   0 total
Time:        0.691 s, estimated 1 s

### INTEGRATION TESTS

## Initial Integration Test Coverage Report

File             | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
-----------------|---------|----------|---------|---------|-------------------
All files        |   94.77 |       88 |    92.3 |   94.26 |                   
 src             |   69.23 |       75 |       0 |   69.23 |                   
  app.js         |   69.23 |       75 |       0 |   69.23 | 10-11,17-18       
 src/routes      |     100 |       90 |     100 |     100 |                   
  tasks.js       |     100 |       90 |     100 |     100 | 20-21             
 src/services    |     100 |    94.11 |     100 |     100 |                   
  taskService.js |     100 |    94.11 |     100 |     100 | 22                
 src/utils       |   86.95 |    85.29 |     100 |   86.95 |                   
  validators.js  |   86.95 |    85.29 |     100 |   86.95 | 22,28,31          
-----------------|---------|----------|---------|---------|-------------------
Test Suites: 1 failed, 1 total
Tests:       6 failed, 20 passed, 26 total
Snapshots:   0 total
Time:        0.532 s, estimated 1 s


## BUGS

Majority are found in the unit tests, however there a few validation checks that are missing that lets some unwanted data to be registered in the app


### OVERALL COVERAGE REPORT

File             | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
-----------------|---------|----------|---------|---------|-------------------
All files        |   94.77 |       88 |    92.3 |   94.26 |                   
 src             |   69.23 |       75 |       0 |   69.23 |                   
  app.js         |   69.23 |       75 |       0 |   69.23 | 10-11,17-18       
 src/routes      |     100 |       90 |     100 |     100 |                   
  tasks.js       |     100 |       90 |     100 |     100 | 20-21             
 src/services    |     100 |    94.11 |     100 |     100 |                   
  taskService.js |     100 |    94.11 |     100 |     100 | 22                
 src/utils       |   86.95 |    85.29 |     100 |   86.95 |                   
  validators.js  |   86.95 |    85.29 |     100 |   86.95 | 22,28,31          
-----------------|---------|----------|---------|---------|-------------------
Test Suites: 2 failed, 2 total
Tests:       8 failed, 40 passed, 48 total
Snapshots:   0 total
Time:        0.534 s, estimated 1 s



