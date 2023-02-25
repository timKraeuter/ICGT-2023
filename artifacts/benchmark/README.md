# Prerequisites
1. Install the command-line benchmark tool [hyperfine](https://github.com/sharkdp/hyperfine#installation).
    - The benchmark was run with hyperfine version **1.15.0** on Windows 10.
    - The hyperfine windows release **1.15.0** is contained in `artifacts/dependencies`.
2. The benchmark was run with Groove version **5.8.1**, which is contained in `groove-5_8_1` and does not have to be installed.
However, Java version 11 or later must be installed.

All benchmarks were run using a Windows 11 machine with an AMD Ryzen 7700X processor with 32 GB DDR5-5600 RAM on NVMe SSD storage.

# HOT transformation benchmark
1. Clone this repository.
2. Open a terminal in **this folder**.
3. Run the following commands:

**Benchmark**:
```bash
hyperfine -L bpmnModel models/e001.bpmn,models/e002.bpmn,models/e006.bpmn,models/e007.bpmn,models/e008.bpmn,models/e009.bpmn,models/e010.bpmn,models/e011.bpmn,models/e015.bpmn,models/e016.bpmn "java -jar ruleGenerator-1.jar {bpmnModel} ./" --output ./HOToutput.txt --export-json HOTstats.json
```

The HOT takes less than 1s and thus is adequately fast.
We suspect most of the time is spent doing I/O, i.e., reading the input BPMN file and writing the graph transformation rules for Groove.
To summarize, the HOT runtime could be further optimized if one avoids writing the generated GT system to stable storage.
Instead, the GT system could remain in the main memory and be accessed from there.  

# State space generation benchmark

# Auxiliary information

Groove graph grammars were generated with the following command (java 11 needs to be installed):
```bash
    java -jar ruleGenerator-1.jar models/e001.bpmn ./
```