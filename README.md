<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  
</head>
<body>

  <h1>📄 Resume Information Extraction using NLP (Named Entity Recognition)</h1>

  <p>This project implements an NLP-based pipeline to automatically extract structured information such as <strong>Name, Skills, Degree, Institutions</strong>, and <strong>Work Experience</strong> from raw resumes in <code>.txt</code> or <code>.pdf</code> format using <strong>SpaCy's Named Entity Recognition (NER)</strong>.</p>

  <h2>🚀 Features</h2>
  <ul>
    <li>Preprocesses a JSON dataset of annotated resumes</li>
    <li>Converts annotations to SpaCy training format</li>
    <li>Trains a custom NER model from scratch using <code>spacy.blank()</code></li>
    <li>Handles overlapping and misaligned entity spans</li>
    <li>Supports testing with custom <code>.txt</code> or <code>.pdf</code> resumes</li>
    <li>Regex-based extraction of Email, Phone, and LinkedIn profiles</li>
  </ul>

  <h2>🧠 Extracted Entities</h2>
  <ul>
    <li><strong>Name</strong></li>
    <li><strong>Skills</strong></li>
    <li><strong>Degree</strong></li>
    <li><strong>College Name</strong></li>
    <li><strong>Graduation Year</strong></li>
    <li><strong>Email</strong></li>
    <li><strong>Phone number</strong></li>
    <li><strong>LinkedIn</strong></li>
  </ul>

  <h2>📂 Files</h2>
  <ul>
    <li><code>NER.ipynb</code> – Main notebook for loading data, training the model, and testing on new resumes</li>
    <li><code>Entity Recognition in Resumes.json</code> – Annotated resume dataset</li>
    <li>Utilities to test with <code>.pdf</code> and <code>.txt</code> resume inputs</li>
  </ul>

  <h2>🛠️ Dependencies</h2>
  <pre><code>
spacy==3.x
pdfplumber
PyMuPDF (fitz)
re
random
</code></pre>

  <h2>📌 How to Run</h2>
  <ol>
    <li>Upload the annotated JSON dataset</li>
    <li>Run the notebook <code>NER.ipynb</code> cell by cell</li>
    <li>Train the custom NER model</li>
    <li>Test the model using your own <code>.txt</code> or <code>.pdf</code> resumes</li>
  </ol>

  <h3>📥 Example: Testing a TXT Resume</h3>
  <pre><code>with open("your_resume.txt", "r", encoding="utf-8") as f:
    resume_text = f.read()

doc = nlp(resume_text)
for ent in doc.ents:
    print(f"{ent.label_:<25} ➤ {ent.text}")
</code></pre>

  <h3>📥 Example: Testing a PDF Resume</h3>
  <pre><code>import pdfplumber

with pdfplumber.open("your_resume.pdf") as pdf:
    resume_text = " ".join(page.extract_text() for page in pdf.pages)

doc = nlp(resume_text)
for ent in doc.ents:
    print(f"{ent.label_:<25} ➤ {ent.text}")
</code></pre>

  <h3>🔍 Regex Post-processing</h3>
  <pre><code>import re

email_match = re.search(r'[\w\.-]+@[\w\.-]+', resume_text)
phone_match = re.search(r'\+91[-\s]?[0-9]{10}', resume_text)
linkedin_match = re.search(r'linkedin\.com\/[^\s]+', resume_text)

if email_match:
    print(f"Email ➤ {email_match.group()}")
if phone_match:
    print(f"Phone ➤ {phone_match.group()}")
if linkedin_match:
    print(f"LinkedIn ➤ {linkedin_match.group()}")
</code></pre>

  <h2>📊 Sample Output</h2>
  <pre><code>
Name                     ➤ Rahul Verma
Email                    ➤ rahul.verma@gmail.com
Phone                    ➤ +91-9876543210
LinkedIn                 ➤ linkedin.com/in/rahul-verma
Degree                   ➤ M.Tech in Data Science
College Name             ➤ Indian Institute of Technology
Skills                   ➤ Machine Learning, Python, SQL
  </code></pre>

  <h2>📸 Visual Output</h2>

  <h3>1. Extracted Entities from Plain Text Resume</h3>
  <img width="542" height="170" alt="Plain Text Resume output" src="https://github.com/user-attachments/assets/425bd061-9e86-40c6-8e98-40cc37c68493" />

  <h3>2. Extracted Entities from PDF Resume</h3>
  <img width="370" height="153" alt="PDF Resume output" src="https://github.com/user-attachments/assets/c7e23d45-257b-483c-98dc-a654c368e7fe" />

  <h2>📌 Notes</h2>
  <ul>
    <li>Misaligned or overlapping entity spans are automatically skipped.</li>
    <li>Ensure entity annotations are clean and whitespace-free.</li>
    <li>Training accuracy depends heavily on dataset quality and coverage.</li>
  </ul>

  <h2>💡 Future Work</h2>
  <ul>
    <li>Improve span alignment and annotation quality</li>
    <li>Fine-tune using pre-trained SpaCy pipelines</li>
    <li>Integrate with Streamlit for resume upload and instant extraction</li>
  </ul>

  <h2>✅ Conclusion</h2>
  <p>
    This project successfully demonstrates how Natural Language Processing (NLP) can be applied to extract structured information from unstructured resumes. 
    By training a custom SpaCy NER model, the system can identify important entities such as Name, Degree, Institution, Skills, and Work Experience.
    Additional regex logic helps capture key contact information like Email and LinkedIn with high accuracy.
  </p>

</body>
</html>
