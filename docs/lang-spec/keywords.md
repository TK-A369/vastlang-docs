# Keywords in VastLang

There are many keywords in VastLang.

Most of them are instructions.

 - `syscall` - perform some operation with provided arguments, and possibly save returned result to variable.  
   Syntax: `syscall [syscall_name] [result_variable] [args_count] [args...]`  
   `syscall_name` should be string.  
   `result_variable` should be variable name to put result into, or `null`.  
   `args_count` should be integer - number of arguments.  
   `args...` should be arguments - constant number or string, or identifier - variable name.  
   Example: `syscall "print" null 1 "Hello world!"`
 - `jump` - unconditionally jump to location in program with given label.  
   Syntax: `jump [destination_label]`  
   `destination_label` should be identifier - name of label to jump to.
 - `jumpptr` - as `jump`, but jumps to address stored in variable, and not to arbitrary label.  
   Syntax: `jumpptr [destination_variable]`  
   `destination_variable` should be identifier - name of variable storing address to jump to.
 - `cjump` - conditionally jump to location in program with given label.  
   Syntax: `cjump [condition] [destination_label]`  
   `condition` should be identifier - name of variable. If its value is 0, jump won't be perfomed. If its value will be different from 0, jump to given label will be performed.  
   `destination_label` should be identifier - name of label to jump to.
 - `cjumpptr` - as `cjump`, but jumps to address stored in variable, and not to arbitrary label.  
   Syntax: `cjumpptr [condition] [destination_variable]`  
   `condition` should be identifier - name of variable. If its value is 0, jump won't be perfomed. If its value will be different from 0, jump to given label will be performed.  
   `destination_variable` should be identifier - name of variable storing address to jump to.
 - `call` - call function at location with given label.  
   Syntax: `call [destination_label] [args_count] [args...]`  
   `destination_label` should be identifier - destination label.  
   `args_count` should be integer - number of arguments.  
   `args...` should be arguments - constant number or string, or identifier - variable name.  
   This instuction pushes current program counter to stack.  
   Then pushes every argument to stack.
   If given argument is variable, then value of that variable is pushed to stack.  
   Arguments are pushed in normal order (i.e. `a`, `b`, `c`). So function body should pop them in reverse order (i.e `c`, `b`, `a`).  
   After that, arguments count is pushed to stack.  
   Lastly, program counter is set to function location, and depth counter is incremented.
 - `callptr` - as `call`, but calls function at address stored in variable, and not at arbitrary label.  
   Syntax: `call [destination_variable] [args_count] [args...]`  
   `destination_variable` should be identifier - destination label.  
   `args_count` should be integer - number of arguments.  
   `args...` should be arguments - constant number or string, or identifier - variable name.
 - `return` - returns from function called by `call` or `callptr` instruction  
   Syntax: `return [return_value]`  
   `return_value` should be constant number or string, or identifier - variable name.  
   It pops one value from stack, and writes it to program counter.  
   Then it pushes result to stack. If `return_value` is identifier - variable name - then it pushes value of this variable to stack.  
   Lastly it frees local variables.