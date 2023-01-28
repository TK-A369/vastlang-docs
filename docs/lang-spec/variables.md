# Variables

Assignment statement, or some of keyword statements (those which write something to variable) can create new variable.

Variable has following properties:

 - name
 - value
 - depth
 - thread

First two are self-explanatory.

When variable is created, its depth is set to current depth counter value (see [functions](../functions/)), and its thread is set to current thread (see [threads](../threads/)).

Variable is considered **global** when its depth is equal to 0.
Global variable can be accessed from anywhere.

Otherwise, if variable's depth is greater than 0, it's **local**.
Local variable can be accessed only from function which created it - when current depth is equal to variable's depth; and only from thread which created it - current thread id is equal to variable's thread.