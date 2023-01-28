# Maths

```
//Read a and b from stdin
syscall "print" null 1 "Enter a:"
syscall "readline" a 0
syscall "tonum" a 1 a
syscall "print" null 1 "Enter b:"
syscall "readline" b 0
syscall "tonum" b 1 b

//Calculate
add a b sum
subtract a b difference
multiply a b product
divide a b quotient

//Print
syscall "strcat" msg 23
	a " + " b " = " sum "\n"
	a " - " b " = " difference "\n"
	a " * " b " = " product "\n"
	a " / " b " = " quotient
syscall "print" null 1 msg

//Compare
eq a b cond
cjump cond ifEqual
gt a b cond
cjump cond ifGreater
lt a b cond
cjump cond ifLesser

//Print
:ifEqual
syscall "print" null 1 "a = b"
jump end

:ifGreater
syscall "print" null 1 "a > b"
jump end

:ifLesser
syscall "print" null 1 "a < b"

:end
```

## Explanation

This program is quite more complex than the previous ones.

It demonstrates usage of conditional jumps (`cjump`) and labels.

First part of program reads two numbers from stdin.

Second parts calculates their sum, difference, product and quotient.

Instructions `add`, `subtract`, `multiply`, `divide`, `eq`, `gt`, `ge`, `lt` and `le` take three arguments: two inputs and one output variable.

Next two statements print those calculations to stdout.

Rest of program is prints if a and b are equal, greater than, or less than.

`cjump` instruction takes two arguments - first is variable with condition, and second is destination label name.
Notice there are such labels (starting from colon) in code.

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