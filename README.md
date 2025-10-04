# SYPHU-CHINA iGEM Inclusive Clinical Research Platform

**Version 1.0.0**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Framework: Streamlit](https://img.shields.io/badge/Framework-Streamlit-ff69b4.svg)](https://streamlit.io/)
[![Code Style: Black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

---

## Abstract

The **SYPHU-CHINA iGEM Inclusive Clinical Research Platform** is a web-based, interactive data collection and analysis platform designed for the 2025 International Genetically Engineered Machine (iGEM) competition. The core objective of this platform is to support a clinical study on patients with Hepatocellular Carcinoma (HCC), while deeply integrating the principles of **Diversity, Equity, and Inclusion (DEI)** into its design and functionality. Through a multi-step, multilingual online questionnaire, the platform collects data on participants' demographics, medical history, symptom assessment, and willingness to participate in future research. Furthermore, it incorporates a real-time data dashboard for dynamic visualization of research progress and provides a research transparency module to ensure the project adheres to the highest standards of scientific ethics.

This project is not merely a data collection tool but an exploration of implementing inclusive design in life sciences research. It aims to lower the barriers to entry for participants from diverse backgrounds (cultural, linguistic, physical ability, etc.), thereby obtaining more representative datasets and driving innovation in the global health sector.

## Table of Contents

1.  [Project Background and Objectives](#1-project-background-and-objectives)
2.  [Key Features](#2-key-features)
3.  [Technology Stack](#3-technology-stack)
4.  [System Architecture & Code Structure](#4-system-architecture--code-structure)
5.  [Installation and Deployment Guide](#5-installation-and-deployment-guide)
    *   [Prerequisites](#prerequisites)
    *   [Installation Steps](#installation-steps)
    *   [Running Locally](#running-locally)
6.  [Usage Guide](#6-usage-guide)
    *   [Questionnaire Workflow](#questionnaire-workflow)
    *   [Live Dashboard](#live-dashboard)
    *   [Research Transparency Module](#research-transparency-module)
7.  [Inclusive Design Philosophy](#7-inclusive-design-philosophy)
8.  [Data Management and Ethical Compliance](#8-data-management-and-ethical-compliance)
9.  [Contribution Guidelines](#9-contribution-guidelines)
10. [License](#10-license)
11. [Citation](#11-citation)
12. [Contact](#12-contact)

---

### 1. Project Background and Objectives

The iGEM competition encourages teams to solve real-world problems. Hepatocellular Carcinoma is a major global health challenge, yet related clinical research data often suffers from geographical and demographic limitations, lacking coverage of ethnic minorities, low-income groups, or individuals with special needs. This data bias can lead to insufficient generalizability of research findings and treatment protocols.

The **SYPHU-CHINA iGEM team** aims to address this pain point through this platform.

**Primary Objectives:**

*   **Efficient Data Collection**: To develop a user-friendly, streamlined questionnaire system for collecting high-quality clinical research data in a standardized manner.
*   **Promoting Inclusivity**: To attract and serve a more diverse participant population through multilingual support, accessibility considerations, and diverse demographic options.
*   **Enhancing Data Transparency**: To increase project credibility by displaying anonymized, aggregated research progress to the public and participants via a real-time dashboard.
*   **Ensuring Ethical Compliance**: To strictly adhere to the principle of informed consent, protect data privacy and security, and comply with scientific ethical standards.
*   **Supporting the iGEM Project**: To provide real-world data support for the team's synthetic biology research project, validating the model's effectiveness and societal value.

### 2. Key Features

*   **Multilingual Interface**: Seamlessly supports switching between Chinese (zh) and English (en), with good scalability to support more languages.
*   **Step-by-Step Questionnaire**: Decomposes a complex questionnaire into six steps: Informed Consent, Basic Information, Medical History, Symptom Assessment, Research Participation, and Completion, reducing the user's cognitive load.
*   **Dynamic Interactive Forms**: Forms contain conditional logic that dynamically shows or hides relevant questions based on user responses, improving completion efficiency.
*   **Rich UI/UX Design**: Employs a modern UI design, including gradients, animations, and custom CSS styles, to provide an excellent user experience.
*   **Accessibility Needs Collection**: A specially designed module to collect participants' accessibility support needs (e.g., visual, auditory assistance) and preferred communication methods.
*   **Real-time Data Dashboard**: Integrates Plotly for interactive data visualization, displaying key metrics such as participant geographical distribution, tumor stage, and participation trends.
*   **Research Transparency**: A dedicated page displays the data usage promise, ethical approval information (simulated), and data export options.
*   **State Management**: Effectively utilizes Streamlit's `session_state` to manage user sessions, ensuring data consistency throughout the multi-step process.

### 3. Technology Stack

*   **Core Framework**: [Streamlit](https://streamlit.io/) - A Python library for rapidly building interactive data applications.
*   **Data Processing & Analysis**: [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/) - For structured data handling and numerical computation.
*   **Data Visualization**: [Plotly Express](https://plotly.com/python/plotly-express/) & [Plotly Graph Objects](https://plotly.com/python/graph-objects/) - For creating rich, interactive charts.
*   **Frontend Styling**: HTML/CSS - Injected via Streamlit's `st.markdown` and `st.components.v1.html` for custom interface styling and layout.
*   **Development Environment**: Python 3.8+

### 4. System Architecture & Code Structure

This application adopts a single-file script (`SYPHU-CHINA iGEM - Inclusive Clinical Research.py`) architecture, suitable for rapid prototyping of Streamlit projects. Its internal logical structure is as follows:

1.  **Initialization & Configuration (`st.set_page_config`, `st.session_state`)**:
    *   Sets page metadata.
    *   Initializes session state variables, such as `language`, `current_step`, `form_data`, etc.

2.  **Multilingual Text Definition (`TEXTS` dictionary)**:
    *   A large nested dictionary that stores bilingual text for all UI elements, forming the core of the internationalization implementation.

3.  **Global UI & Styling**:
    *   Injects custom CSS to define the application's visual style.
    *   Builds global components like the Header, language switcher, and Footer.

4.  **Main Application Logic (Tabs)**:
    *   `tab 1: Questionnaire Area`:
        *   Conditionally renders the corresponding questionnaire step based on the value of `st.session_state.current_step`.
        *   Each step is an independent `st.form`, ensuring that data is captured as a whole when "Next" is clicked.
        *   Navigation buttons (Previous/Next) control the flow by modifying the value of `current_step`.
    *   `tab 2: Live Dashboard`:
        *   Uses simulated data (`st.session_state.participants_data`) to generate statistical metrics and Plotly charts.
    *   `tab 3: Research Transparency`:
        *   Displays static information and a simulated data export function.

### 5. Installation and Deployment Guide

#### Prerequisites

*   Python 3.8 or higher.
*   `pip` Python package manager.
*   Git (recommended, for cloning the project).

#### Installation Steps

1.  **Clone the repository**:
    ```bash
    git clone [Your Repository URL]
    cd [Project Directory]
    ```

2.  **Create and activate a virtual environment (recommended)**:
    ```bash
    # Windows
    python -m venv venv
    venv\Scripts\activate

    # macOS / Linux
    python 3 -m venv venv
    source venv/bin/activate
    ```

3.  **Install dependencies**:
    All project dependencies are listed in the `requirements. txt` file. Run the following command to install them:
    ```bash
    pip install -r requirements.txt
    ```
    *If a `requirements.txt` file is not present, install the dependencies manually based on the `import` statements in the code:*
    ```bash
    pip install streamlit pandas plotly numpy
    ```

#### Running Locally

From the project root directory, execute the following command:
```bash
streamlit run SYPHU-CHINA iGEM - Inclusive Clinical Research.py
```
The application will automatically open in your default browser, typically at `http://localhost:8501`.

### 6. Usage Guide

#### Questionnaire Workflow

1.  **Language Selection**: Choose "中文" or "English" in the top-right corner of the page.
2.  **Informed Consent**: Carefully read the research terms, check all consent boxes, and then click "Start Questionnaire".
3.  **Step-by-Step Completion**: Follow the progress bar at the top of the page to complete the forms for each step. Fields marked with `*` are required.
4.  **Navigation**: Use the "Previous" and "Next" buttons to switch between different steps.
5.  **Submission**: After completing the final step, review your data summary and click the "Submit" button to finish the questionnaire.

#### Live Dashboard

Click the "Live Dashboard" tab at the top of the page to view real-time (simulated) statistical charts about research participation. The charts are interactive; you can hover over data points to see detailed information.

#### Research Transparency Module

Click the "Research Transparency" tab to learn about this study's data usage policy, ethical guidelines, and how to export anonymized data.

### 7. Inclusive Design Philosophy

The design of this platform adheres to the following inclusive principles:

*   **Linguistic Inclusion**: Provides multilingual support to eliminate language barriers.
*   **Identity Inclusion**: Offers multiple options for "Gender Identity," such as "Non-binary," "Transgender," and "Prefer not to say," respecting individual differences.
*   **Cultural Inclusion**: Collects information on ethnicity and residence type to understand health conditions in different cultural contexts.
*   **Ability Inclusion**: Specifically asks about accessibility needs, reflecting care and support for the participation of individuals with disabilities in research.
*   **Digital Divide Consideration**: The questionnaire includes a "Survey Method" option (e.g., paper, phone), acknowledging that not all participants can or are willing to use an online platform.

### 8. Data Management and Ethical Compliance

*   **Informed Consent**: Ensures participants are fully informed about the research through a mandatory informed consent step before data collection begins.
*   **Data Anonymization**: Pledges that all publicly released or analyzed data will be strictly anonymized, removing all personally identifiable information (PII).
*   **Data Security**: (In a production environment) Data transmission should use HTTPS encryption, and database access should be under strict permission control.
*   **Data Usage**: Explicitly promises that all data will be used solely for the iGEM competition and related scientific research purposes.
*   **Ethical Review**: The project's design follows the principles of the Declaration of Helsinki and simulates the approval process of an Institutional Review Board (IRB).

### 9. Contribution Guidelines

We welcome contributions from the community! If you wish to contribute to this project, please follow these steps:

1.  Fork this repository.
2.  Create a new branch (`git checkout -b feature/YourFeature`).
3.  Make your changes.
4.  Ensure your code adheres to the [Black](https://github.com/psf/black) code style.
5.  Commit your changes (`git commit -m 'Add some feature'`).
6.  Push your branch to the remote repository (`git push origin feature/YourFeature`).
7.  Create a Pull Request.

### 10. License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). See the `LICENSE` file for details.

### 11. Citation

If you use this platform or its design philosophy in your research or work, please cite it as follows:

```
SYPHU-CHINA iGEM Team 2025. (2024). SYPHU-CHINA iGEM Inclusive Clinical Research Platform (Version 1.0.0) [Software]. Available from https://github.com/[your-repo-link]
```

### 12. Contact

**SYPHU-CHINA iGEM Team 2025**
