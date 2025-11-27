# finding_jobs
group of czw,wyg,zzh

## topic

* Big data analysis: Job Posting Data Cleanning and Descriptive Analysis

## work allocation
### **I. Project Objectives**
1. Collect public recruitment data and obtain a high-quality dataset through cleaning and processing;
2. Explore key patterns in the data (such as job distribution, salary levels, skill requirements, etc.);
3. Intuitively present recruitment market trends through visualization to provide references for job seekers or enterprises.


### **II. Project Process and Task Breakdown**

#### **Phase 1: Data Acquisition**
**Core Task**: Collect structured/semi-structured data from public job websites to ensure sample size and representativeness.

1. **Selection of Data Sources**
   - Recommended priorities:  
     Zhaopin, 51job (obtain public information using web crawler tools);  
   - Alternative options: Kaggle public datasets (e.g., `Kaggle Job Posts`)  

2. **Determination of Collection Fields** 
   Mandatory fields:  
   - Basic information: Job title, company name, city location, release time, number of recruits;  
   - Core information: Salary range (e.g., "10k-15k/month"), education requirements, work experience requirements;  
   - Descriptive information: Job responsibilities, job qualifications (extract keywords such as "Python", "strong pressure resistance").  

3. **Data Collection Execution** 
   - Tool selection:  
     - Code crawling: Use `Python` + `Requests` (for dynamic pages) + `BeautifulSoup` for parsing;  
   - Output format: Save as `CSV` or `Excel` with naming conventions such as `recruitment_data_raw_202510.csv`.  


#### **Phase 2: Data Cleaning**
**Core Task**: Handle missing values, outliers, format inconsistencies, etc., to form a "clean" dataset.

1. **Data Loading and Preliminary Exploration**
   - Tools: `Python` (with `Pandas` library), `Excel`;  
   - Operations:  
     - Check data scale and field types;  
     - Calculate the proportion of missing values (e.g., `df.isnull().sum()`), and mark fields with severe missing values (fields with a missing rate > 50% are recommended to be deleted).  

2. **Handling Missing Values**
   - Strategies:  
     - Key fields (e.g., salary): If the missing rate is < 10%, use "mode imputation";  
     - Secondary fields (e.g., number of recruits): Mark with "unknown" or `NaN` without forced imputation;  
     - Rows with complete missing values: Delete directly.  

3. **Format Standardization**
   - Salary field: Convert "10k-15k/month" to numerical values (e.g., minimum salary 10000, maximum salary 15000, average salary 12500);  
   - Date field: Unify formats such as "2025-10-01" and "released on October 1st" to `YYYY-MM-DD`;  
   - Text fields: Remove special symbols (e.g., `\n`) from job responsibilities and unify case (e.g., "python" → "Python").  

4. **Handling Outliers**
   - Identification of anomalies:  
     - Salary anomalies (e.g., "1k-2k/month" for a "data scientist" position): Judge based on industry common sense, mark as "outlier" or delete;  
     - Logical contradictions (e.g., "requiring 5 years of experience" but "education requirement: junior college or below" with extremely high salary): Check individually and remove if necessary.  

5. **Data Integration**
   - Add derived fields:  
     - Salary level: Classified as "low (<8k), medium (8k-20k), high (>20k)";  
     - Experience requirements: Convert "1-3 years" "3-5 years" to numerical ranges (e.g., 1-3 years → lower limit 1, upper limit 3);  
   - Output: Save as `recruitment_data_cleaned.csv`.  


#### **Phase 3: Descriptive Analysis**
**Core Task**: Explore data distribution, correlations, and trends through statistical methods.

1. **Univariate Analysis**
   - Categorical variables (e.g., city, education requirements):  
     - Calculate the proportion of job positions in each city and the distribution of education requirements (e.g., "bachelor's degree or above" accounts for 60%);  
   - Numerical variables (e.g., salary, work experience):  
     - Calculate salary mean, median, and standard deviation (to judge salary dispersion);  
     - Analyze the distribution of work experience requirements (e.g., positions requiring "3-5 years of experience" account for the highest proportion).  

2. **Bivariate/Multivariate Analysis**
   - City and salary: Compare average salaries in different cities (e.g., salaries of big data positions in Beijing vs. Shanghai);  
   - Education and experience: Whether high-education positions correspond to lower experience requirements (e.g., the proportion of "less than 1 year of experience" in "master's degree" positions);  
   - Job type and skills: For example, the frequency of "Python", "SQL", and "Excel" in "data analyst" positions.  

3. **Time Trend Analysis**
   - Count changes in the number of positions by release time (e.g., growth trend of "AI engineer" positions in the past 3 months);  
   - Analyze salary fluctuations over time (e.g., salary differences between peak and off-seasons).  


#### **Phase 4: Visualization Presentation**
**Core Task**: Intuitively display analysis results with charts to highlight key conclusions.

1. **Tool Selection**  
   - Entry-level: `Excel` charts, `Tableau`;  
   - Advanced: `Python` libraries (`Matplotlib` for static charts, `Plotly` for interactive charts).  

2. **Essential Visualization Charts**  
   - Geographic distribution of positions: **Bar charts/maps** (showing the number of positions in each city);  
   - Salary distribution: **Box plots** (showing salary ranges and medians for different positions);  
   - Proportion of education requirements: **Pie charts/donut charts**;  
   - Skill requirement popularity: **Word clouds** (extracting high-frequency skills from "job qualifications");  
   - Relationship between experience and salary: **Scatter plots** (x-axis: experience, y-axis: average salary).  

3. **Report Integration**  
   - Arrange charts in the logical order of "geography → salary → skills → trends" and add conclusion explanations (e.g., "The average salary of data positions in first-tier cities is 40% higher than that in second and third-tier cities, and Python is the core skill");  
   - Output format: PDF report.  


### **III. Tools and Technology Stack**
- Data acquisition: `Python` (with `Requests`);  
- Data cleaning: `Python` (with `Pandas`/`NumPy`), `Excel`;  
- Analysis and visualization: `Python` (with `Matplotlib`/`Plotly`), `Tableau`;  
- Version control: `Git` (optional, for code/data version management).  


### **IV. Expected Outcomes**
1. A cleaned recruitment dataset;  
2. A descriptive analysis report containing key findings;  
3. Several core visualization charts supporting interactive or static display.
