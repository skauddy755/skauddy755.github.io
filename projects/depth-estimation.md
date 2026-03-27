# Depth Estimation | Portrait Mode - Galaxy S24

## Overview
On-device monocular depth estimation system used for portrait mode (bokeh effect) in smartphone camera. The goal was to generate accurate depth maps from a single RGB image, enhanced with dual-pixel (DP) sensor data.

## My Role
- Contributed to model development and experimentation
- Worked on improving robustness and perceptual quality of depth maps
- Collaborated on integrating model into on-device pipeline

## System Overview
- Input:
  - RGB image
  - Dual-pixel (DP) data for additional depth cues
- Model:
  - CNN-based architecture (EfficientNet / MobileNetV2 variants)
  - Multi-branch design with a specialized branch for human subjects
- Output:
  - Dense depth map for background blur (bokeh rendering)

## Key Challenges

### 1. Low-light performance degradation
- Issue: Significant drop in depth quality under low-light conditions
- Causes:
  - Sensor noise (low SNR)
  - Reduced reliability of dual-pixel signals

### 2. Loss of fine-grained details
- Issue: Poor reconstruction of edges and thin structures (e.g., hair, object boundaries)
- Cause:
  - CNNs tend to oversmooth high-frequency details

### 3. Domain-specific requirements (human subjects)
- Issue: Portrait mode primarily focuses on humans, requiring higher accuracy on faces and body contours

## Solutions

### Improving Low-Light Robustness
- Increased representation of low-light data in training set
- Applied illumination-based augmentations:
  - brightness and contrast variations
  - gamma transformations
- Improved model robustness to noise and varying lighting conditions

### Preserving Fine Details
- Leveraged multi-scale feature learning to retain both:
  - low-level spatial details
  - high-level semantic understanding
- Improved edge quality and reduced over-smoothing in depth maps

### Human-Specific Branch
- Introduced a specialized branch in the network to focus on human regions
- Helped capture human-specific depth priors (face structure, body contours)
- Improved perceptual quality of portrait-mode outputs

## Impact
- Improved depth estimation quality in challenging scenarios (low-light, fine edges)
- Enhanced perceptual quality of bokeh effect, especially for human subjects

## Learnings
- Depth estimation is highly sensitive to input quality and lighting conditions
- Data distribution and augmentation play a critical role in model robustness
- Incorporating domain-specific priors (e.g., humans) can significantly improve real-world performance