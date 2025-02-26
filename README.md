# **Intelligent Test Automation**
A Multi-Agent LLM Framework for Dynamic Test Case Generation and Validation

## **Overview**
This repository contains the implementation of **Intelligent Test Automation**, a multi-agent framework that utilizes **Large Language Models (LLMs)** to automatically generate, validate, and execute test cases based on software requirements. The system is built using **AutoGen** and Python’s `unittest` module to streamline the testing process with minimal human intervention.

## **Features**
- **Automated Test Case Generation:** Extracts software requirements and generates structured test cases.
- **Multi-Agent Collaboration:** Uses distinct agents to handle test creation, validation, and execution.
- **Self-Adaptive Test Modification:** Automatically refines test cases and source code based on failures.
- **Seamless Integration with Python Testing Frameworks:** Works with `unittest` for structured test execution.

## **Installation**
Ensure you have Python **3.8 or higher** installed. Then, install the required dependencies:

```sh
pip install autogen
```

## **Configuration**
Before running the framework, configure the API settings:
1. Set the API key in an environment variable or a JSON file.
2. Ensure that **GPT-4** is the selected model.

Example JSON configuration:
```json
{
    "model": "gpt-4",
    "api_key": "your_api_key_here"
}
```

## **Usage**
### **Step 1: Run AutoGen Setup**
Configure AutoGen and set up the required agents:
```python
import autogen
config = autogen.config_list_from_json("OAI_CONFIG_LIST")
```

### **Step 2: Generate Test Cases**
Extract requirements from `REQ_SPE.pdf` and generate test cases:
```python
assistant = autogen.AssistantAgent(name="Software Tester")
user_proxy = autogen.UserProxyAgent(name="User", assistant=assistant)
user_proxy.chat("Extract test cases from REQ_SPE.pdf")
```

### **Step 3: Execute Tests**
Run generated test cases using Python’s `unittest` module:
```sh
python -m unittest discover -v
```

### **Step 4: Validate and Modify Tests**
If test cases fail, the system automatically refines them and re-executes:
```python
if test_failed:
    assistant.chat("Modify test cases and re-run")
```

## **Project Structure**
```
|-- src/
|   |-- test_case_generator.py
|   |-- test_validator.py
|   |-- test_executor.py
|
|-- data/
|   |-- REQ_SPE.pdf
|
|-- README.md
|-- requirements.txt
```

## **Contributing**
Contributions are welcome! Feel free to submit issues or pull requests.

## **License**
This project is open-source and licensed under the **MIT License**.

## **Contact**
For any inquiries, reach out via **pragatik992@gmail.com**.

