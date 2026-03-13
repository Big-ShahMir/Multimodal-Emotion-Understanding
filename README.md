# Evaluating Modality Contributions in Multimodal Emotion Understanding with Cross-Attention Mechanisms

## Research Overview
This project investigates multimodal emotion recognition using a Transformer-based architecture designed to fuse audio and visual data. The primary goal is to capture fine-grained human emotions by modeling both intra-modal temporal dependencies and inter-modal interactions. By focusing on nonverbal pathways (audio and video), the research evaluates the capacity of these modalities to predict emotional intensity while excluding textual input to avoid linguistic bias.

[Read the full research paper here](https://github.com/Big-ShahMir/Multimodal-Emotion-Understanding/blob/main/Final%20Report.pdf)

## Methodology & Architecture
The model utilizes a sophisticated fusion pipeline to process and align disparate data streams:

* **Feature Extraction:** The system uses 74-dimensional COVAREP features for audio and 35-dimensional FACET 4.2 features for video.
* **Transformer Encoders:** Each modality is processed through a dedicated Transformer encoder to capture modality-specific temporal dependencies through self-attention.
* **Cross-Attention Mechanisms:** These layers enable different modalities to attend to one another, ensuring contextual alignment and inter-modal interaction.
* **Temporal Aggregation:** Fused representations are pooled using an attention-based mechanism to emphasize emotionally salient moments before final prediction.

## Model Hyperparameters
 Specific configurations were identified through hyperparameter tuning to balance model capacity and computational efficiency:

*  **Audio-Visual Model:** Best performance achieved with a learning rate of $10^{-4}$, $d_{model}=64$, $n_{heads}=2$, and 2 Transformer layers per modality encoder.
*  **Audio-Visual-Text Model:** Best configuration used a learning rate of $10^{-4}$, $d_{model}=32$, $n_{heads}=2$, and a single Transformer layer per modality encoder.
*  **Text-Only Baseline:** Optimized with a learning rate of $3 \times 10^{-4}$, a batch size of 16, and a bidirectional LSTM with a hidden size of 64.

## Dataset & Processing
 The study utilizes the CMU-MOSEI dataset, focusing on a truncated subset to manage computational constraints:

*  **Standardization:** All utterances are truncated or zero-padded to 500 frames (approximately 5 seconds) to enable efficient batch processing.
*  **Class Balancing:** To mitigate the heavy bias toward "happiness" in the original dataset, a balanced subset was constructed by subsampling roughly 1,000 examples per emotion.
*  **Feature Synchronization:** Audio features were extracted at 100 Hz and video features at 30 fps, with both modalities temporally aligned to ensure frame-level correspondence.

## Key Results
 The experimental results demonstrate that the Transformer-based architecture is highly effective at reconstructing continuous emotional intensity:

| Metric | Result | Context |
| :--- | :--- | :--- |
| **Weighted Accuracy (WA)** | **93%** |  Substantially surpasses the published benchmark WA of 80.7%. |
| **Macro F1 Score** | **40%** |  Lower due to class imbalance, label sparsity, and the coarse nature of binary thresholding. |

 **Major Finding:** Multimodal integration—specifically the Audio-Visual-Text (A+V+T) model—achieves the highest weighted accuracy (0.9326), while the Audio-Visual (A+V) model offers greater flexibility for multilingual settings by avoiding language-specific embeddings.

## Authors
*  Shah Mir Ahmad (University of Toronto) 
*  Nguyen Vo Khoi Nguyen (University of Toronto) 
*  Zuhayr Ahmed (University of Toronto) 
*  Abuzar Ansari (University of Toronto)

## Disclaimer
Original repository is privatized, this repository holds the same contents as the original and all the code/text written in the course of this experiment. 
