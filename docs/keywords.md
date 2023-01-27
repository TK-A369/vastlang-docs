# VastLang keywords

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
 - `call`
 - `callptr`