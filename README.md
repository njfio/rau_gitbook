# Rust Airtable Utility (RAU) Documentation

[![Rust](https://img.shields.io/badge/Rust-2021-orange)](https://www.rust-lang.org/) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Welcome to the Rust Airtable Utility (RAU) documentation. RAU is a command-line utility written in Rust that allows you to interact with the Airtable API. This utility enables you to query, create, and update records in your Airtable bases seamlessly. Below is the detailed documentation for using RAU effectively.

### Features

* **Query Records:** Retrieve records and their field values by record ID or query parameters.
* **Create Records:** Generate new records with specified field values.
* **Update Records:** Modify existing records by updating field values.
* **Cache Management:** Locally cache available fields for faster subsequent requests.
* **Schema and Fields Output:** Display the table schema or available fields for reference.
* **Recent Records:** List the 100 most recent record IDs and their names for quick access.
* **Configuration:** Easily manage multiple Airtable bases and tables through a `config.toml` file.
* **Secure API Key Handling:** Store your API key securely using environment variables.

### Installation

1. **Install Rust:** If you haven't installed Rust yet, you can download it from [here](https://www.rust-lang.org/tools/install).
2.  **Clone the Repository:**

    ```bash
    bashgit clone https://github.com/njfio/rau.git
    ```
3.  **Navigate to the Project Directory:**

    ```bash
    bashcd rau
    ```
4.  **Build the Project:**

    ```bash
    bashcargo build
    ```

### Configuration

1. **Create a Configuration File (`config.toml`):** Place a `config.toml` file in the root directory of your project.
2.  **Define Airtable Configurations:** In `config.toml`, specify your Airtable bases and tables as shown below:

    ```toml
    toml[tables]tweets = { base_id = "appEo7LBNoYQRwEc0", table_name = "Table1" }pokemons = { base_id = "app2jJgrXCQirseg5", table_name = "Pokemon" }prompts = { base_id = "appzdA0NkqZ7JYMeP", table_name = "Prompt PreSet" }
    ```
3. **Set Your API Key:** Add your Airtable API key to `config.toml` or use an environment variable:
   *   **Directly in `config.toml`:**

       ```toml
       tomlapi_key = "YOUR_AIRTABLE_API_KEY"
       ```
   *   **Environment Variable:**

       ```bash
       bashexport AIRTABLE_API_KEY="YOUR_AIRTABLE_API_KEY"
       ```

### Usage

To use RAU, follow the command template below:

```bash
bashrau <config_name> [record_id] [fields] [options]
```

**Arguments:**

* `<config_name>`: The name of the configuration from your `config.toml` file.
* `[record_id]` (optional): The ID of the record to interact with.
* `[fields]` (optional): A list of fields to update or query, specified in key=value format.

**Options:**

* `-s, --schema`: Output the table schema.
* `-f, --fields`: Output the available fields for the table.
* `-r, --recent`: Output the 100 most recent record IDs and their names.

**Examples:**

*   **Query all fields of a record:**

    ```bash
    bashrau tweets rec123
    ```
*   **Query specific fields of a record:**

    ```bash
    bashrau tweets rec123 Name Content
    ```
*   **Update a record:**

    ```bash
    bashrau tweets rec123 Name="Updated Name" Content="New content"
    ```
*   **Create a new record:**

    ```bash
    bashrau tweets
    ```
*   **Output the schema:**

    ```bash
    bashrau tweets --schema
    ```
*   **Output available fields:**

    ```bash
    bashrau tweets --fields
    ```
*   **Output recent records:**

    ```bash
    bashrau tweets --recent
    ```

***

RAU is a powerful CLI tool that simplifies your interaction with Airtable. For advanced usage and further customization, refer to the source code and additional documentation provided in the repository.
