Download Link: https://assignmentchef.com/product/solved-project-3-double-ended-queue-dequedeck-cpsc-131
<br>
<span style="font-size: 2.61792em; letter-spacing: -1px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">Introduction</span>

The Standard Library provides stack and queue classes (std::stack&lt;T&gt; and std::queue&lt;T&gt;), but they are actually adapters (a kind of wrapper) for the Standard Library’s deque class (std::deque&lt;T&gt;). Deques allow you to add items or remove them from either end of the deque (e.g., push_back, push_front, pop_back, and pop_front).

Most Standard Library implementations of std::deque&lt;T&gt; use two back-to-back vectors, a fronthalf vector that you call push_back on when you need to push to the front of the deque, and a backhalf vector that you call push_back on when you need to push to the back of the queue.







<table width="666">

 <tbody>

  <tr>

   <td width="222"><strong>minideque&lt;T&gt; </strong></td>

   <td width="222"><strong>std::vector&lt;T&gt; fronthalf </strong></td>

   <td width="222"><strong>std::vector&lt;T&gt; backhalf </strong></td>

  </tr>

  <tr>

   <td width="222"><strong>push_front(value) </strong></td>

   <td width="222">fronthalf.push_back(value)</td>

   <td width="222"> </td>

  </tr>

  <tr>

   <td width="222"><strong>push_back(value) </strong></td>

   <td width="222"> </td>

   <td width="222">backhalf.push_back(value)</td>

  </tr>

  <tr>

   <td width="222"><strong>pop_front(value) </strong></td>

   <td width="222">fronthalf.pop_back(value) *</td>

   <td width="222"> </td>

  </tr>

  <tr>

   <td width="222"><strong>pop_back() </strong></td>

   <td width="222"> </td>

   <td width="222">backhalf.pop_back() *</td>

  </tr>

  <tr>

   <td width="222"><strong>front() </strong></td>

   <td width="222">usually calls fronthalf.back() — if fronthalf is empty, will have to call backhalf.front()</td>

   <td width="222"> </td>

  </tr>

  <tr>

   <td width="222"><strong>back() </strong></td>

   <td width="222"> </td>

   <td width="222">usually calls backhalf.back() — if backhalf is empty, will have to call fronthalf.front()</td>

  </tr>

  <tr>

   <td width="222"><strong>operator[](i) </strong></td>

   <td colspan="2" width="444">returns the i-th element of the deque, could be in fronthalf or backhalf. Note that element 0 is the “top” element of frontvector.</td>

  </tr>

 </tbody>

</table>




The logic needs some adjusting if pop_back is called when the backhalf vector is empty, or if pop_front is called when the fronthalf vector is empty. In those cases, you will want to ​<strong>re-balance the values between the two vectors, </strong>​making sure you keep the queue items in order – move half the values from fronthalf to backhalf, or vice-versa. It will take a little time to get this part to work correctly. Do not expect it to take 5-10 minutes.

<h1>Objective</h1>

You are given a partial implementation of a “mini-deque” class. minideque&lt;T&gt;​​        ​is a templated class that holds the deque. Unlike the actual std::deque&lt;T&gt; class, minideque will <u>​<strong>NOT</strong></u>​ have the iterator classes (iterator, const_iterator, reverse_iterator, and const_reverse_iterator). This means you will also ​<strong><u>NOT</u></strong>​ have to provide the iterator-based functions: erase, begin and end.

<strong> </strong>

For this project, you should use the std::vector class from the C++ standard library.




Complete the implementation of class minideque&lt;T&gt;​​ , adding public/private member variables and functions as needed. Your code is tested in the provided main.cpp.​

<h1>Source Code Files</h1>

You are given “skeleton” code files with declarations that may be incomplete and without any implementation. Implement the code and ensure that all the tests in main.cpp​​    ​pass successfully.

minideque.h​: This is to be completed main.cpp: This calls a test function (in minideque.h) that tests the output of your minideque&lt;T&gt; class. You may wish to add additional tests, based on the ones already provided.

README.md​: You must edit this file to include the name and CSUF email of each student in your group. Do this even if you are working by yourself. This information will be used so that we can enter your grades into Titanium.

<h1>Hints</h1>

As you start implementing the minideque&lt;T&gt;​​ ​class, comment out the tests in main.cpp that you haven’t implemented yet in your class.  As you fill in the code for your class, uncomment the matching tests to make sure your class is working. Keep testing your code as you implement it. It is much easier to debug one method in your class than all of the methods at the same time. <strong> </strong>




Do not wait till the very end to test your code.

When you complete your project, all of the tests should run correctly.  Expected output of running the program is provided below.




Speak to your teachers if you need help designing your approach, or are having trouble compiling or debugging your code.  const errors can frequently prevent your code from compiling.  Note also that it is possible to be 95% of the way finished, but have the impression you are miles away. Your instructor can help you get over that final 5% if you need help. Don’t hesitate to ask.




<strong>EXPECTED OUTPUT: </strong>

<strong>PASSED dq[0] == dq.front(): expected and received 1 </strong>

<strong>PASSED dq[0] == 9: expected and received 9 </strong>

<strong>PASSED dq.front() == 1: expected and received 1 </strong>

<strong>PASSED dq.back() == 9: expected and received 9 </strong>

<strong>PASSED dq.front() == dq.push_front(el): expected and received 2 </strong>

<strong>PASSED dq.front() == dq.push_front(el): expected and received 3 </strong>

<strong>PASSED dq.front() == dq.push_front(el): expected and received 4 </strong>

<strong>PASSED dq.front() == dq.push_front(el): expected and received 5 </strong>

<strong>PASSED dq.front() == dq.push_front(el): expected and received 6 </strong>

<strong>PASSED dq.front() == dq.push_front(el): expected and received 7 </strong>

<strong>PASSED dq.front() == dq.push_front(el): expected and received 8 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 10 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 11 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 12 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 13 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 14 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 15 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 16 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 17 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 18 </strong>

<strong>PASSED dq.back() == dq.push_back(el): expected and received 19 </strong>

<strong>PASSED assign to array index: expected and received 9999 PASSED read from array index: expected and received 9999 </strong>

<strong> clearing the minideque… </strong>

<strong>NOTE: the minideque keeps REBALANCING the front/back to have similar # entries dq.pop_front() ==&gt; 7 6 5 4 3 2 1 | 9 10 11 12 13 14 15 16 17 18 19 , front:7, </strong>

<strong>back:19, size:18 </strong>

<strong>dq.pop_front() ==&gt; 6 5 4 3 2 1 | 9 10 11 12 13 14 15 16 17 18 19 , front:6, </strong>

<strong>back:19, size:17 </strong>

<strong>dq.pop_front() ==&gt; 5 4 3 2 1 | 9 10 11 12 13 14 15 16 17 18 19 , front:5, back:19, </strong>

<strong>size:16 </strong>

<strong>dq.pop_front() ==&gt; 4 3 2 1 | 9 10 11 12 13 14 15 16 17 18 19 , front:4, back:19, </strong>

<strong>size:15 </strong>

<strong>dq.pop_front() ==&gt; 3 2 1 | 9 10 11 12 13 14 15 16 17 18 19 , front:3, back:19, </strong>

<strong>size:14 </strong>

<strong>dq.pop_front() ==&gt; 2 1 | 9 10 11 12 13 14 15 16 17 18 19 , front:2, back:19, size:13 </strong>

<strong>dq.pop_front() ==&gt; 1 | 9 10 11 12 13 14 15 16 17 18 19 , front:1, back:19, size:12 dq.pop_front() ==&gt; | 9 10 11 12 13 14 15 16 17 18 19 , front:9, back:19, size:11 dq.pop_front() ==&gt; 10 11 12 13 14 | 15 16 17 18 19 , front:10, back:19, size:10 PASSED rebalancing fronthalf and backhalf vectors: expected and received 5 dq.pop_front() ==&gt; 11 12 13 14 | 15 16 17 18 19 , front:11, back:19, size:9 dq.pop_front() ==&gt; 12 13 14 | 15 16 17 18 19 , front:12, back:19, size:8 dq.pop_front() ==&gt; 13 14 | 15 16 17 18 19 , front:13, back:19, size:7 dq.pop_front() ==&gt; 14 | 15 16 17 18 19 , front:14, back:19, size:6 dq.pop_front() ==&gt; | 15 16 17 18 19 , front:15, back:19, size:5 </strong>

<strong>dq.pop_front() ==&gt; 16 17 | 18 19 , front:16, back:19, size:4 </strong>

<strong>PASSED rebalancing fronthalf and backhalf vectors: expected and received 2 </strong>

<strong>dq.pop_front() ==&gt; 17 | 18 19 , front:17, back:19, size:3 dq.pop_front() ==&gt; | 18 19 , front:18, back:19, size:2 dq.pop_front() ==&gt; | 19 , front:19, back:19, size:1 dq.pop_front() ==&gt; minideque is empty </strong>

<strong> </strong>

<strong>Passed: 25 out of: 25 total tests. …done. </strong>

<strong>Program ended with exit code: 0</strong>

<h1>Obtaining and submitting code</h1>

Click the assignment link to fork your own copy of the skeleton code to your PC. One student from a group clicks on the link below and forms a new team. The ​<u>team name must begin with your section</u> <u>number</u> (e.g., ​      2-​         Brians-team)​ . This student then invites his/her project partner as an “Outside collaborator” in the settings menu.




<u>Do not fork your repository to your personal github account</u><u>​</u>. Your code should have a URL like

https://github.com/CSUF-CPSC-131-Fall2018/project3-2-brians-team, NOT https://github.com/brian/project3-2-brians-team.




<a href="https://classroom.github.com/g/Ee6Y8QM5">https://classroom.github.com/g/Ee6Y8QM5</a>




Here is a video that shows the steps: <u>​</u><a href="https://www.youtube.com/watch?v=-52quDR2QSc">https://www.youtube.com/watch?v=-52quDR2QSc</a>

Then edit your code locally as you develop it. As you make progress, commit and push your changes to your repository regularly. This ensures that your work is backed up, and that you will receive credit for making a submission.




<h1>Development environment</h1>

The test platform is Linux with the g++ -std=c++14 compiler. For this reason, the recommended development platform is Linux.

<h2>Linux environment​</h2>

To attempt to compile the test program, use the following command: <strong>$ clang++ -g -std=c++14 *.cpp -o test</strong>




To attempt to run the compiled test program, use the following command:

<strong>$ ./test</strong>

<h1></h1>