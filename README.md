# ResumeMatch
End-to-end distributed deep learning pipeline to match match a resume with relevant jobs from the job postings.

Flow:
. Scraped and stored job postings from multiple sources to GCP (Google cloud), preprocessed data using PySpark on Databricks, and stored collections in MongoDB (ELT pipeline). Utilized Airflow for scheduled scraping.
. Parsed resumes and job postings and generated word embeddings on this cleaned data using Setence transformer models (large and small) 
. Peformed vector similarity search between resume and all job postings embeddings to find the best match and suggest accordingly.
. Achieved perfect accuracy for the manually tested 30 resumes
. Clustered job postings using pyspark clustering libraries to group similar jobs together
