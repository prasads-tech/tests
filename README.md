# Automation Processor

This Python script processes JSON input files to validate fields, replace placeholders in templates, and generate output YAML files. 
It is designed to work with multiple input files, dynamically creating output directories and files based on the provided input data.

## Features
- Loads and parses JSON input files.
- Validates input fields based on a mapping file with rules like required fields, regex patterns, and min/max length.
- Replaces placeholders in a template YAML file with values from the input JSON.
- Generates output directories and YAML files based on the input data.
- Supports error handling for missing files, invalid JSON, and input validation issues.

## Prerequisites
- Python 3.8 >
- Required Python packages: `dotenv` (for loading environment variables).

## Setup

1. Clone the repository.
2. Create a `.env` file in the project directory with the following content:

```bash
   OUTPUT_DIR=/path/to/output
```

# Install dependencies (if not already installed)

```bash
   pip install python-dotenv
```


# Usage
To run the script, execute it with JSON input files as arguments:

```bash
   python3 main.py input1.json
```

## JSON Input File
The JSON input file must contain the following fields:

- CLUSTER_NAME: Used to name the output directory and file.
- mapping: Path to the mapping JSON file for field validation.
- template: Path to the template YAML file where placeholders will be replaced.


## Field Mapping File
The field mapping file defines validation rules for each input field, such as required fields, regex patterns, and min/max length.

## Template File
The template file should contain placeholders in the ${PLACEHOLDER_NAME} that will be replaced with values from the input JSON.

## Output
The script generates a folder structure for each CLUSTER_NAME and creates a YAML file in the output directory. 
The generated folder will have subdirectories like namespaces, config, rbac, and network.

## Example Output Directory

```bash
/Workload/example-cluster/
│
├── namespaces/
│   └── README.md
├── config/
│   └── README.md
├── rbac/
│   └── README.md
├── network/
│   └── README.md
└── example-cluster.yaml
```

## Logging
The script logs important events and errors. Log messages include:

- File processing steps.
- Validation of success or failure.
- Errors such as file not found, JSON decoding issues, and validation errors.
- Error Handling

## The script handles various errors including:

- Missing or invalid JSON files.
- Missing required fields or mismatched field formats in the input.
- Placeholder mismatches between input and template.


# License
This project is licensed under the MIT License.
