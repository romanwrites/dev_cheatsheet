# C language stuff

## What would compiler do with strlen in a loop

Even with optimisation if use strlen with variable as a parameter, strlen will be called every time. But not with constant value.
<img src="img/c_compiler_strlen_in_loop.png">

## Tips
* To easily locate leaks in program on macOS, use debugger. Set breakpoints, and on every breakpoint use `leaks <your-program-process-name>`.
