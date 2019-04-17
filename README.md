# cs1302-ce31 More Social Network Graph Analytics

In this class exercise, students will explore the use of different sorting algorithms in the
context of various data analytics problems related to the MyFace social network.

## References and Prerequisites

* [CSCI 1302 Maven Repository](http://cobweb.cs.uga.edu/~mec/cs1302-mvn-repo/)
* [CSCI 1302 Maven Tutorial](https://github.com/cs1302uga/cs1302-tutorials/blob/master/maven.md)

## Questions

In your notes, clearly answer the following questions. These instructions assume that you are
logged into the Nike server.

**NOTE:** If a step requires you to enter in a command, please provide in your notes the full
command that you typed to make the related action happen. If context is necessary (e.g., the
command depends on your present working directory), then please note that context as well.

### Getting Started

1. **This exercise picks up from the end of checkpoint three of 
   [`cs1302-ce30`](https://github.com/cs1302uga/cs1302-ce30/).** 
   If your group did not complete through checkpoint 3 of `ce30`, then you should do that now.  

1. **If you have a new group member,** then please add them as a collaborator via the
   repository's GitHub website (click "Settings" → "Collaborators"). This will send them
   an invite that they can accept either via email or by visiting the repository's website 
   on GitHub. **After accepting the invite,** the new group member should clone the repository
   via the the "SSH" URL under "Quick setup" on the repository's GitHub website.

1. Once each group member has completed the Getting Started steps, 
   pick an ordering for the group members (e.g., Group Member 1, Group Member 2, etc.).
   If a step is being performed by one group member, then everyone is expected
   to watch, pay attention, and take notes.
   
1. Your instructors may have updated the MyFace and Sorting libraries. Theses libraries are
   on the bleeding edge in order to meet the demand of your analytics programs. To make sure 
   you have the latest version of each library dependency, you can execute the following 
   Maven command in the same directory as your POM:

   ```
   $ mvn dependency:resolve -U
   ```

## Exercise Steps

1. **EVERYONE:** It turns out that your company stores the elements of the MyFace 
   `users` array on multiple servers on a network. This makes swapping elements in the array 
   costly as network lag is involved. Consider a scenario where you need to sort the `users` array 
   by user *social score* (as in the previous exercise) using each of the four algorithms available
   in the `cs1302.sorting` package.

   In your notes, write down which algorithm you think will be able to sort it the
   fastest (total time). We can approximate total time by adding up the total time spent
   doing comparisons and the total time spent doing swaps.

1. **NEXT GROUP MEMBER:** In `main`, adjust the code so that MyFace `users` array only contains
   `100` users. Then, write the code to sort the `users` array by user
   social score using each of the four algorithms available in the `cs1302.sorting` package.
   For this problem, you will need to supply a custom `Comparator<MyFaceUser>` implementation
   (probably using a lambda expression). You may use the `Swapper<MyFaceUser>` returned by
   `Swapper.getNetworkSwapper(100)` to simulate random network lag with a maximum delay of
   `100` milliseconds.
   
1. To avoid computing the total running time manually, let's write a bit of additional code
   to have the program print the total run time for each algorithm **in seconds**. To accomplish this,
   you will need to gain access to the individual statistics for comparisons and swaps using the
   methods provided in the [`Sort API`](http://cobweb.cs.uga.edu/~mec/cs1302-mvn-site/cs1302-sorting/apidocs/index.html).
   Add the code to print the total time (comparison time plus swap time) for each algorithm in
   seconds. **Note:** You will need to convert from nanoseconds to seconds before printing.

   1. Once your code code compiles and runs, **run it a couple times**. Each time, does your
      choice of algorithm win or lose? Write it in your notes!
      
   1. In addition to writing the winning algorithm, write down the total run time for each algorithm
      using the `100ms` delay network swapper.
      
   1. Also, write down the a rough estimate of the average swap / comparison time across all algorithms.
      No need to get a calculator out - just get a rough idea.  Which operation took more time?
      
   1. Stage, commit, and push all changes.

1. **EVERYONE:** Pull your changes from the group repository.

1. **EVERYONE:** Popularity in MyFace has increased! The social networking site just added `9900` new
   members! The increase in revenue from ad sales has allowed the company to update their network
   infrastructure which will dramatically reduce swap times.   

1. In `main`, adjust the code to reduce the swap delay to `1ms` and update the number of members to `10,000`. 
   In your notes, write down which algorithm you think will be able to sort our users the fastest (total time).
   
   1. Once your code code compiles and runs, **run it a couple times**. Each time, does your
      choice of algorithm win or lose? Write it in your notes!
      
   1. In addition to writing the winning algorithm, write down the total run time for each algorithm
      using the `100ms` delay network swapper.
      
   1. Also, write down the a rough estimate of the average swap / comparison time across all algorithms.
      No need to get a calculator out - just get a rough idea.  Which operation took more time?
      
   1. Stage, commit, and push all changes.

1. **EVERYONE:** Pull your changes from the group repository.
   
**CHECKPOINT**

1. **EVERYONE:** Your boss was contacted by a new startup company called "Insert Name Here" that helps people
   turn their ideas into books. They want to target the users that may be interested in becoming writers. Your
   boss has suggested to target the users whose messages contain big words. The idea being that people who
   talk to people who use big words are more likely to be writers. It may not be his best idea but it's a 
   starting point. You realize that sorting people by this updated criteria may result in an increase in
   comparison times for users. 
   
   In your notes, write down which algorithm you think will be able to sort users the fastest (total time)
   using this new criteria and our updated (`1ms` delay) network. 
   
1. **NEXT GROUP MEMBER (SWAP DRIVERS):** in `main`, write a method called `countLargeWords` that takes a 
   `MyFaceUser` as an argument and returns the total number of words with `5` or more characters across 
   all of their messages. You may need to reference the
   [MyFace Message API](http://cobweb.cs.uga.edu/~mec/cs1302-mvn-site/cs1302-myface/apidocs/index.html).
   
1. To make sure your method is working properly, modify the number of users in your social network to `25`. 
   Write a nested loop that prints the contents of all messages for each user along with the total count
   of large words across all messages. Make your print statements clear so that you can easily check
   that your method is working. **Note:** Each user has a random number of messages between `0` and the
   social network size divided by 10. That is [`0`, `25/10`]. 
   
   **Warning:** You are reading people's messages. We don't encourage this
   behavior, in general. Also, some of the messages might be a bit odd (people send weird things) - the
   contents of the messages were populated from the [Fortune Cookie Database] (https://github.com/bmc/fortunes).
   
1. Once you are sure that your method is working, update your `Comparator` so that our sorting algorithms
   will sort based on this updated criteria. In your notes, write down which algorithm you think will be able 
   to sort it the fastest according to total time.

1. Now, write the code in `main` to sort the `users` array by user their large word count using 
   each of the four algorithms available in the `cs1302.sorting` package.
   For this problem, you will need to use your custom `Comparator<MyFaceUser>` implementation.
   You should use the `Swapper<MyFaceUser>` returned by `Swapper.getNetworkSwapper(1)`.

   1. Change your social network size to `750` users for testing. Once your code code compiles 
      and runs, **run it a couple times**. Each time, does your choice of algorithm win or lose? 
      Write it in your notes!
      
   1. In addition to writing the winning algorithm, write down the total run time for each algorithm.
      
   1. Also, write down the a rough estimate of the average swap / comparison time across all algorithms.
      No need to get a calculator out - just get a rough idea.  Which operation took more time?
      
   1. Stage, commit, and push all changes.

1. **EVERYONE:** Pull your changes from the group repository.

**CHECKPOINT**
 
<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
