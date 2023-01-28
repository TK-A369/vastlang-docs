# Hello world!

```
syscall "print" null 1 "Hello world!"
```

## Explanation

This program is very simple. It calls syscall with name "print".
It doesn't return anything, so we write `null`.
We want to provide one argument to this syscall, so we write arguments count 1, and the string we want to print - "Hello world!".

## Requirements

This example requires `print` syscall. The Lua program which uses VastLang library should provide such syscall.

If you run this example on your own machine, on your own interpreter, you should have something like this in your Lua program:

```lua
local vm = interpreter.newVM()
interpreter.addSyscallsCore(vm) -- This adds some standard syscalls
interpreter.addSyscalls(vm, {
	print = function(args)
		print(table.unpack(args))
	end
})
```