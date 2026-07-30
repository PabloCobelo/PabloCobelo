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

🎓 **Multimodal Deep Learning for Multiple Sclerosis Detection (Degree Thesis)**

* **Note:** The code and dataset are confidential due to medical privacy regulations.
* **Objective:** Detect Multiple Sclerosis from non-invasive retinal imaging by fusing deep features across four OCT and OCTA modalities. The retina is a directly observable extension of the central nervous system: OCT captures the structural thinning caused by axonal damage, OCTA the microvascular changes that often precede it.
* **Role:** Lead developer & researcher for my Final Degree Project (TFG), on a clinical cohort of **52 patients / 103 eyes** (61 MS, 42 controls) from Hospital General Universitario Gregorio Marañón.
* **Approach:** Compared end-to-end fine-tuning against frozen feature extraction (**EfficientNet-B0**, **ResNet-50**, and the **RETFound** retinal foundation model), Extra Trees feature selection over a >400,000-component fused space, and early/intermediate/late fusion schemes — **64 experimental configurations** in total. Every one was evaluated with **stratified cross-validation grouped by patient**, so no patient's eyes could ever appear in both training and test: with a cohort this size, that grouping is the difference between a real result and an inflated one.
* **Results:** Late fusion of all four modalities with feature selection reached **F1 0.985, sensitivity 1.000, specificity 0.950**, against **F1 0.951** for the strongest single modality (fine-tuned macular OCT). Fusing the two OCTA projections with each other did *not* beat the best OCTA model alone — their errors are correlated — while crossing structural with vascular data did. That asymmetry is the actual evidence for neurovascular synergy, rather than the headline score.
* **What the negative result taught me:** RETFound, pre-trained on retinal images, behaved anomalously until I traced the cause to the quality of the extracted representations rather than to the classifier. A foundation model used outside its original data domain cannot be assumed valid without explicitly verifying its representations first — a check that belongs *before* deployment, not after an odd metric shows up.
* **Limitations:** with 103 eyes the test folds are small, so these scores carry real variance (up to ±0.10 on specificity) and need a larger cohort to confirm. The OCTA modalities in particular were unstable in isolation.
* **Technologies:** Python, PyTorch, Scikit-Learn, Transfer Learning (EfficientNet-B0, ResNet-50, RETFound), Medical Image Processing.
