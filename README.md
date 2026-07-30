# Hi there 👋, I'm Pablo Cobelo

**Recent Artificial Intelligence Graduate | AI Engineer | Data Scientist**

Welcome to my GitHub profile! I recently graduated with a Bachelor's Degree in Artificial Intelligence from Universidade da Coruña, and I am passionate about solving real-world problems using machine learning and data-driven approaches.

### 👨‍💻 About Me
* 🎓 **Education:** BSc in Artificial Intelligence (2022 - 2026).
* 💼 **Experience:** Previously worked as an AI Intern at Plexus Tech, where I focused on data preprocessing, exploratory data analysis (EDA), and predictive modeling.
* 🌱 **Currently learning:** Deploying machine learning models / Computer Vision / NLP / Agentic systems.
* 🚀 **Looking for:** A full-time position as a Junior AI Engineer or Data Scientist.
* 📫 **Let's connect:** [pdcobelo@gmail.com](mailto:pdcobelo@gmail.com) | [LinkedIn](https://www.linkedin.com/in/pablo-cobelo-459b3226a)

### 🛠️ Technical Skills
* **Programming Languages:** Python, SQL
* **Libraries & Frameworks:** Pandas, NumPy, Scikit-Learn, PyTorch, Pydantic, LangGraph, Streamlit
* **Tools:** Git, GitHub Actions, Jupyter Notebook, Docker, Jenkins, SonarQube

### 📊 Featured Projects

🧾 **[Invoice Insights](https://github.com/PabloCobelo/invoice-insights)** — ▶ **[try the live demo](https://monolitoapp-8ymk5tkzw4bet2uvxq3ir5.streamlit.app/)**

* **What it is:** An end-to-end invoice processing app. Upload a PDF or a photo, a vision LLM extracts the fields, business rules validate them, a human reviews and corrects anything wrong, and the result lands in SQLite. A LangGraph agent then writes an executive spend report over the whole database.
* **Try it without an API key:** press **Load sample data** to explore 15 synthetic invoices, the spend and vendor charts, the anomaly detection, and a pre-generated agent report.
* **Design decisions worth a look:**
  * **Structured output instead of prompt parsing:** Gemini is called with a Pydantic model as its `response_schema`, so the response is valid JSON by construction and there is no fragile text parsing to maintain.
  * **An agent that cannot invent figures:** the report agent is a linear LangGraph `planner → tools → writer` costing exactly two LLM calls. Every number is computed by pandas; the writer only ever sees aggregate summaries and rendered tool output, never the raw rows. A test fails if raw data leaks into a prompt.
  * **Testable without spending API quota:** the LLM client is injected rather than constructed inside the nodes, so all 74 tests are deterministic and make zero API calls. CI runs the full suite on every push without needing a key.
  * **Documented limits:** the README states what the app does *not* handle — multi-page PDFs, mixed-currency totals, ephemeral storage on free hosting — instead of hiding it.
* **Technologies:** Python 3.12, Streamlit, Google Gemini, LangGraph, Pydantic v2, pandas, SQLite, pytest, GitHub Actions.

🚧 **Multimodal Deep Learning for Multiple Sclerosis Detection (Degree Thesis)**

* **Note:** The code and dataset are confidential due to medical privacy regulations.
* **Objective:** Developed an automated deep learning system to detect Multiple Sclerosis (MS) in its early stages using non-invasive retinal images (OCT and OCTA).
* **Role:** Lead developer & researcher for my Final Degree Project (TFG).
* **Key Achievements & Methodology:**
  * **Deep Feature Extraction:** Employed Transfer Learning using frozen pre-trained CNNs (like **EfficientNet-B0** and **ResNet-50**) to extract deep features from structurally and vascularly complex 3D image volumes.
  * **Multimodal Fusion:** Designed and evaluated "late" and "intermediate" feature fusion strategies to successfully combine structural (OCT) and microvascular (OCTA) data, capturing a more complete neurovascular signature of the disease.
  * **Feature Selection:** Implemented an Extra Trees algorithm to select the most relevant features and mitigate overfitting in high-dimensional fused spaces (over 400,000 components).
  * **Classification & Validation:** Evaluated combinations using classical classifiers (**SVM**, **Random Forest**, **Logistic Regression**). Implemented a rigorous **Stratified Group K-Fold cross-validation** technique, grouped by patient, to strictly prevent data leakage.
* **Results:** The best configuration (late fusion with feature selection) achieved an outstanding **F1-Score of 0.985** and a **specificity of 0.950**, demonstrating the immense potential of multimodal deep learning as a clinical biomarker for MS.
* **Technologies:** Python, PyTorch, Scikit-Learn, Transfer Learning (EfficientNet-B0, ResNet-50), Medical Image Processing.
