# Guess the number game

```
syscall "randint" num 2 1 100	//Choose random number
syscall "print" null 1 "I choose a random number from 1 to 100. Try to guess it!"
:loop
	syscall "print" null 1 "Guess number: "
	syscall "readline" guess 0
	syscall "tonum" guess 1 guess
	syscall "eq" isEqual 2 guess num	//Check if guessed number is equal to selected
	cjump isEqual gameEnd				//If it is equal, break from the loop
	//If isn't equal
		syscall "gt" isGreater 2 guess num	//If it isn't equal, then check if it is greater
		cjump isGreater ifGreater			//If it is greater, then jump
	//If it isn't equal nor greater, then surely it is lesser
		syscall "print" null 1 "Your number is too small!"
		jump loop							//Go to beginning of loop
	//If is greater
		:ifGreater
		syscall "print" null 1 "Your number is too big!"
		jump loop
:gameEnd
syscall "print" null 1 "Congratulations!"
syscall "strcat" msg 3 "My number was " num "."
syscall "print" null 1 msg
```

## Explanation

TODO

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