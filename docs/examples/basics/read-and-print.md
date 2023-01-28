# Read and print

```
syscall "readline" data 0
syscall "print" null 3 "Text you entered is " data "."
```

## Explanation

This program reads one line of text from stdin and prints it to stdout.

It calls syscall with name "readline".
We want to save returned value to variable called `data`, so we write `data`.
This syscall doesn't take any arguments, so we write 0.

Then we want to print that text. So we call syscall `print`.
It doesn't return anything, so we write `null`.
We want to provide three arguments to this syscall, so we write arguments count 3, and then parts of string we want to print.

## Requirements

This example requires `print` and `readline` syscalls. The Lua program which uses VastLang library should provide such syscalls.

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