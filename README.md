# Starve-Free-Reader-Writer-s-solution

This is a pseudo-code for implementing Starve Free Reader-Writer's problem.
We will implement this by using three semaphores:-
1. mutex --> It takes care about the condition of mutual exclusion for each process of reading. And it is initialized with 1.
2. read_write_mutex --> It takes care of the condition of writing exclusively. And it is initialized with 1.
3. order --> It takes care of the condition of mutual exclusion in the whole process.

An integer variable read__count is used of saving the count of readers. Initialized with a value of 0.

//under Readers section
As we have taken order semaphore for maintaining mutual exclusion irrespective of the processes. We will use this in a situation where suppose the reader is waiting for a writer's process to complete then the reader is put in the FIFO queue of order semaphore.
A mutex lock is also implemented to take care of mutual exclusion conditions among reader processes along with keeping the reader process count. If reader__count is found to be greater than we command the writer process to wait by setting read_write_mutex to wait. And sread_write_mutex semaphore is released when read___count is found equal to 0.


//under Writers section 
The order semaphore is used in a similar way as in the reader section for queuing writers in the FIFO queue. And read_write_mutex for implementing condition that if the writer process has locked the semaphore no other processes can enter.
