CONTRIBUTIONS

Iason: 
 - Fork/join computation
 - Created child processes
 - Error handling

Siam:
 - Memory-mapped file I/O
 - Conducted experiement
 - Wrote README

REPORT
Experiment Results: 
Test run with threshold 2097152
real    0m0.393s
user    0m0.313s
sys     0m0.007s

Test run with threshold 1048576
real    0m0.188s
user    0m0.327s
sys     0m0.010s

Test run with threshold 524288
real    0m0.122s
user    0m0.338s
sys     0m0.011s

Test run with threshold 262144
real    0m0.105s
user    0m0.378s
sys     0m0.023s

Test run with threshold 131072
real    0m0.104s
user    0m0.392s
sys     0m0.027s

Test run with threshold 65536
real    0m0.115s
user    0m0.407s
sys     0m0.040s

Test run with threshold 32768
real    0m0.123s
user    0m0.420s
sys     0m0.061s

Test run with threshold 16384
real    0m0.124s
user    0m0.429s
sys     0m0.102s

Explanation: 

The parsort application carries out an array sorting task by partitioning the array into smaller chunks and assigning each chunk to an individual process for sorting. 
The size of these chunks is determined by a specified threshold value. A lower threshold results in a larger number of smaller chunks, which in turn leads to the creation of more processes. 
If sufficient CPU cores are available, this setup can facilitate a higher degree of parallelism.
During our testing phase, we noticed a pattern where the total real-time required for the sorting operation generally declined as we lowered the threshold, thereby increasing the level of parallelism. 
This improvement in speed can be attributed to the ability to perform more sorting tasks concurrently across different cores, thereby boosting the overall computational speed.
However, we also observed a point of diminishing returns, where further increases in parallelism did not lead to additional speed improvements. In fact, it resulted in a slowdown in the computation process. 
This point was reached when the threshold was reduced to below 131072. The likely cause for this is the overhead associated with the creation and synchronization of an increased number of processes. 
As the number of processes grows, so does this overhead, and beyond a certain point, it starts to negate the benefits derived from parallelism.   
In conclusion, while parallelism can greatly enhance the speed of sorting, there is an optimal level of parallelism that yields maximum speedup. 
Beyond this point, the cost of managing an increased number of processes surpasses the benefits derived from parallelism. 
The ideal threshold value is likely to vary based on the specific characteristics of the system, such as the number of cores and the efficiency of the operating system's process scheduling mechanism.