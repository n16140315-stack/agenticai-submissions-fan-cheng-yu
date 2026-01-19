\# Technical Report: HRV-Based Agent System for Physiological State Detection



\*\*Author:\*\* 2026-Lee-Po-Lin

\*\*Group Members:\*\* Lee Po-Lin, Fan Cheng-Yu, Liu Wu-Jun

\*\*License:\*\* CC-BY-4.0



\## Abstract



This report describes an agent-based system designed to analyze electrocardiogram (ECG) signals and assess physiological states using heart rate variability (HRV) metrics. The system combines two complementary analysis pipelines: frequency-domain HRV analysis based on NeuroKit2 and Pan-Tompkins R-peak detection, and time-domain HRV analysis with a rule-based decision agent. ECG signals are processed to extract R-peaks, RR intervals, and HRV features such as BPM, SDNN, RMSSD, and LF/HF ratio. Based on predefined physiological thresholds, the agent classifies the subject’s state as normal, fatigued, or high stress, and generates corresponding recommendations. This modular and interpretable design demonstrates how a simple agent architecture can integrate signal processing, feature extraction, and decision logic into a coherent physiological monitoring system.



\## Introduction



Fatigue and stress significantly affect human performance, safety, and health. Traditional assessment methods often rely on subjective questionnaires or clinical equipment that is not suitable for continuous or lightweight monitoring. Heart rate variability (HRV), derived from ECG signals, provides an objective and non-invasive indicator of autonomic nervous system activity.



The objective of this project is to develop an AI agent system that can:

1\. Process raw ECG data

2\. Extract meaningful HRV features

3\. Perform rule-based physiological state classification

4\. Provide interpretable recommendations based on analysis results



Rather than focusing on complex machine learning models, this project emphasizes clarity, interpretability, and modular agent design.



\## System Architecture



The proposed system follows a modular, agent-based pipeline architecture. The system is implemented using two coordinated analysis modules, each responsible for a specific stage of ECG and HRV processing.



\### Overall Pipeline



1\. ECG data loading

2\. Signal preprocessing and R-peak detection

3\. HRV feature extraction (time and frequency domains)

4\. Agent-based decision making

5\. Recommendation generation



\### Component Descriptions



| Component | Type | Description |

|---------|------|-------------|

| ECG Loader | Tool | Reads ECG data from CSV files and extracts signal columns |

| Signal Processor | Tool | Performs ECG cleaning and R-peak detection |

| Frequency HRV Analyzer | Tool | Computes LF, HF, and LF/HF ratio using NeuroKit2 |

| Time-Domain HRV Analyzer | Tool | Computes BPM, SDNN, and RMSSD from RR intervals |

| DecisionAgent | Agent | Classifies physiological state using rule-based thresholds |

| ActionAgent | Agent | Outputs human-readable recommendations based on state |



The two analysis pipelines operate on the same ECG data and together form a unified agent system.



\## Implementation



\### ECG Data Processing and Frequency-Domain Analysis



One module uses NeuroKit2 to perform ECG signal cleaning and R-peak detection based on the Pan-Tompkins algorithm. After detecting R-peaks, frequency-domain HRV metrics are computed, including LF power, HF power, and the LF/HF ratio. Power spectral density is calculated using Welch’s method, and visualization is generated with VHF components excluded to improve interpretability.



Key steps include:

\- ECG signal stitching and cleaning

\- Pan-Tompkins R-peak detection

\- Frequency-domain HRV computation

\- HRV spectrum visualization and reporting



\### Time-Domain HRV Analysis and Agent Decision Logic



The second module focuses on time-domain HRV analysis using RR intervals derived from detected R-peaks. Metrics such as BPM, SDNN, and RMSSD are calculated. These features are then passed to a rule-based agent system.



The DecisionAgent classifies physiological states using predefined thresholds:

\- High stress: elevated BPM with high RMSSD

\- Fatigue: low RMSSD

\- Normal: values within typical physiological ranges



The ActionAgent converts the detected state into a clear recommendation, such as resting, light activity, or maintaining current behavior.



\## Results



The system successfully processes ECG recordings and produces interpretable HRV metrics in both time and frequency domains. For each ECG segment, the system outputs:

\- BPM, SDNN, RMSSD

\- LF, HF, and LF/HF ratio

\- Classified physiological state

\- Text-based recommendation



Visual outputs include ECG waveforms with R-peaks marked and HRV frequency spectra. The results demonstrate that rule-based agents can effectively map physiological indicators to meaningful states without requiring complex models.



\## Discussion



\### Strengths

\- Clear and interpretable agent logic

\- Modular design allows independent testing of each component

\- Combines time-domain and frequency-domain HRV analysis



\### Limitations

\- Rule-based thresholds may not generalize across all individuals

\- No personalized baseline calibration

\- Offline analysis only; not real-time



\### Lessons Learned

This project highlights the importance of system architecture and interpretability in agent-based systems. Even simple decision rules can provide useful insights when combined with robust signal processing.



\## Conclusion



This project demonstrates a modular AI agent system for ECG-based HRV analysis and physiological state detection. By integrating frequency-domain analysis, time-domain metrics, and rule-based decision agents, the system provides a transparent and extensible framework for fatigue and stress assessment. Future work may include personalized thresholds, temporal modeling, and real-time deployment.



\## References



Pan, J., \& Tompkins, W. J. (1985). A real-time QRS detection algorithm. IEEE Transactions on Biomedical Engineering, 32(3), 230–236.



Task Force of the European Society of Cardiology and the North American Society of Pacing and Electrophysiology. (1996). Heart rate variability: standards of measurement, physiological interpretation and clinical use. Circulation, 93(5), 1043–1065.



NeuroKit2 Documentation: https://neurokit2.readthedocs.io/

