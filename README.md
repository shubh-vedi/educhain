
<p align="center">
  <img src="https://github.com/VedantDeshmukh2/educhain/blob/main/images/educhain.svg" alt="Educhain Logo" width="800" height="400">
</p>

<div align="center">
  
  [![PyPI version](https://badge.fury.io/py/educhain.svg)](https://badge.fury.io/py/educhain)
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
  [![Python Versions](https://img.shields.io/pypi/pyversions/educhain.svg)](https://pypi.org/project/educhain/)
  [![Downloads](https://pepy.tech/badge/educhain)](https://pepy.tech/project/educhain)

</div>

# Educhain 🎓🔗
[Website](https://educhain.in) | [Documentation](docs/index.md)

Educhain is a powerful Python package that leverages Generative AI to create engaging and personalized educational content. From generating multiple-choice questions to crafting comprehensive lesson plans, Educhain makes it easy to apply AI in various educational scenarios.

<img src="images/logo.svg" alt="Educhain Logo" align="center" height="120" width="120" />

## 🚀 Features

- 📝 Generate Multiple Choice Questions (MCQs)
- 📊 Create Lesson Plans
- 🔄 Support for various LLM models
- 📁 Export questions to JSON, PDF, and CSV formats
- 🎨 Customizable prompt templates
- 📚 Generate questions from text/PDF/URL files
- 📹 Generate questions from YouTube videos
- 🥽 Generate questions from images

## 📈 Workflow

**Reimagining Education with AI** 🤖
- 📜 QnA Engine: Generates an infinte variety of Questions
- 📰 Content Engine: One-stop content generation - lesson plans, flashcards, notes etc
- 📌 Personalization Engine: Adapts to your individual level of understanding for a tailored experience.

<img src="images/educhain_diagram.png" alt="Educhain workflow diagram" />

## 🛠 Installation

```bash
pip install educhain
```

## 🎮 Usage

## Starter Guide

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1JNjQz20SRnyRyAN9YtgCzYq4gj8iBTRH?usp=chrome_ntp#scrollTo=UtLn9rOF-gPm)

### Quick Start

Get started with content generation in < 3 lines! 

```python
from educhain import Educhain

client = Educhain()

ques = client.qna_engine.generate_questions(topic="Newton's Law of Motion",
                                            num=5)
print(ques)
ques.json() # ques.dict()
```

### Supports Different Question Types

Generates different types of questions. See the advanced guide to create a custom question type. 


```python
# Supports "Multiple Choice" (default); "True/False"; "Fill in the Blank"; "Short Answer"

from educhain import Educhain

client = Educhain()

ques = client.qna_engine.generate_questions(topic = "Psychology", 
                                            num = 10,
                                            question_type="Fill in the Blank"
                                            custom_instructions = "Only basic questions")

print(ques)
ques.json() #ques.dict()
```

### Use Different LLM Models

To use a custom model, you can pass a model configuration through the `LLMConfig` class

Here's an example using the Gemini Model

```python
from langchain_google_genai import ChatGoogleGenerativeAI
from educhain import Educhain, LLMConfig

gemini_flash = ChatGoogleGenerativeAI(
    model="gemini-1.5-flash-exp-0827",
    google_api_key="GOOGLE_API_KEY")

flash_config = LLMConfig(custom_model=gemini_flash)

client = Educhain(flash_config) #using gemini model with educhain

ques = client.qna_engine.generate_questions(topic="Psychology",
                                            num=10)

print(ques)
ques.json() #ques.dict()
```

### Customizable Prompt Templates 

Configure your prompt templates for more control over input parameters and output quality. 

```python
from educhain import Educhain

client = Educhain()

custom_template = """
Generate {num} multiple-choice question (MCQ) based on the given topic and level.
Provide the question, four answer options, and the correct answer.
Topic: {topic}
Learning Objective: {learning_objective}
Difficulty Level: {difficulty_level}
"""

ques = client.qna_engine.generate_questions(
    topic="Python Programming",
    num=2,
    learning_objective="Usage of Python classes",
    difficulty_level="Hard",
    prompt_template=custom_template,
)

print(ques)
```


### Generate Questions from Data Sources

Ingest your own data to create content. Currently supports URL/PDF/TXT.

```python
from educhain import Educhain
client = Educhain()

ques = client.qna_engine.generate_questions_from_data(
    source="https://en.wikipedia.org/wiki/Big_Mac_Index",
    source_type="url",
    num=5)

print(ques)
ques.json() # ques.dict()
```


### Generate Lesson Plans

Create interactive and detailed lesson plans. 

```python
from educhain import Educhain

client = Educhain()

plan = client.content_engine.generate_lesson_plan(
                              topic = "Newton's Law of Motion")

print(plan)
plan.json()  # plan.dict()
```


## 📊 Supported Question Types

- Multiple Choice Questions (MCQ)
- Short Answer Questions
- True/False Questions
- Fill in the Blank Questions

## 🔧 Advanced Configuration

Educhain offers advanced configuration options to fine-tune its behavior. Check our [advanced guide]() for more details. (coming soon!)

## 🌟 Success Stories

Educators worldwide are using Educhain to transform their teaching. Read our [case studies](https://educhain.ai/case-studies) to learn more.

## 📈 Usage Statistics

Educhain's adoption has been growing rapidly:

<img src="/api/placeholder/600/400" alt="Usage Growth Graph" />

## 🗺 Roadmap

- [x] Bulk Generation
- [x] Outputs in JSON format
- [x] Custom Prompt Templates
- [x] Custom Response Models using Pydantic
- [x] Exports questions to JSON/PDF/CSV
- [x] Support for other LLM models
- [x] Generate questions from text/PDF file
- [ ] Integration with popular Learning Management Systems
- [ ] Mobile app for on-the-go content generation

## 🤝 Open Source Contributions Welcome!

We invite you to help enhance our library. If you have **any ideas, improvements, or suggestions for enhancements** to contribute, please open a [GitHub issue](https://github.com/satvik314/educhain/issues) or submit a pull request. Be sure to adhere to our existing project structure and include a detailed README.md for any new Contribution.

Thank you for your continued support, community!

[![Star History Chart](https://api.star-history.com/svg?repos=satvik314/educhain&type=Date)](https://star-history.com/#satvik314/educhain&Date)


## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📬 Contact

- For general inquiries: [educhain.in](https://educhain.in)
- For technical support: [satvik@buildfastwithai.com](mailto:satvik@buildfastwithai.com)
- Follow us on [Twitter](https://x.com/EduchainWithAI)

---

<img src="images/logo.svg" alt="Educhain Logo" align="right" height="80" width="80" />

Made with ❤️ by Buildfastwithai

[www.educhain.in](https://educhain.in)
```

You can now copy and paste this directly into your project!
