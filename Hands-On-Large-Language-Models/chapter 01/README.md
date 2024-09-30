
# Chapter 1 - Introduction to Language Models

## Description
This notebook introduces the Phi-3 language model and demonstrates how to use it for text generation using Hugging Face's `transformers` library. The notebook includes step-by-step instructions to load the model, create a text-generation pipeline, and generate text based on user input.

## Setup Instructions
To run the examples in this notebook efficiently, it is recommended to use a GPU, especially if running in a cloud environment like Google Colab.

1. In Colab:  
   Go to **Runtime > Change runtime type > Hardware accelerator > GPU > GPU type > T4**.

2. Install the necessary libraries:
   ```bash
   !pip install transformers>=4.40.1 accelerate>=0.27.2
   ```

## Usage

### Step 1: Load the Phi-3 Model
The model and tokenizer are loaded using the `AutoModelForCausalLM` and `AutoTokenizer` functions.

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model = AutoModelForCausalLM.from_pretrained("microsoft/Phi-3-mini-4k-instruct", device_map="cuda", torch_dtype="auto")
tokenizer = AutoTokenizer.from_pretrained("microsoft/Phi-3-mini-4k-instruct")
```

### Step 2: Create a Text-Generation Pipeline
The pipeline function simplifies the usage of the model for generating text.

```python
from transformers import pipeline

generator = pipeline(
    "text-generation",
    model=model,
    tokenizer=tokenizer,
    return_full_text=False,
    max_new_tokens=500,
    do_sample=False
)
```

### Step 3: Generate Text
You can now generate text by providing a prompt:

```python
messages = [{"role": "user", "content": "Create a funny joke about chickens."}]
output = generator(messages)
print(output[0]["generated_text"])
```

## Example Output
```
Why did the chicken join the band? Because it had the drumsticks!
```

## Libraries Used:
- `transformers`: Provides state-of-the-art pre-trained models for natural language processing tasks.
- `accelerate`: Optimizes model performance on GPUs.

## Requirements:
- Python 3.7+
- `transformers` >= 4.40.1
- `accelerate` >= 0.27.2
