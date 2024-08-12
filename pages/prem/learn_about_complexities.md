Here comes one of the interesting and important topics. The primary motive to use DSA is to solve a problem effectively and efficiently. How can you decide if a program written by you is efficient or not? This is measured by complexities. Complexity is of two types:

1.  [Time Complexity](https://www.geeksforgeeks.org/understanding-time-complexity-simple-examples/): Time complexity is used to measure the amount of time required to execute the code.
    
2.  [Space Complexity](https://www.geeksforgeeks.org/g-fact-86/): Space complexity means the amount of space required to execute successfully the functionalities of the code. You will also come across the term **Auxiliary Space** very commonly in DSA, which refers to the extra space used in the program other than the input data structure.
    

Both of the above complexities are measured with respect to the input parameters. But here arises a problem. The time required for executing a code depends on several factors, such as: 

*   The number of operations performed in the program, 
    
*   The speed of the device, and also 
    
*   The speed of data transfer if being executed on an online platform. 
    

So how can we determine which one is efficient? The answer is the use of asymptotic notation. 

> [**Asymptotic notation**](https://www.geeksforgeeks.org/analysis-of-algorithms-set-3asymptotic-notations/) is a mathematical tool that calculates the required time in terms of input size and does not require the execution of the code. 

It neglects the system-dependent constants and is related to only the number of modular operations being performed in the whole program. The following 3 asymptotic notations are mostly used to represent the time complexity of algorithms:

*   **Big-O Notation (Ο)** – Big-O notation specifically describes the worst-case scenario.
    
*   **Omega Notation (Ω)** – Omega(Ω) notation specifically describes the best-case scenario.
    
*   **Theta Notation (θ)** – This notation represents the average complexity of an algorithm.