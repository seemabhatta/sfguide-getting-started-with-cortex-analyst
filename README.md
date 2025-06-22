# Cortex Analyst: Getting Started

This repository provides a hands-on introduction to using **Snowflake Cortex Analyst** for natural language interaction with your data. It includes two Streamlit demo applications, sample data, and a semantic model to help you quickly explore and experiment with Cortex Analyst capabilities.

## Features
- **Natural Language Data Analysis:** Ask questions about your data in plain English and get instant answers.
- **Streamlit Demos:** Two ready-to-run Streamlit apps:
  - `app.py` and `demo.py`: Local Streamlit apps for Cortex Analyst REST API and chat-based interface.
  - `cortex_analyst_sis_demo_app.py`: Traditional chat-based interface for Snowflake SiS.
  - `cortex_analyst_streaming_demo.py`: Local streaming demo with real-time SQL and chart rendering.
- **Sample Data & Semantic Model:** Includes CSVs and a YAML semantic model for revenue analysis.

## Prerequisites
- Python 3.8+
- Access to a Snowflake account with Cortex Analyst enabled
- [Streamlit](https://streamlit.io/) installed

## Installation & Setup
1. **Clone this repository:**
   ```powershell
   git clone https://github.com/snowflake-labs/sfguide-getting-started-with-cortex-analyst.git
   cd sfguide-getting-started-with-cortex-analyst
   ```
2. **Create and activate a virtual environment (recommended):**
   ```powershell
   python -m venv venv310
   .\venv310\Scripts\activate
   ```
3. **Install dependencies:**
   ```powershell
   pip install -r requirements.txt
   ```
4. **Configure Snowflake connection:**
   - Create a `.streamlit` directory if it doesn't exist:
     ```powershell
     mkdir .streamlit
     ```
   - Create or edit `.streamlit/secrets.toml` with your Snowflake credentials:
     ```toml
     [connections.snowflake]
     account = "<your-account-identifier>"  # e.g. eic09452 or KIXUIIJ-MTC00254
     user = "<your-username>"
     password = "<your-password>"
     role = "<your-role>"
     warehouse = "<your-warehouse>"
     database = "<your-database>"
     schema = "<your-schema>"
     client_session_keep_alive = true
     ```
   - Example:
     ```toml
     [connections.snowflake]
     account = "eic09452"
     user = "UJJALBFM2025"
     password = "your-password"
     role = "ACCOUNTADMIN"
     warehouse = "CORTEX_ANALYST_WH"
     database = "CORTES_DEMO_2"
     schema = "CORTEX_ANALYST_DEMO"
     client_session_keep_alive = true
     ```
   - **Important:** Add `.streamlit/secrets.toml` to `.gitignore` to avoid committing secrets.

5. **Check and update semantic model:**
   - The semantic model YAML (`revenue_timeseries.yaml`) must reference the correct table names as in your Snowflake database (e.g., `product`, `region`, not `product_dim`, `region_dim`).
   - If you change table names or schema, update the YAML accordingly.

## Project Structure
```
app.py                                 # Streamlit app for Cortex Analyst REST API
cortex_analyst_sis_demo_app.py         # Streamlit app for SiS
cortex_analyst_streaming_demo.py       # Local streaming demo app
revenue_timeseries.yaml                # Example semantic model
requirements.txt                       # Python dependencies
data/
    daily_revenue.csv                  # Sample revenue data
    product.csv                        # Sample product data
    region.csv                         # Sample region data
.streamlit/
    secrets.toml                       # Snowflake connection secrets
```

## Usage
### 1. Run the Main Streamlit App (Recommended)
This app demonstrates natural language interaction with your Snowflake data using the Cortex Analyst REST API.
```powershell
streamlit run app.py
```
- Interact with your data using natural language.
- See database info, run custom queries, and explore tables.

### 2. Run the Advanced Demo App
The `demo.py` app provides a chat-based interface and advanced features.
```powershell
streamlit run demo.py
```
- Enter questions and see real-time SQL and chart results.
- Uses your `.streamlit/secrets.toml` for secure connection.

### 3. Cortex Analyst SiS Demo App
This app is designed for use within Snowflake's Streamlit in SiS (Snowflake in Snowflake):
```powershell
streamlit run cortex_analyst_sis_demo_app.py
```

### 4. Cortex Analyst Streaming Demo (Local)
This app demonstrates real-time streaming with the Cortex Analyst REST API. **You must run this locally.**
1. Edit `cortex_analyst_streaming_demo.py` and fill in your Snowflake credentials and connection details at the top of the file.
2. Run:
   ```powershell
   streamlit run cortex_analyst_streaming_demo.py
   ```

## Data & Semantic Model
- **Sample Data:** Located in the `data/` folder. Includes daily revenue, product, and region CSVs.
- **Semantic Model:** `revenue_timeseries.yaml` describes the data model for revenue analysis, including measures, time dimensions, and calculated fields. Ensure the table and schema names match your Snowflake environment.

## Troubleshooting
- **404 or authorization errors:**
  - Double-check your `secrets.toml` for correct account, user, role, warehouse, database, and schema.
  - Ensure your semantic model YAML references the correct tables and schema.
  - Make sure your user has privileges on all referenced objects.
- **Module not found errors:**
  - Ensure you are running Streamlit from the same virtual environment where you installed the dependencies.
- **Stage or file not found:**
  - Confirm the stage and file exist in your Snowflake account and the path matches your code and YAML.

## Documentation & Resources
- [Cortex Analyst Quickstart Guide](https://quickstarts.snowflake.com/guide/getting_started_with_cortex_analyst/index.html)
- [Cortex Analyst REST API Docs](https://docs.snowflake.com/LIMITEDACCESS/snowflake-cortex/rest-api/cortex-analyst)
- [Streamlit Documentation](https://docs.streamlit.io/)

## Support
For full instructions and troubleshooting, refer to the [Quickstart Guide](https://quickstarts.snowflake.com/guide/getting_started_with_cortex_analyst/index.html).

---
© 2025 Snowflake Inc. | For demonstration and educational use only.
