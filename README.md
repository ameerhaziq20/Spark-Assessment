# Credit Card Transaction Analysis with PySpark

A comprehensive data analysis project using Apache Spark to process and analyze credit card transaction data, focusing on data cleaning, feature engineering, and fraud detection patterns.

## 🚀 Project Overview

This project demonstrates advanced data processing capabilities using PySpark to analyze a large dataset of credit card transactions. The analysis includes JSON data flattening, data type conversions, timestamp handling, name parsing, and data quality assessment.

### Key Features

- **Large-scale Data Processing**: Handles 1.2M+ transaction records efficiently
- **JSON Data Flattening**: Processes nested JSON structures for personal details and addresses  
- **Data Cleaning Pipeline**: Comprehensive cleaning including name standardization and special character handling
- **Timestamp Conversion**: Converts various timestamp formats to UTC+8 timezone
- **Data Quality Analysis**: Identifies and quantifies data quality issues
- **Memory-optimized Processing**: Implements sampling and chunking for large datasets

## 📊 Dataset Information

- **Size**: 1,296,675 transaction records
- **Format**: JSON with nested structures
- **Key Fields**: 
  - Transaction details (amount, category, merchant info)
  - Personal information (names, addresses, demographics)
  - Fraud labels for supervised learning
  - Geographic coordinates and timestamps

## 🛠️ Technical Stack

- **Apache Spark 4.0.0** - Distributed data processing
- **PySpark** - Python API for Spark
- **Python 3.13.3** - Core programming language
- **Pandas** - Data manipulation and analysis
- **Java 17** - Spark runtime environment

## 📋 Project Structure

```
├── cc_sample_transaction.json          # Source dataset
├── PySpark Assessment.ipynb            # Main analysis notebook
├── PySpark_Assessment_*.html           # HTML export
├── README.md                           # This file
└── convert_to_markdown.py              # HTML to Markdown converter
```

## 🔧 Setup Instructions

### Prerequisites

1. **Java 17** installed and configured
2. **Python 3.8+** with virtual environment
3. **Apache Spark** (handled via PySpark)

### Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd credit-card-analysis
```

2. Create and activate virtual environment:
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install pyspark pandas jupyter nbconvert
```

4. Set Java Home (adjust path as needed):
```bash
export JAVA_HOME="/path/to/java-17"  # On Windows: set JAVA_HOME=C:\Program Files\Microsoft\jdk-17.0.16.8-hotspot
```

## 🚀 Running the Analysis

### Option 1: Jupyter Notebook
```bash
jupyter notebook "PySpark Assessment.ipynb"
```

### Option 2: Direct Python Execution
The notebook contains modular code that can be extracted and run as Python scripts.

## 📈 Analysis Pipeline

### 1. Data Loading & Schema Inspection
- Load JSON data using Spark's built-in JSON reader
- Analyze schema structure and data types
- Assess dataset size and complexity

### 2. Data Flattening
- **Personal Details**: Extract nested JSON fields (name, gender, demographics)
- **Address Information**: Parse address JSON into structured columns
- **Schema Definition**: Create proper Spark schemas for type safety

### 3. Data Type Conversions
- **Numeric Fields**: Convert string amounts and coordinates to doubles
- **Boolean Fields**: Transform fraud flags to proper boolean types
- **Timestamps**: Handle multiple timestamp formats with timezone conversion
- **Dates**: Parse date strings to Spark date types

### 4. Name Processing & Cleaning
- **Special Character Handling**: Replace symbols (@, |, !) with commas
- **Name Standardization**: Remove suffixes like "NOOOO" and "eeeee"  
- **Name Parsing**: Split into first and last names
- **Quality Assessment**: Count null, empty, and malformed names

### 5. Data Quality Analysis
- Comprehensive statistics on data completeness
- Special character detection and quantification
- Name parsing success rates
- Data type validation

## 📊 Key Results

### Data Quality Metrics
- **Total Records**: 1,296,675
- **Clean Names**: ~50% (648,682 records)
- **Names with Special Characters**: ~50% (647,993 records)
- **Successfully Parsed Names**: 83% (1,079,958 records)
- **Missing Last Names**: 16.7% (216,717 records)

### Sample Data Transformations

**Before Cleaning**:
```
Edward@Sanchez          → first_name: "Edward@Sanchez", last_name: NULL
Jeremy/White, !         → first_name: "Jeremy/White", last_name: "!"
Kelsey, , Richards NOOOO → first_name: "Kelsey", last_name: ""
```

**After Cleaning**:
```
Edward@Sanchez          → first_name: "Edward", last_name: "Sanchez"
Jeremy/White, !         → first_name: "Jeremy", last_name: "White"  
Kelsey, , Richards NOOOO → first_name: "Kelsey", last_name: "Richards"
```

## 🔍 Technical Challenges & Solutions

### Memory Management
- **Challenge**: 1.2M+ records causing Java heap space errors
- **Solution**: Implemented data sampling and increased driver memory allocation

### JSON Parsing
- **Challenge**: Nested JSON structures in string fields
- **Solution**: Dynamic schema generation from sample data + `from_json()` function

### Name Standardization  
- **Challenge**: Inconsistent name formats with special characters
- **Solution**: Multi-step regex cleaning pipeline with suffix removal

### Timestamp Handling
- **Challenge**: Mixed timestamp formats (Unix timestamps vs. datetime strings)
- **Solution**: Separate processing pipelines with timezone normalization

## 🎯 Business Applications

This analysis pipeline can be applied to:

- **Fraud Detection**: Clean data enables better ML model performance
- **Customer Analytics**: Standardized names improve customer matching
- **Geographic Analysis**: Parsed addresses enable location-based insights
- **Temporal Analysis**: Proper timestamps support time-series analysis

## 🔮 Future Enhancements

- [ ] **Machine Learning Pipeline**: Implement fraud detection models
- [ ] **Real-time Processing**: Adapt for streaming data with Spark Streaming
- [ ] **Advanced Analytics**: Add statistical analysis and visualization
- [ ] **Data Validation**: Implement comprehensive data quality rules
- [ ] **Performance Optimization**: Further optimize for larger datasets

## 📚 Learning Outcomes

This project demonstrates proficiency in:

- **Big Data Processing**: Handling large datasets with distributed computing
- **Data Engineering**: Building robust data cleaning and transformation pipelines
- **PySpark Expertise**: Advanced usage of Spark DataFrames and SQL functions
- **Data Quality**: Implementing comprehensive data validation and cleaning
- **Performance Optimization**: Memory management and efficient data processing

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙋‍♂️ Author

**Ameer Haziq Basharuddin**

---

⭐ **Star this repository if you find it helpful!**
