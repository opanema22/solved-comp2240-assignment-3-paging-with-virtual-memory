Download Link: https://assignmentchef.com/product/solved-comp2240-assignment-3-paging-with-virtual-memory
<br>
In assignment 1, we assumed that the system had an infinite amount of memory. In this assignment, the operating system has a limited amount of memory and this needs to be managed to meet process demands. You will write a program to simulate a system that uses paging with virtual memory. The characteristics of the system are described below:

<ul>

 <li><strong>Memory:</strong> The system has <strong>F</strong> frames available in main memory. During execution, the processor will determine if the page required for the currently running process is in main memory.

  <ol>

   <li>If the page is in main memory, the processor will access the instruction and continue.</li>

   <li>If the page is not in main memory, the processor will issue a page fault and block the process until the page has been transferred to main memory.</li>

   <li>Initially no page is in the memory. I.e. the simulation will be strictly demand paging, where pages are only brought into main memory when they are requested.</li>

   <li>In fixed allocation scheme frames are equally divided among processes, additional frames remain unused.</li>

  </ol></li>

 <li><strong>Paging and virtual memory:</strong> The system uses paging (with no segmentation).

  <ol>

   <li>Each process can have a maximum 50 pages where each page contains a single instruction.</li>

   <li>For page replacement you will need to apply <strong><em>least recently used</em> (LRU)</strong> and <strong><em>clock</em></strong></li>

   <li>Resident set is managed using ‘<strong><em>Fixed Allocation with Local Replacement Scope</em></strong>’ strategy. I.e. you can assume, frames allocated to a process do not change over the simulation period and page replacements (if necessary) will occur within the allocated frames.</li>

   <li>All pages are read-only, so no page needs to be written back to disk.</li>

  </ol></li>

 <li><strong>Page fault handling:</strong> When a page fault occurs, the interrupt routine will handle the fault by placing an I/O request into a queue, which will later be processed by the I/O controller to bring the page into main memory. This may require replacing a page in main memory using a page replacement policy (LRU or clock). Other processes should be scheduled to run while such an I/O operation is occurring.

  <ol>

   <li>Issuing a page fault and blocking a process takes no time. If a page fault occurs then another ready process can run immediately at the same time unit.</li>

   <li>Swapping in a page takes 6 units of time (if a page required by a process is not in main memory, the process must be put into its blocked state until the required page is available).</li>

  </ol></li>

</ul>




<ul>

 <li><strong>Scheduling:</strong> The system is to use a Round Robin short-term scheduling algorithm with time a quantum of <strong>Q</strong>.

  <ol>

   <li>Executing a single instruction (i.e. a page) takes 1 unit of time.</li>

   <li>Switching the processes does not take any time.</li>

   <li>If multiple process becomes ready at the same time then they enter the ready queue in the order of their ID.</li>

   <li>All the processes start execution at time <em>t</em>=0.</li>

   <li>If a process becomes ready at time unit <em>t</em> then execution of that process can occur in the same time unit <em>t</em> without any delay.</li>

  </ol></li>

</ul>







You are to compare the performance of the <strong><em>LRU</em></strong> and <strong><em>clock</em></strong> page replacement algorithms for the <strong><em>fixed allocation with local replacement</em></strong> strategy.

Please use the basic versions of the policies introduced in lectures.




<strong>Input and Output: </strong>

Input to your program should be via <strong>command line</strong> arguments, where the arguments are system configurations and   the names of files that specify the execution trace of different processes. All processes start execution at time 0, and are entered into the system in the order of the command line arguments (with the third argument being the earliest process). For example:




<h1>java A3 30 3 process1.txt process2.txt process3.txt</h1>




…where 30 is the number of frames (<strong>F</strong>) and 3 is the quantum size (<strong>Q</strong>) for Round Robin algorithm and the other arguments are text file names containing page references for each process (these are <strong>relative filenames</strong>, and <strong>SHOULD NOT BE HARDCODED</strong> in anyway).




Since we assume that each page contains a single instruction, an execution trace is simply a page request sequence.




For example: (process1.txt)

begin 1

3

2

1

4 3 end




This specifies a process that first reads page 1, then page 3, and so on until the ‘end’ is reached.




For each replacement strategy, the simulation should produce a summary showing, for each process, the total number of page faults, the time the page faults were generated, and the total turnaround time (including I/O time).




Sample inputs/outputs are provided. Working of the first example is presented with details of different levels. Your code will be tested with additional inputs.




Your program should output to standard output. Output should be <strong><u>strictly</u></strong> in the shown output format. <strong><u>If output is</u> <u>not generated in the required format then your program will be considered incorrect.</u></strong>







<strong>Programming Language: </strong>

The programming language is Java, versioned as per the University Lab Environment (<strong>currently a subversion of Java 1.8</strong>). You may only use standard Java libraries as part of your submission.




If you wish to use any language other than the preferred programming language, you must first notify (and justify this to) the course demonstrator (Dan).

<strong> </strong>

<strong> </strong>

<strong>User Interface: </strong>

The output should be printed to the console, and strictly following the output samples shown above (also given in the assignment package as separate files). You will lose marks if your program does not conform with the input/output formats.