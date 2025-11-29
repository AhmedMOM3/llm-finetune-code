# LLM Fine-tuning for Code Generation

A comprehensive project for fine-tuning Large Language Models (LLMs) to generate Python code from natural language descriptions. This project uses LoRA (Low-Rank Adaptation) for efficient fine-tuning of the Qwen2.5-3B-Instruct model on the CoNaLa dataset.

## 🎯 Project Overview

This project fine-tunes an LLM to:

1. **Enhance Intent**: Rewrite vague programming requests into detailed, technical specifications
2. **Generate Code**: Produce clean, executable Python code from enhanced specifications

The model learns to transform ambiguous requests like "combine numbers in a list" into precise specifications and corresponding Python code.

## 🤗 LoRA Adaptor

**Hugging Face Model**: [abdelalem33/coder](https://huggingface.co/abdelalem33/coder)

## 📊 Dataset

The project uses the [CoNaLa (Code/Natural Language Challenge)](http://www.phontron.com/download/conala-corpus-v1.1.zip) dataset, which contains:

- **Training samples**: 2,379 intent-code pairs
- **Split**: 4,000 training samples (including augmented data), 758 validation samples

Each sample includes:

- Original intent (natural language description)
- Rewritten intent (enhanced technical specification)
- Python code snippet

## 🏗️ Architecture

### Base Model

- **Model**: Qwen2.5-3B-Instruct
- **Parameters**: 3.2B total, 119.7M trainable (3.74%)
- **Fine-tuning Method**: LoRA (Low-Rank Adaptation)
  - Rank: 64
  - Target modules: All linear layers (gate_proj, o_proj, k_proj, q_proj, up_proj, v_proj, down_proj)

## 📈 Results

### Training Metrics

- **Final Training Loss**: 0.8757
- **Final Validation Loss**: 0.8581
- **Training Speed**: 0.671 samples/second
- **Total Training Time**: 3 hours 18 minutes

### Model Performance

The model successfully learns to:

- Transform vague intents into precise specifications
- Generate syntactically correct Python code
- Use appropriate variable names and data structures
- Implement clean, Pythonic solutions

## 🎓 Key Features

### Dual-Task Training

The model is trained on two complementary tasks:

1. **Intent Enhancement**:
  - Input: Vague natural language description
  - Output: Detailed technical specification with explicit variable names, data types, and operations
2. **Code Generation**:
  - Input: Enhanced technical specification
  - Output: Executable Python code

### System Prompts

Custom system prompts guide the model's behavior:

- **Intent Enhancement Prompt**: Emphasizes providing complete information (variable names, data structures, types, operations)
- **Code Generation Prompt**: Focuses on producing clean, efficient, executable code

## 🛠️ Technical Details

### Data Preprocessing

- Structured output format using Pydantic schemas
- JSON formatting for consistent responses
- Careful handling of special tokens and chat templates

## 📊 Experiment Tracking

Training metrics are logged to Weights & Biases:

- Loss curves
- Learning rate schedule
- GPU utilization
- Training speed

## 🙏 Acknowledgments

- [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory) for the fine-tuning framework
- [Qwen Team](https://github.com/QwenLM/Qwen) for the base model
- [CoNaLa Dataset](https://conala-corpus.github.io/) creators
- Hugging Face for transformers and PEFT libraries
