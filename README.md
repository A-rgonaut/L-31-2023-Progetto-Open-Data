# HealthGraph: A 5-Star Knowledge Graph of Sicilian Health Services

![Jupyter Notebook](https://img.shields.io/badge/Jupyter-FAFAFA?style=for-the-badge&logo=jupyter&logoColor=F37626)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![RDF](https://img.shields.io/badge/RDF-e81b00?style=for-the-badge&logo=semantic-web&logoColor=white)
![SPARQL](https://img.shields.io/badge/SPARQL-005A9C?style=for-the-badge&logo=sparql&logoColor=white)

> Team implementation of 5-star data knowledge from a 2-star dataset of your choice, with a bot application for Telegram.

## 📖 **Context**

This project was developed for the **Open Data Management** examination of Prof. **Davide Taibi**, during the **2022/2023** Academic Year at the **Università degli Studi di Palermo**.

## 👥 **Authors**
_Andrea Spinelli - Marco Valenti - Raffaele Terracino_

## 🛠️ **Technologies Used**

*   **Languages:** Python, SPARQL
*   **Frameworks/Libraries:** Pandas, OSMPythonTools, rdflib, SPARQLWrapper
*   **Other:** Git

## 🚀 **Installation and Startup**

To run this project, you need to set up both the data transformation scripts (optional, as the RDF data is already generated) and the Telegram bot.

### Instructions

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/A-rgonaut/L-31-2023-Progetto-Open-Data.git
    cd L-31-2023-Progetto-Open-Data
    ```

2.  **Set Up a Virtual Environment (Recommended)**
    It's a good practice to create a virtual environment to manage dependencies.
    ```bash
    # Create the virtual environment
    python -m venv venv

    # Activate it
    # On Windows:
    .\venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    ```

3.  **Install Dependencies**
    The project has two main components with their own requirements. Install them both.
    ```bash
    # Install requirements for the Telegram Bot
    pip install -r HealthCareBot/requirements.txt

    # Install requirements for the RDF creation scripts
    pip install -r RDF_creation/requirements.txt
    ```

4.  **Configure the Telegram Bot**
    You need to provide your own Telegram Bot API token.

    *   First, get a token from the [BotFather](https://t.me/botfather) on Telegram.
    *   Navigate to the `HealthCareBot` directory.
    *   Create a copy of the `config.py.example` file and name it `config.py`.
    *   Open `config.py` and paste your token into the `TELEGRAM_TOKEN` variable:

    ```python
    # file: HealthCareBot/config.py

    # Replace "YOUR_TELEGRAM_BOT_TOKEN" with your actual token
    TELEGRAM_TOKEN = "YOUR_TELEGRAM_BOT_TOKEN" 
    ```

5.  **Run the Telegram Bot**
    Now you are ready to launch the bot. Make sure you are in the `HealthCareBot` directory.
    ```bash
    # Navigate to the bot's directory
    cd HealthCareBot

    # Run the bot
    python bot.py
    ```
    Once the bot is running, you can find it on Telegram and start interacting with it.

---
### (Optional) Regenerating the RDF Data
If you want to modify the data transformation process or run it yourself, you can execute the main script located in the `RDF_creation` folder.

```bash
# Navigate to the RDF creation script's directory
cd RDF_creation

# Run the script to generate the .ttl file from the CSVs
python create_RDF.py
```

## ✨ **Key Features**

1. **Transformation and Creation of a Knowledge Graph**

    **Input**: The system starts from a 2-star dataset (.csv) containing information on healthcare entities.

    **Ontology**: It uses a custom ontology (ontology.owl) to define classes (e.g., Pharmacy, Hospital), properties, and relationships between them, following Semantic Web best practices.

    **Enrichment**: Using Python scripts (RDF_creation/), the project transforms tabular data into a structured and interconnected format.

    **Output**: The final result is a knowledge graph in RDF/Turtle (.ttl) format, which represents the data in 5-star Linked Open Data format. This means that the data is not only machine-readable, but also linked to other data and contextualized, making it much more powerful.

2. **Telegram Bot for Querying the Knowledge Graph**

    **User Interface**: It provides a simple and intuitive interface via a Telegram bot, allowing anyone to “talk” to the data without needing to know complex query languages such as SPARQL.

    **Functional Queries**: The bot allows you to perform searches and obtain useful information, such as:
    Finding pharmacies/drugstores in a given city.
    Searching for healthcare institutions by name.
    Obtaining specific details about an institution (e.g., address, hours, VAT number).

    **Natural Language Interactio**n: The user can interact with the bot using simple and direct commands (e.g., /search_pharmacies Rome).
