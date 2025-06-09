# ApexInsight

## 📖 Overview

`ApexInsight` is a powerful Command Line Interface (CLI) tool designed to provide in-depth analysis and clarification of Apex classes and interfaces. Built on top of the robust `apex-parser` library, `ApexInsight` helps developers understand the structure, relationships, and dependencies within their Salesforce Apex codebase.

Whether you're looking to quickly inspect a single class or get a comprehensive overview of an entire Apex folder, `ApexInsight` streamlines the process of extracting valuable metadata, including methods, variables, inheritance, and crucial cross-class references.

## ✨ Features

* **Comprehensive Class Analysis**: Extracts detailed information for each Apex class and interface, including:

  * Simple and fully qualified names

  * Nesting level and parent class information for inner classes

  * Inheritance details (`extends` class and `implements` interfaces)

  * Abstract class identification

* **Variable Insights**: Lists all variables (fields and local) with their names, types, modifiers, and line numbers. Categorizes variables into:

  * Custom Apex classes

  * Standard or custom SObjects (`__c`, `__x`, `__e`, `__mdt`, `__s`)

  * Collection types (List, Set, Map)

* **Method and Constructor Details**: Provides information on all methods and constructors, including:

  * Names, return types, parameters, and modifiers

  * Identification of classes referenced within method and constructor bodies

* **Intelligent Class Reference Clarification**: Automatically resolves simplified class names to their fully qualified names across your analyzed codebase, improving the accuracy of dependency mapping.

* **SOQL Query Exclusion**: Smartly identifies and excludes elements within SOQL queries from being mistakenly identified as Apex class references, ensuring cleaner and more relevant results.

* **Multiple Output Formats**: Export analysis results in:

  * `text` (human-readable summary or detailed)

  * `json` (machine-readable structured data)

  * `report` (a formatted report for better readability)

* **File Output**: Option to save the analysis results directly to a specified file, rather than just printing to the console.

## 🚀 Installation

To use `ApexInsight`, you need Node.js (version 18 or higher) and npm (or yarn) installed on your system.

1. **Clone the repository:**

```bash
git clone https://github.com/alcabon/apexinsight.git
cd apexinsight
```

2. **Install dependencies:**

```bash
npm install
```

3. **Build the CLI tool:**

```bash
npm run build
```

4. **Link the CLI globally (optional, but recommended for easy use):**

```bash
npm link
```

This makes `apexinsight` command available directly in your terminal.

## 💡 Usage

The primary command is `analyze`, which takes a source path (file or directory) as input.

```bash
apexinsight analyze  [options]
```

### Arguments

* `<fileOrFolder>`: The path to a single `.cls` (Apex class) or `.trigger` (Apex trigger) file, or a directory containing Apex files.

### Options

* `-o, --output <format>`: Specifies the output format.

  * `text` (default): A human-readable summary.

  * `json`: A machine-readable JSON object with all extracted data.

  * `report`: A detailed, formatted report of clarification statistics and class registry.

* `-e, --include-errors`: Include any parsing errors encountered in the output. By default, errors are not shown unless this flag is present.

* `-d, --detailed`: For `text` and `report` formats, provides more verbose output, including all variables and methods with their `usedClasses`.

* `-f, --file <path>`: Specifies an output file path to save the results. If not provided, output is printed to `stdout`. Parsing errors (if `--include-errors` is used) will be appended to this file.

### Examples

1. **Analyze a single Apex class file and print basic text output:**

```bash
apexinsight analyze MyClass.cls
```

2. **Analyze an entire folder of Apex classes and save detailed text output to a file:**

```
apexinsight analyze src/classes -d -f analysis_summary.txt
```

3. **Get JSON output for a class and pipe it to a file:**

```bash
apexinsight analyze controllers/AccountController.cls --output json > account_controller.json
```

*Alternatively, using the new `-f` option:*

```bash
apexinsight analyze controllers/AccountController.cls --output json --file account_controller.json
```

4. **Generate a clarification report for an Apex project:**

```bash
apexinsight analyze force-app/main/default/classes --output report
```

5. **Analyze a class, include any parsing errors, and save to a file:**

```bash
apexinsight analyze BuggyClass.cls -e -f buggy_class_analysis.txt
```

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improvements or find any issues, please open an issue or submit a pull request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgements

`ApexInsight` is built upon the foundational work of the `apex-parser` project. Our deepest gratitude goes to the developers and maintainers of this excellent tool, which makes advanced Apex code analysis possible.

* **Based on:** [apex-parser](https://github.com/apex-dev-tools/apex-parser)
