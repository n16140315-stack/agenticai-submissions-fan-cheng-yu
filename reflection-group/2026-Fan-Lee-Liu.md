# Reflection: Agent vs Chat-Based ECG HRV Analysis

**Group:** 2026-Fan-Lee-Liu  
**Members:** Cheng-Yu Fan, Po-Lin Lee, Wu-Jun Liu
**License:** CC-BY-4.0

## Tools

Custom Python-based AI Agent system vs. ChatGPT-4

## Task Description

We compared approaches for analyzing ECG data to extract heart rate variability(HRV) features and generate an automated physiological state assessment based onfrequency-domain indicators.

The task focused on ECG signal reconstruction, R-peak detection, HRV spectral analysis, and interpretation of LF/HF ratio.

## Agent Approach

Our AI agent system:

1. Automatically reconstructed a continuous ECG signal from segmented heartbeat data
2. Cleaned the ECG signal using NeuroKit2 preprocessing methods
3. Detected R-peaks using the Pan-Tompkins algorithm
4. Computed frequency-domain HRV metrics (LF, HF, LF/HF ratio)
5. Generated a structured visual report and assessment result

The agent executed the full analysis pipeline in a single run with no manual intervention after the script was initiated.

## Chat Approach

Using a chat-based approach with ChatGPT-4:

1. We asked how to perform HRV frequency-domain analysis from ECG data
2. ChatGPT provided code snippets for individual processing steps
3. We manually copied, executed, and adjusted the code
4. Errors and missing details required multiple follow-up prompts
5. Results and interpretations were manually compiled into a report

This process involved repeated interactions and manual orchestration of each analysis step.

## Performance Comparison

| Metric | Agent | Chat-based |
|--------|-------|------------|
| Time to complete | ~30 sec | ~30–45 min |
| Manual steps required | 1 (run script) | 10+ |
| Errors encountered | 0 | Several minor issues |
| Output consistency | High | Varied |

## Analysis

The performance difference occurs because:

1. **Workflow automation:**  

&nbsp;  The agent executes a predefined pipeline end-to-end, while the chat-based
&nbsp;  approach requires manual coordination of each step.

2. **Tool integration:**  

&nbsp;  The agent directly interfaces with signal-processing libraries. Chat-based
&nbsp;  solutions can only suggest code that must be executed and debugged by users.

3. **State management:**  

&nbsp;  The agent maintains analysis context throughout the workflow, whereas chat
&nbsp;  interactions require repeated clarification.

4. **Error reduction:**  

&nbsp;  Automation reduces human error in repetitive signal-processing tasks.

## Lessons Learned

- Agentic AI is effective for structured, multi-step biomedical data workflows
- Chat-based AI is better suited for exploratory learning and one-off questions
- Agent-based systems provide higher reproducibility and efficiency
- The benefits of agents increase as task complexity and repetition grow