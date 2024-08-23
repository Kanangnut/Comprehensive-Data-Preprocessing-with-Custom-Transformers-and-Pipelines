# Comprehensive-Data-Preprocessing-with-Custom-Transformers-and-Pipelines

This project demonstrates how to preprocess data using various techniques and pipelines in Python with pandas and scikit-learn.

#### Data Preparation
1. **Initial Data**:
   - Two datasets are provided, `df` and `df2`, with features: `Name`, `Age`, `Gender`, and `Job`.

2. **Preprocessing Steps**:
   - **Dropping Features**: The `Name` column is dropped as it is not needed for analysis.
   - **Imputation**: Missing values in the `Age` column are filled using the mean age.
   - **Encoding**:
     - `Gender` is converted to a binary numeric format (`M` to 0 and `F` to 1).
     - `Job` is one-hot encoded to convert categorical job titles into separate binary columns.

3. **Custom Transformers**:
   - **NameDropper**: A custom transformer to drop the `Name` column.
   - **AgeImputer**: A custom transformer to impute missing values in the `Age` column using the mean.
   - **FeatureEncrypt**: A custom transformer to convert `Gender` to numeric and one-hot encode `Job` titles.

4. **Pipeline**:
   - A `Pipeline` is created to streamline the preprocessing steps, combining `NameDropper`, `AgeImputer`, and `FeatureEncrypt` into a single process.

5. **Application**:
   - The preprocessing steps and pipeline are applied to a new dataset (`df2`), demonstrating how to consistently preprocess data using the defined transformers and pipeline.

#### Key Code Segments
1. **Initial DataFrame Creation**:
   ```python
   df = pd.DataFrame(data)
   ```

2. **Preprocessing Pipeline**:
   ```python
   from sklearn.impute import SimpleImputer
   from sklearn.preprocessing import OneHotEncoder
   # Code to drop columns, impute missing values, and encode categorical features
   ```

3. **Custom Transformers**:
   ```python
   from sklearn.base import BaseEstimator, TransformerMixin
   class NameDropper(BaseEstimator, TransformerMixin): ...
   class AgeImputer(BaseEstimator, TransformerMixin): ...
   class FeatureEncrypt(BaseEstimator, TransformerMixin): ...
   ```

4. **Pipeline Creation and Usage**:
   ```python
   from sklearn.pipeline import Pipeline
   pipe = Pipeline([
       ("dropper", NameDropper()),
       ("imputer", AgeImputer()), 
       ("encrypt", FeatureEncrypt())   
   ])
   ```

5. **Transformations Applied to New Data**:
   ```python
   pipe.fit_transform(df2)
   ```

This project illustrates a methodical approach to preprocessing data, ensuring that missing values are handled, categorical data is encoded, and workflows are streamlined through custom transformers and pipelines.
