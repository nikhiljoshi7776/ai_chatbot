# GPU-powered Chatbot with llama-cpp-python #

This Jupyter Notebook empowers you to create a chatbot application that leverages the [```llama-cpp-python```](https://pypi.org/project/llama-cpp-python/) library for efficient large language model (LLM) inference on a GPU.

## Prerequisites ##

Python Environment: Ensure you have a compatible Python 3.x environment set up.
Package Management: The ```pip``` package manager is essential for installing dependencies.
GPU Hardware: Access to a GPU with sufficient Video RAM (VRAM) is recommended for optimal performance, especially with larger models.

### Libraries: ###

```
llama-cpp-python (version 0.1.78 recommended)
numpy (version 1.23.4 recommended)
huggingface_hub (for model download)
```

## Installation ##

### Install Required Libraries: ###

```
Bash
pip install llama-cpp-python==0.1.78 numpy==1.23.4 huggingface_hub
```

Enable GPU Acceleration (if applicable):

For CUDA-enabled GPUs, set the ```CMAKE_ARGS``` environment variable before installation:

```
Bash
export CMAKE_ARGS="-DLLAMA_CUBLAS=on"
```

Consult the [```llama-cpp-python```](https://github.com/abetlen/llama-cpp-python) documentation for specific instructions on enabling GPU support based on your hardware configuration.

## Functionality ##

### 1. Model Download: ###

The notebook employs the ```huggingface_hub``` library to seamlessly download a pre-trained LLM model from the Hugging Face Hub. The example utilizes ```"TheBloke/Llama-2-13B-chat-GGML"```, but you can explore other models to suit your needs.

### 2. LLM Initialization: ###

The ```Llama``` class from ```llama-cpp``` is instantiated to create an instance of the LLM model. Here's a breakdown of key configuration parameters:

* ```model_path```: Path to the downloaded model file.

* ```n_threads```: Number of CPU threads to employ.

* ```n_batch```: Batch size for inference (experiment to find the optimal value considering VRAM constraints).

* ```n_gpu_layers```: Number of GPU layers to leverage for inference (experiment for best performance).

### 3. Chatbot Interaction: ###

The ```create_chatbot_response``` function serves as the heart of the chatbot's logic. It takes the following steps:

* Prompt Processing: User input is received as a prompt and formatted with a predefined template.

* LLM Inference: The formatted prompt is fed to the LLM for response generation.

* Response Extraction: The generated text is extracted from the LLM's output.

### 4. Jupyter Notebook Loop: ###

A while loop facilitates continuous interaction with the user. It iterates through the following steps:

* User Input Prompt: The user is prompted to enter a question or request.

* Chatbot Response: The ```create_chatbot_response``` function generates a response based on the user's input.

* Response Display: The chatbot's response is printed to the console.

* Exit Condition: The loop continues until the user enters ```"quit"``` to terminate the chatbot.

## Customization ##

* Model Exploration: Experiment with various LLM models available on the Hugging Face Hub to discover the best fit for your chatbot's purpose.

* Performance Tuning: Adjust the ```n_batch``` and ```n_gpu_layers``` parameters based on your GPU's capabilities and the model's requirements. Strike a balance between efficient inference and resource utilization.

* Tailored Interactions: Modify the ```prompt_template``` and response processing logic within ```create_chatbot_response``` to fine-tune the chatbot's behavior and interactions. This allows you to personalize the conversation flow and cater to specific use cases.
