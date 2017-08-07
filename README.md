

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

* **Efficient Path Profiling**; *1996*; Ball, T. Larus J.R.

    **Summary**: Profiling just the edges of a CFG (i.e. DAGs (directed acylic graphs)) blurs the actual path taken during execution. The authors instead describe an algorithm that adds manageable overhead during tracing (31% over 16% when just recording edges) but delivers accurate results. By assigning values to some edges and accumulating these values during execution leads to a unique number which identifies the path taken.

* **Softare Profiling for Hot Path Prediction: Less is More**; *2000*; Duesterwale, E. Bala, V.

    **Summary:** The authors show that in dynamic compilation systems path profile accuracy is less important than fast results. "Offline profiles are summaries of program behaviour while online profiles are predictions." Instead of using path profiles, only potential loop headers have associated counters. Also, choosing the right threshold value (called delay in the paper) has an impact on performance and has to balance opportunity costs.

* **Exploring optimal compilation unit shapes for an embedded just-in-time compiler**; *2000*; Bruening, D. Duesterwald, E.

    **Summary:** Comparison of traces, loops and methods with respect to how much hot code each strategy covers. Conclusion: mix of loops and methods, or traces and methods work best, establish a 90/10 rule.

* **Incremental Dynamic Code Generation with Trace Trees**; *2006*; Gal, A. Franz. M

    **Summary:** The authors prodive a model for trace-trees and describe a prototype implementation for the JamVM. They compare their results to other Java VMs, most notably hotspot over 7 benchmarks. Their protoype implementation reaches a speedup over pure interpreted execution of 7, whilst HotSpot maintains a 10x speedup. The authors highlight that compared to HotSpot their implementation compilres 100-700x faster and emits 30x less code.
