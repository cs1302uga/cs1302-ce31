# cs1302-ce31 More Social Network Graph Analytics

In this class exercise, students will further explore the use of different sorting algorithms 
in the context of various data analytics problems related to the MyFace social network.

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
   
   If you have not yet written a method to compute a `MyFaceUser` social score,
   here is a sample implementaton:
   
   ```java
   public static int socialScore(MyFaceUser user) {
       return user.getFriends().size() * user.getName().length() / user.getAge()
   } // socialScore
   ```
   
   Given the `socialScore` method above, you can create your **reverse social score**
   comparator by taking the reverse, ordered difference between two user social
   scores.

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

1. **NEXT GROUP MEMBER (SWAP DRIVERS):** In `main`, adjust the code so that MyFace `users` array 
   only contains `75` users. Then, write the code to sort the `users` array by user
   social score using the selection sort, inserstion sort, and quicksort algorithms available 
   in the `cs1302.sorting` package -- your boss heard that 
   [former President Obama thinks, "the bubble sort is not the way to go."](https://youtu.be/k4RRi_ntQc8?t=34)
   For this problem, you will need to supply a custom `Comparator<MyFaceUser>` implementation
   (probably using a lambda expression). You may use the `Swapper<MyFaceUser>` returned by
   `Swapper.getNetworkSwapper(100)` to simulate random network lag with a maximum delay of
   `100` milliseconds.
   
   1. To avoid computing the total running time manually, let's write a bit of additional code
      to have the program print an _estimate_ for total run time of each algorithm **in seconds**. 
      To accomplish this, implement the following method:
   
      ```
      /**
       * Given a reference to a {@code Stats} object returned from the {@code getStats()}
       * method of a sorting algorithm, print the sum of the values returned by the 
       * {@code getSum()) method of each statistic (converted to seconds) and also print the 
       * values returned by the {@code getAverage()} method of each statistic (converted to
       * microseconds).
       * 
       * @param stats an object containing the statistics for a sorting algorithm execution
       */
      public static void printEstimate(Sort.Stats stats);
      ```
      
      Here is an example of the expected output of this method:
      
      ```
      Total Runtime Estimate   = 27.4746948 s
      Average Comparision Time = 7.47091 us
      Average Swap Time        = 48938.210 us
      ```
      
      You do NOT need to truncate digits after the decimal point to specific precision.
      
   1. Add the code to print the total runtime estimate and individual average operation times
      for each algorithm (using your convenient new method) except for `BubbleSort`.

   1. **Before running,** guess which algorithm you think will win. That is, write down which 
      algorithm you think will be able to sort our users the fastest (by total time estimate).

   1. Once your code code compiles and runs, **run it three times** and the table
      below in your notes (title the table **75 users -- 100 ms delay**):
      
      | Algo      | Runtime 1 | Runtime 2 | Runtime 3 | Avg. Comp. Time | Avg Swap Time |
      |-----------|-----------|-----------|-----------|-----------------|---------------|
      | ~Bubble~  |-----------|-----------|-----------|-----------------|---------------|
      | Selection |-----------|-----------|-----------|-----------------|---------------|
      | Insertion |-----------|-----------|-----------|-----------------|---------------|
      | Quick     |-----------|-----------|-----------|-----------------|---------------|
       
      For each run, write down the runtime estimate **in seconds** and circle the fastest
      one. Did your choice of algorithm win or lose each time? In the other table, not the
      average operation times **in microseconds**.
      
   1. Stage, commit, and push all changes.

1. **EVERYONE:** Pull your changes from the group repository.

**CHECKPOINT**

1. **NEXT GROUP MEMBER (SWAP DRIVERS):** Popularity in MyFace has increased! The social networking site
   just added `9900` new members! The increase in revenue from ad sales has allowed the company to update 
   their network infrastructure which will dramatically reduce swap times.   

   In `main`, adjust the code to reduce the swap delay to `1ms` and update 
   the number of members to `10,000`. 
   
   1. **Before running,** guess which algorithm you think will win. Note which algorithm you 
      think will be able to sort our users the fastest (total time estimate).

   1. Once your code code compiles and runs, **run it three times** and the table
      below in your notes (title the table **10,000 users -- 1 ms delay**):
      
      | Algo      | Runtime 1 | Runtime 2 | Runtime 3 | Avg. Comp. Time | Avg Swap Time |
      |-----------|-----------|-----------|-----------|-----------------|---------------|
      | Selection |-----------|-----------|-----------|-----------------|---------------|
      | Insertion |-----------|-----------|-----------|-----------------|---------------|
      | Quick     |-----------|-----------|-----------|-----------------|---------------|
       
      For each run, write down the runtime estimate **in seconds** and circle the fastest
      one. Did your choice of algorithm win or lose each time? In the other table, not the
      average operation times **in microseconds**.
      
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
   
   To make sure your method is working properly, modify the number of users in your social network to `25`. 
   Write a nested loop that prints the contents of all messages for each user along with the total count
   of large words across all messages. Make your print statements clear so that you can easily check
   that your method is working. **Note:** Each user has a random number of messages between `0` and the
   social network size divided by 10. That is [`0`, `25/10`]. 
   
   **Warning:** You are reading people's messages. **We don't encourage this behavior, in general.** 
   I know it says we can do it in the [EULA](https://en.wikipedia.org/wiki/End-user_license_agreement),
   but we know that most MyFace users don't read that thing. Also, some of the messages might be a bit 
   odd (people write weird stuff sometimes) -- the contents of the messages were populated from the 
   [Fortune Cookie Database](https://github.com/bmc/fortunes).
   
1. Once you are sure that your method is working, update your `Comparator` so that our sorting 
   algorithms will sort based on this updated criteria.

1. Now, write the code in `main` to sort the `users` array by user their large word count
   using the selection sort, inserstion sort, and quicksort algorithms available 
   in the `cs1302.sorting` package. For this problem, you will need to use your custom 
   `Comparator<MyFaceUser>` implementation. You should use the `Swapper<MyFaceUser>` returned 
   by `Swapper.getNetworkSwapper(1)`. **Change your social network size to `750` users for testing.**

   1. **Before running,** guess which algorithm you think will win. Note which algorithm you 
      think will be able to sort our users the fastest (total time estimate).

   1. Once your code code compiles and runs, **run it three times** and the table
      below in your notes (title the table **750 users -- 1ms delay -- big comparator**):
      
      | Algo      | Runtime 1 | Runtime 2 | Runtime 3 | Avg. Comp. Time | Avg Swap Time |
      |-----------|-----------|-----------|-----------|-----------------|---------------|
      | Selection |-----------|-----------|-----------|-----------------|---------------|
      | Insertion |-----------|-----------|-----------|-----------------|---------------|
      | Quick     |-----------|-----------|-----------|-----------------|---------------|
       
      For each run, write down the runtime estimate **in seconds** and circle the fastest
      one. Did your choice of algorithm win or lose each time? In the other table, not the
      average operation times **in microseconds**.
      
   1. Stage, commit, and push all changes.

1. **EVERYONE:** Pull your changes from the group repository.

1. **CLOSING QUESTION:** What do you think your instructors wanted you to notice about the
   average comparison and average swap times between the three scenarios explored throughout
   the exercise?

**CHECKPOINT**
 
<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
