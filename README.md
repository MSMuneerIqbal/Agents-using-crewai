
### **Conclusion**
A well-structured README not only helps users understand your project but also enhances its visibility and usability. Make sure to keep it updated as your project evolves!

---

**Agentic AI Using CrewAI: Project Overview**

CrewAI is an innovative open-source Python framework designed to facilitate the development of collaborative, autonomous AI agents that work together to solve complex problems. Here’s a detailed breakdown of its features, components, and practical applications:

### **Key Features of CrewAI**
- **Multi-Agent System**: CrewAI allows the creation of multiple AI agents, each with specialized roles, to collaboratively tackle tasks.
- **Task Decomposition**: Complex problems can be broken down into manageable tasks, which are then assigned to different agents.
- **Manager Agent**: A central agent that oversees the workflow, monitors progress, and coordinates the interactions between agents.
- **Real-Time Adaptation**: Agents can dynamically adjust their strategies based on feedback and changing conditions.

### **Components of CrewAI**
1. **Agents**: Individual AI entities that specialize in specific tasks. Examples include:
   - **Code Reader**: Analyzes code.
   - **Code Reviewer**: Reviews and suggests improvements.
   - **Code Documentation Writer**: Generates documentation based on code analysis.
   - **CV Reader**: Processes CV data.
   - **Query Builder**: Constructs database queries.
   - **Query Executor**: Executes the constructed queries.

2. **Tasks**: Defined units of work that agents are responsible for completing.

3. **Crew**: A collection of agents working together to accomplish a set of tasks.

## Main Function Points

- **Multi-Agent System**: The project allows the creation of multiple AI agents, each with specialized roles, to collaboratively tackle tasks.
- **Task Decomposition**: Complex problems can be broken down into manageable tasks, which are then assigned to different agents.
- **Manager Agent**: A central agent that oversees the workflow, monitors progress, and coordinates the interactions between agents.
- **Real-Time Adaptation**: Agents can dynamically adjust their strategies based on feedback and changing conditions.

## Technology Stack

- **Python**
- **CrewAI framework**

### **How CrewAI Works**
- Agents communicate with each other to share insights and data.
- The Manager Agent coordinates these efforts, ensuring that each agent’s output feeds correctly into the next agent’s input.
- This collaborative approach allows the system to handle complex tasks efficiently.

### **Use Cases**
CrewAI has been applied in various projects, including:
- **Terraform Code Analysis**: A workflow involving a Code Reader, Code Reviewer, and Code Documentation Writer to automate code review and documentation generation.
- **CV Data Transformation**: A project that converts unstructured CV text into structured data for databases, utilizing agents specialized in reading CVs and executing queries.

# UV , litellm and CrewAi Setup
Welcome to the repository for GloProg (GloVersity) Class 08, held on -- / -- / ----. ion.  

## 📌 Table of Contents
1. [PowerShell Setup](#powershell-setup)  
2. [UV Basics](#uv-basics)  
3. [Creating and Managing Projects](#creating-and-managing-projects)  
4. [Adding Dependencies](#adding-dependencies)  
5. [Working with LiteLLM](#working-with-litellm)  
6. [Understanding Python Decorators](#understanding-python-decorators)  
7. [CrewAI Installation & Setup](#crewai-installation--setup)  
8. [Running CrewAI Workflow](#running-crewai-workflow)  

---

## ⚡ PowerShell Setup  
To begin, run the following command to install UV:  
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
Check if UV is installed correctly:  
```sh
uv version
uv help
```

---

## 🎯 UV Basics
Initialize a new project:  
```sh
uv init my-project
code .
```
Open the terminal and navigate into the project folder:  
```sh
cd .\my-project\
uv run hello.py
```
Modify `hello.py`, rerun the script, and observe changes:  
```sh
uv run hello.py
```

---

## 📦 Adding Dependencies  
Install additional packages:  
```sh
uv add numpy pandas
```
Verify the dependencies in the `pyproject.toml` file.  

---

## 🚀 Creating and Managing Projects  
Create another project:  
```sh
uv init --package another-project
```
Return to VS Code and check the `pyproject.toml` file.  
Navigate to `src/` and create `hello.py`:
```python
def my_function():
    print("Hello from my_function()")
```
Now, add a new command in `pyproject.toml`:  
```toml
gloprog = "another_project.hello:my_function"
```
Run the command from the terminal:  
```sh
uv run gloprog
```
Install the package in editable mode:  
```sh
pip install -e .
```

---

## 🔥 Working with LiteLLM  
Initialize a new project:  
```sh
uv init --package litellm-project
cd litellm-project
```
Add the LiteLLM dependency:  
```sh
uv add litellm
uv venv
```
Activate the virtual environment:  
```sh
.venv\Scripts\activate   # Windows
source .venv/bin/activate   # macOS/Linux
```
Now make hello.py in SRC folder. 

```python
from litellm import completion
import os

os.environ["OPENAI_API_KEY"] = "ADD YOUR API KEY"
os.environ["GEMINI_API_KEY"] = "ADD YOUR API KEY"

def openai():
    response = completion(
        model="openai/gpt-4o",
        messages=[{"content": "Hello, how are you?", "role": "user"}]
    )
    print(response)

def gemini():
    response = completion(
        model="gemini/gemini-1.5-flash",
        messages=[{"content": "Hello, how are you?", "role": "user"}]
    )
    print(response)

def gemini2():
    response = completion(
        model="gemini/gemini-2.0-flash-exp",
        messages=[{"content": "Hello, how are you?", "role": "user"}]
    )
    print(response)
```
Add your API key and run:  
```sh
uv run gemini
```

---

## 🧠 Understanding Python Decorators  
**Python decorators** are functions that modify the behavior of another function without changing its structure.  
Example:  
```python
def my_decorator(func):
    def wrapper():
        print("Before the function is called.")
        func()
        print("After the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello, world!")

say_hello()
```
Try running this in **Google Colab** to experiment with decorators.

---

## 🤖 CrewAI Installation & Setup  
To install CrewAI, follow these steps:

### Step 1: Install Microsoft C++ Build Tools  
Download from [Visual Studio Official Site](https://visualstudio.microsoft.com/visual-cpp-build-tools/).  

### Step 2: During Installation, Select:  
✅ MSVC v142 or later  
✅ Windows 10 SDK  
✅ C++ CMake tools for Windows  

Restart your system after installation.

### Step 3: Upgrade Pip & Install CrewAI  
```sh
pip install --upgrade pip setuptools wheel
pip install crewai
```
If using a virtual environment:  
```sh
.venv\Scripts\activate   # Windows
source .venv/bin/activate   # macOS/Linux
```
If installation issues occur:  
```sh
pip install hnswlib
pip install crewai
```
Verify installation:  
```sh
crewai version
```

---

## ⚙️ Running CrewAI Workflow  
Create a new CrewAI workflow:  
```sh
crewai create flow crew_flow
dir
```
Open the project in **VS Code** and edit `.env`:  
```env
OPENAI_API_KEY= (Replace with GEMINI_API_KEY)
MODEL=gemini/gemini-1.5-flash
```
Run the CrewAI script:  
```sh
uv run kickoff
```

---

## 🎯 Conclusion  
This revision guide covered:
- Setting up **UV**, **LiteLLM**, and **CrewAI**  
- Running Python scripts and managing dependencies  
- Understanding **Python decorators**  
- Configuring API keys and virtual environments  

🚀 **Keep practicing, and happy coding!** 🚀

---
