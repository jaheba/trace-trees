

# Trace-Trees

## Problem Statement

Tracing Just-In-Time Compilers compile and optimise traces -- units of code with linear control flow -- to fast machine code. The linear nature of traces has advantages and disadvantages. One of the disadvantages is that in order to represent control flow taken during execution of a program multiple traces have to be created and thus trace-trees are generated. Also in contrast to method-based approaches, parts of a program are always only translated after they have been executed; method-based JITs often compile whole function bodies and thus also compile parts of a program which might not have been executed before.

Although tracing-JITs can be added to an interpreter with relative ease and deliver good performance on smaller programs, it is generally assumed that the performance is hard to predict when more complex applications are executed.

Research and industrial efforts in the area of tracing JITs has slowed down significantly over the last two decades. When I asked experts, none of them had a profound answer to the whys.


### Research Question

What are the charasteristics of tracing JITs that can lead to unpredictable performance.


## Ideas

* Visualisation; make hot paths within a program visible.
    Create CFG and highlight edges depending on execution frequency.

* Collect trace of a whole program execution. We can then simulate the behaviour of the JIT and measure the impact of different threshold values.


## Related Work Papers

* **Exploring optimal compilation unit shapes for an embedded just-in-time compiler**
    Bruening, D. Duesterwald, E.

    **Summary:** Comparison of traces, loops and methods with respect to how much hot code each strategy covers. Conclusion: mix of loops and methods, or traces and methods work best, establish a 90/10 rule.
