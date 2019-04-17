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
