# Read and print 2

```
syscall "readline" data 0
syscall "strcat" msg 3 "Text you entered is " data "."
syscall "print" null 1 msg
```

## Explanation

This program does the same thing as the previous one. It reads one line of text from stdin and prints it to stdout.

But instead of calling print with 3 arguments, it firstly concencates those three strings, and then prints it at once.

## Requirements

This example requires `print`, `readline` and `strcat` syscalls. The last one is core syscall, and thus should be always available.
The Lua program which uses VastLang library should provide such first two syscalls.

If you run this example on your own machine, on your own interpreter, you should have something like this in your Lua program:

```lua
local vm = interpreter.newVM()
interpreter.addSyscallsCore(vm) -- This adds some standard syscalls
interpreter.addSyscalls(vm, {
	print = function(args)
		print(table.unpack(args))
	end,
	readline = function(_)
		return io.read("l")
	end
})
```