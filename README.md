# resume-parser
A generic Resume Parser that can process two file formats: .pdf and .docx.

###  Problem Statement:
Given a resume, is there a way to automatically extract name, email, and list of skills?

Goal: Given a resume, the parser should be able to extract name, email, and skills into a structured JSON object.

### Data
Sample resumes used for testing were obtained from Kaggle public datasets. There are composed of both pdf and docx files.

### File Structure
Outline the directory and file structure of your project for easy navigation.

    resume-parser/
    ├── data/                  # Resume data
    ├── notebooks/             # Jupyter notebooks for parsing
    ├── reports/               # Final json outputs
    ├── requirements.txt       # Project dependencies
    └── README.md              # Read me file

### Installation & Usage

Clone the repository:

    git clone https://github.com/jraramirez/resume-parser.git
    cd resume-parser

Create a virtual environment:

    python -m venv venv
    source venv/bin/activate

Install dependencies:

    pip install -r requirements.txt

Setup Google project, enable Vertex AI API, and setup authentication. Follow this documentation: https://cloud.google.com/vertex-ai/docs/start/cloud-environment

Run the notebooks/scripts:
To use the resume parser, open

    notebooks/notebook-resume-parser.ipynb

in a Jupyter Notebook.

### Methodology

#### Research on AI Tools
First a research on AI tools that can be used to automatically extract information from documents was conducted. Google Cloud's Vertex AI came up as top choice for this task. There are several generative AI models available in Google Cloud but Gemini 2.5 Flash came up as the optimal for of text parsing.

#### Input Formats
In the Vertex AI library, a package for conveniently reading pdf is available. However, no package is readily available for .docx documents. The python package python-docx is used to handle these documents.

#### Generative AI Design
For the extraction to work, a prompt is designed and fed to the model using the generate_content function.

##### Prompt Used

    [
        "Extract the following details from this resume in JSON format:",
        "Name, Email, Skills",
        {document_contents}
    ]

The result of the content generation will be a JSON string that still needs to be parsed. String operations are used to generate the desired JSON object.


### Results & Findings
The solution was able to process both pdf and docx formats and was able to process 10 sample resumes. The resulting JSON objects include names, email addresses, and list of skills.

Conclusion: The Gemini 2.5 Flash model accurately identified the names, email addresses, and skills that can be found in a resume document. The extraction is also relatively fast for processing few sample resumes.


### Acknowledgements
Google Cloud CLI: https://cloud.google.com/sdk/docs/install
Google Cloud - Setup a Project: https://cloud.google.com/vertex-ai/docs/start/cloud-environment
Data Source 1: https://www.kaggle.com/datasets/palaksood97/resume-dataset/data
Data Source 2: https://www.kaggle.com/datasets/extremelysunnyyk/resume-data-with-annotations/data

### Author
Name: Joe Ramir Ramirez

Email: ramirezjoeramir@gmail.com