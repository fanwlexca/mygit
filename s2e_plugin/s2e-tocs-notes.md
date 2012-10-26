# User Interface

![Fig7](./pictures/fig7.png?raw=true)  

1. Path Selection  
	Data-based selection:  
		Annotations plugin:direct injection  
	Code-based selection:  
		CodeSelector plugin:enable multipath execution on whether the pc is within a target code area.  
	Priority-based selection:  
		define the order  
		Random, Depth First, Breath First etc.  
	MaxCoverage selector:  
		works in conjunction with coverage analyzers to heuristically select paths that maximize coverage.  
	PathKiller selector  
		deletes paths.  

2. Path Analysis  
	multipath analysis plugins:such as a performance profiler, memory checkers, crash detectors, or execution tracers.  
	single-path analysis tools:such as Valgrind, Oprofile [Levon and Elie 1998], or Microsoft Driver Verifier [Microsoft 2011a]  

	1. Reusing Existing Single-Path Analysis Tools.  

	2. Multipath Analyzers:  
	bug finders:  
		such as the WinBugCheck and MemoryChecker plugins  
			look for Windows “blue screens of death” and memory errors, and output the execution paths leading to the encountered bugs.  
	execution tracers:  
		InstructionTracer  
			selectively records the instructions executed along a path  
		MemoryTracer  
			which logs memory accesses and hardware I/O. Tracing can be used for many purposes, like offline coverage measurement or profiling.  
		PerformanceProfiler analyzer  
			counts cache misses,TLB misses, and page faults incurred along each path  		
	intercept Windows-specific events using undocumented interfaces or other hacks:  
		WindowsMonitor  
			parses and monitors Windows kernel data structures and notifies other plugins when the kernel loads a driver, a library, or an application.  
		CrashDumpGenerator plugin  
			generates a memory dump compatible with Microsoft WinDbg.  
	3. Offline Multipath Analyzers:  
	collecting execution traces and saving them to a file for offline analysis.  
	reverse engineering  
	core tracing plugin Logger  
		provides an interface to other plugins that they can use to log arbitrary data.  
		wraps the written data into a trace item object containing a path identifier, timestamp, size, and the plugin that wrote the item.  

3. Configuration Interface  
	combine plugins using the S2E configuration interface.(config.lua)there is a section in the script that lets the user control the plugin’s behavior.  

# Developer Interface

![Table II](./pictures/tableII.png?raw=true)   

Execution Path Abstraction:each path<->a distinct ExecutionState object instance  

The dynamic binary translator (DBT) turns blocks of guest code into corresponding host code; for each block of code this is typically done only \*\*once**.  

Custom Instructions:S2E opcodes are custom guest machine instructions that are directly interpreted by S2E.  
	creating symbolic values (S2SYM), enabling/disabling multipath execution (S2ENA and S2DIS) and logging debug information (S2OUT).  

# 2 examples

1.Using the S2E API to Build the Annotations Plugin:TODO  

2.Combining S2 E Plugins and In-VM Tools(useful)  











		




