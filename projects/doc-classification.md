# Document Classification | Gallery Search - Galaxy S25

## Overview
On-device document classification system for gallery search, supporting categories like passport, credit card, notes, etc.

## My Role
- Worked on C++ inference pipeline and Android integration
- Owned OCR + tokenizer integration

## System Overview
- Input: Image from gallery
- Preprocessing: Resize, normalization
- Model: Vision-Language Model (VLM)
- Additional Signal: OCR text
- Output: Document category

## Key Challenges

### 1. Cross-platform accuracy mismatch
- Issue: On-device accuracy lower than Python baseline
- Root cause: PIL vs OpenCV interpolation mismatch

### 2. Tokenization in C++
- Python used HuggingFace AutoTokenizer
- No equivalent in C++ pipeline

### 3. OCR integration
- Needed coordination with separate OCR team
- No existing API contracts

## Solutions

### Custom Resize Implementation
- Studied PIL and OpenCV internals
- Implemented custom resize function
- Ensured consistency with training pipeline

### Tokenizer Integration
- Used SentencePiece
- Extended APIs and compiled as `.so`
- Integrated into inference pipeline

### OCR Pipeline Integration
- Defined API contracts with OCR team
- Designed multimodal input pipeline

## Impact
- +4% classification accuracy
- ~10% latency reduction
- ~5% memory optimization

## Learnings
- Small preprocessing mismatches can significantly impact ML performance
- Deployment constraints require adapting research pipelines