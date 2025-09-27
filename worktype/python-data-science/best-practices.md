# Python Data Science Best Practices

> **Scope**: Python data analysis, machine learning, scientific computing  
> **Applications**: Data analysis, ML models, financial analysis, research

## Project Structure

- **Environment Management**: Use `conda` or `venv` for isolated environments
- **Requirements**: Maintain `requirements.txt` or `environment.yml` with pinned versions
- **Directory Structure**: Organize data/, notebooks/, src/, tests/, docs/ directories
- **Configuration**: Use config files (YAML/JSON) for parameters and settings
- **Version Control**: Use Git with `.gitignore` for data files and checkpoints

## Data Management

- **Data Pipeline**: Implement ETL processes with clear data flow documentation
- **Data Validation**: Validate data quality and schema consistency
- **Version Control**: Track data versions and lineage for reproducibility
- **Storage**: Use appropriate formats (Parquet, HDF5) for large datasets
- **Backup**: Implement data backup and recovery strategies

## Pandas Best Practices

- **Memory Optimization**: Use appropriate dtypes and categorical data
- **Vectorization**: Prefer vectorized operations over loops
- **Indexing**: Use proper indexing strategies for performance
- **Chaining**: Use method chaining for readable data transformations
- **Missing Data**: Handle NaN values explicitly and consistently

## Machine Learning Workflow

- **Data Splitting**: Use proper train/validation/test splits with stratification
- **Feature Engineering**: Document feature creation and selection processes
- **Model Selection**: Use cross-validation for model comparison
- **Hyperparameter Tuning**: Implement systematic hyperparameter optimization
- **Model Evaluation**: Use appropriate metrics for problem type
- **Model Persistence**: Save models with versioning and metadata

## Jupyter Notebook Guidelines

- **Cell Organization**: Keep cells focused and well-documented
- **Markdown Documentation**: Use markdown cells for explanations and insights
- **Code Quality**: Follow PEP 8 and use meaningful variable names
- **Reproducibility**: Clear all outputs before committing to version control
- **Conversion**: Convert important notebooks to scripts for production

## Visualization Best Practices

- **Library Selection**: Choose appropriate libraries (Matplotlib, Plotly, Seaborn)
- **Interactive Dashboards**: Use Dash or Streamlit for interactive applications
- **Color Schemes**: Use colorblind-friendly and accessible color palettes
- **Chart Types**: Select appropriate visualization types for data characteristics
- **Annotations**: Add clear titles, labels, and legends

## Performance Optimization

- **Profiling**: Use `cProfile` and `line_profiler` to identify bottlenecks
- **Vectorization**: Leverage NumPy and Pandas vectorized operations
- **Parallel Processing**: Use `multiprocessing` or `joblib` for CPU-bound tasks
- **Memory Management**: Monitor memory usage and optimize data loading
- **Caching**: Cache expensive computations with `functools.lru_cache`

## Testing and Validation

- **Unit Testing**: Test data processing functions and model components
- **Data Testing**: Validate data quality and schema expectations
- **Model Testing**: Test model predictions and performance metrics
- **Integration Testing**: Test end-to-end data pipelines
- **Continuous Integration**: Automate testing with CI/CD pipelines

## Financial Data Analysis

- **Time Series**: Handle time zones, holidays, and market hours correctly
- **Data Quality**: Validate price data for splits, dividends, and corporate actions
- **Risk Metrics**: Implement proper risk calculations (VaR, Sharpe ratio, etc.)
- **Backtesting**: Avoid look-ahead bias and implement realistic trading costs
- **Regulatory Compliance**: Ensure compliance with financial data usage terms

## Documentation and Reproducibility

- **Code Documentation**: Use docstrings and type hints consistently
- **Analysis Documentation**: Document assumptions, limitations, and methodology
- **Environment**: Pin all dependencies and document system requirements
- **Data Sources**: Document data sources, collection methods, and limitations
- **Results**: Save and version model outputs and analysis results
