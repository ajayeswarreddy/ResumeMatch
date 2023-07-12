# ResumeMatcher

Match a resume to relevant open job postings

Team: Prithvi Nuthanakalva, Bharadwaj Allu, Ajayeswar Peddyreddy, Tejaswi Samrat Dasari, Harrison Yu, Akhil Gopi

#### Product Proposal

Build a resume matching platform (i.e. when user uploads a resume, the system parses the resume and finds the most relevant job posting from the available job postings on the internet) - JobsForYou.


### User Flow
- User opens the "Jobs For You" application and is presented with a landing page as shown below.

![landing page](./assets/landing.jpeg?raw=true "Landing page")

- The user is supposed to upload a resume and click the submit button in the UI. Upon doing so, the system will recommend potential jobs that the user is a good match for, as shown below.

![outputs](./assets/results.jpeg?raw=true "Results")

### Steps Involved

#### Data Collection
- Periodically (using Airflow) use job listing APIs to retrieve the open job listings, and save the content to google cloud storage(GCS).
  Eg APIs: https://rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch to extract diverse job descriptions.
- Aggregated the saved data from GCS and created a collection in Mongo Atlas.

#### Encoding Job descriptions and Resumes

- Sentence transformers are deep learning models that take in a sentence as input and generate a dense vector representation of that sentence as output. These vectors are designed to capture the semantic meaning of the input sentence, and therefore they can be used to compare and match sentences based on their meaning.

- In the context of job descriptions, we can use sentence transformers to convert the text of job descriptions into numerical vectors. These vectors can then be used to match job descriptions with candidate resumes, or to cluster similar job descriptions together.

#### Storing and retrieval using Pinecone

- Once the job descriptions have been encoded into vectors using the sentence transformer model, we need to store these vectors in a way that allows us to efficiently search and retrieve them. We have used Pinecone to get this task done efficiently.

- Pinecone is a cloud-based vector database that allows us to store and search high-dimensional vectors efficiently. By storing the encoded job descriptions in Pinecone, we can easily search for and retrieve the most relevant job descriptions based on a candidate's resume or search query.

#### UI development
- The task involves building a front-end application using Streamlit, a Python library used for creating web applications. The purpose of the front-end application is to allow users to upload a resume file in PDF format.In this case, the application is focused on allowing users to upload a PDF file of their resume.

- Once the user has uploaded their resume file in pdf, it gets stored on the device, the path is sent as the argument to the Affinda API to generate
text and further vectorize it to get the relevant job descriptions.
