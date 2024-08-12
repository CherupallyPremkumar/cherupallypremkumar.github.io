### 1\. About the Project

**Summary**: The project is about checking whether a large number is prime using parallel computing with MPI (Message Passing Interface). The goal is to speed up the process by dividing the work among multiple processors.

**Example**: Suppose you have a number like 1,000,000,003, and you want to check if it's prime. Doing this on a single processor would take a long time, especially if you have to check many such numbers. By using MPI, you can distribute the work across several processors, so each processor checks a portion of possible divisors, speeding up the overall process.

### 2\. Problem Description

**Summary**: The problem is to determine if a given number n is prime. A prime number is one that has no divisors other than 1 and itself.

**Example**: For example, consider n = 11. The only divisors of 11 are 1 and 11, so it is a prime number. But if n = 12, it can be divided by 1, 2, 3, 4, 6, and 12, so it’s not a prime number.

### 3\. Description of Algorithm

#### Computational Steps:

*   **Example**: If you have 4 processors, one of them will be the master (rank 0), and the others will be workers (ranks 1, 2, 3).
    
    *   MPI environment is initialized, and each process is assigned a rank (ID).
        
*   **Example**: Suppose n = 11. The master process will send 11 to all worker processes. After all workers check their portions, the master collects the results. If no divisors are found, the master concludes that 11 is prime.
    
    *   Checks if n is greater than 1.
        
    *   Sends the number n to all worker processes.
        
    *   Collects results from the workers.
        
    *   If any worker finds a divisor, it concludes that n is not prime.
        
*   **Example**: If there are 3 worker processes and n = 11, one worker might check divisibility by 2, 5, 8 (e.g., starting at 2 and jumping by 3), the second by 3, 6, 9, and the third by 4, 7, 10.
    
    *   Receive the number n from the master.
        
    *   Each worker checks a portion of possible divisors.
        
    *   Send the results back to the master.
        

#### Division of Work:

*   The range of numbers to check for divisibility is divided among the worker processes.
    

**Example**: If you have 3 workers and need to check divisibility up to 11, the work might be divided as:

*   Worker 1: Check 3, 6, 9
    
*   Worker 2: Check 4, 7, 10
    
*   Worker 3: Check 5, 8
    

#### Communication Between Processors:

*   **Sending the Number**: The master sends the number n to each worker.
    
*   **Receiving the Number**: Workers receive n from the master.
    
*   **Sending Results**: Workers send back whether they found any divisors.
    
*   **Receiving Results**: The master collects these results.
    

**Example**: The master sends n = 11 to each worker. Each worker checks its range and sends back "no divisor found" if they don't find any divisors. The master then decides if 11 is prime.

#### Synchronization:

*   Ensures all workers finish their checks before the master makes the final decision.
    

**Example**: The master waits for all worker results before concluding that 11 is prime.

### 4\. Input and Output

*   **Input**: The number n to check for primality.
    
*   **Output**: Whether n is prime and the total runtime of the program.
    

**Example**: If n = 11, the output might be:

*   "11 is prime."
    
*   "Total runtime: 0.03 seconds."
    

### 5\. Performance Analysis

#### Strong Scaling:

*   **Strong Scaling**: Measures how the runtime changes with the number of processors for a fixed problem size.
    

**Example**: If checking n = 11 takes 1 second with 1 processor, and 0.5 seconds with 2 processors, the program shows strong scaling.

Processors Execution Time (Sec)

4 0.359012

8 0.120213

16 0.052258

24 0.032980

#### Weak Scaling:

*   **Weak Scaling**: Measures how the runtime changes with the number of processors when the problem size per processor is fixed.
    

**Example**: If you double both the number of processors and the size of n, weak scaling measures how well the program maintains runtime.

Processors Problem Size Execution Time (Sec)

4 77777777 0.355576

8 155555554 0.239588

16 311111108 0.001529

24 466666662 0.002713

### Summary:

Using MPI, you distribute the workload of checking if a number is prime across multiple processors, which allows the task to be completed faster. The program demonstrates both strong and weak scaling, showing how efficient it is at utilizing additional processors.