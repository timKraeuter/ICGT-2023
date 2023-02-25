# Prerequisites
1. Install the command-line benchmark tool [hyperfine](https://github.com/sharkdp/hyperfine#installation).
    - The benchmark was run with hyperfine version **1.15.0** on Windows 10.
    - The hyperfine windows release **1.15.0** is contained in `artifacts/dependencies`.
2. The benchmark was run with Groove version **5.8.1**, which is contained in `groove-5_8_1` and does not have to be installed.
However, Java version 11 or later must be installed.

# HOT transformation benchmark
1. Clone this repository.
2. Open a terminal in **this folder**.
3. Run the following commands:

**Complete benchmark**:
```bash
hyperfine -L bpmnModel models/e001.bpmn,models/e002.bpmn,models/e006.bpmn,models/e007.bpmn,models/e008.bpmn,models/e009.bpmn,models/e010.bpmn,models/e011.bpmn,models/e015.bpmn,models/e016.bpmn "java -jar ruleGenerator-1.jar {bpmnModel} ./" --output ./HOToutput.txt --export-json HOTstats.json
```

# State space generation benchmark

# Auxiliary information

Groove graph grammars were generated with the following command (java 11 needs to be installed):
```bash
    java -jar ruleGenerator-1.jar models/e001.bpmn ./
```