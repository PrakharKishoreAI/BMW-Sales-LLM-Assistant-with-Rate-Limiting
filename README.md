# BMW-Sales-LLM-Assistant-with-Rate-Limiting
A basic rate limiter is added to control the number of requests sent to the LLM.  The project is designed to demonstrate how an LLM application can combine data processing, language models, and request control.
Project Overview

This project is a beginner-friendly LLM application built using a BMW sales dataset.

The application allows a user to ask simple questions about the BMW sales data. A small Hugging Face language model is used to generate natural-language answers.

A basic rate limiter is added to control the number of requests sent to the LLM.

The project is designed to demonstrate how an LLM application can combine data processing, language models, and request control.

Project Motivation

LLM applications can receive many requests from users. If requests are unlimited, the system may consume unnecessary computing resources and,when using paid APIs, can increase API costs.

Rate limiting helps control this usage.

In this project, the system allows a maximum of five requests. After five requests, additional requests are blocked and the system displays a429 Too Many Requests message.

Project Workflow

BMW Sales Dataset

↓

Pandas loads and explores the data

↓

A small dataset context is created

↓

User asks a question

↓

Rate limiter checks the request

↓

If allowed, the request is sent to the LLM

↓

The LLM generates an answer

↓

The request is stored in the request log

↓

Allowed and blocked requests are analyzed

Technologies Used

Python

Pandas

Hugging Face Transformers

FLAN-T5 Small

PyTorch

Matplotlib

Kaggle Notebook

Excel or CSV dataset

Dataset

The project uses a BMW sales dataset.

The dataset is loaded using Pandas. The notebook automatically supportsboth Excel and CSV files.

Example supported files:

bmw_sales_dataset.xlsx

or

bmw_sales_dataset.csv

The exact columns depend on the dataset used.

LLM Model

The project uses:

google/flan-t5-small

FLAN-T5 is a small instruction-following language model that is suitablefor a beginner-friendly demonstration.

The model is used to generate natural-language answers from the BMWdataset context.

Rate Limiting

The project uses a simple request-count based rate limiter.

The configured limit is:

5 requests

The first five requests are allowed.

The sixth and later requests are blocked.

Example:

Request 1: ALLOWED
Request 2: ALLOWED
Request 3: ALLOWED
Request 4: ALLOWED
Request 5: ALLOWED
Request 6: BLOCKED

The blocked request is represented using:

429 Too Many Requests

Request Logging

The application records basic request information:

Request number

User question

Request status

The status can be:

ALLOWED

or

BLOCKED

The logs are converted into a Pandas DataFrame for analysis.

Analytics

The notebook calculates:

Total requests

Allowed requests

Blocked requests

A Matplotlib graph is also created to visualize allowed and blockedrequests.

The request log is saved as:

bmw_llm_request_logs.csv

Project Structure

BMW-Sales-LLM-Rate-Limiter/
│
├── BMW Sales Dataset
├── BMW_LLM_Rate_Limiter.ipynb
├── bmw_llm_request_logs.csv
└── README.md

How to Run

1. Open Kaggle

Create a new Kaggle Notebook.

2. Add the BMW dataset

Use the Add Input option and upload or attach the BMW sales dataset.

3. Run the notebook

Run the cells from top to bottom.

The notebook will:

Install the required libraries.

Load the BMW dataset.

Explore the data.

Load the FLAN-T5 model.

Create a BMW data context.

Answer questions using the LLM.

Apply rate limiting.

Log requests.

Display statistics.

Create a request monitoring graph.

Example Questions

The application can be used with questions such as:

Give me a summary of the BMW sales dataset.

What information is available in this dataset?

What are the main BMW models?

What are the important columns in the dataset?

What can I learn from this BMW sales data?

Important Design Decision

The LLM is not used as an exact calculator.

For exact numerical analysis, Pandas should be used.

For example:

Average price
Total sales
Maximum sales
Minimum sales
Sales by region

These calculations should be performed using Pandas, and the LLM canthen be used to explain the results in natural language.

This separation makes the application more reliable.

What I Learned

This project helped demonstrate:

How to load and explore business data using Pandas

How to load a small Hugging Face language model

How an LLM can be used with structured data

What rate limiting means

Why applications need request limits

What HTTP 429 Too Many Requests represents

How to log application requests

How to analyze application usage

How basic LLM applications are structured

Future Improvements

The current project is intentionally simple.

Possible future improvements include:

Time-based rate limiting

Token Bucket algorithm

Per-user rate limits

Token usage tracking

LLM API cost monitoring

SQLite request storage

FastAPI backend

Better numerical question answering

Deployment as an API


Project Goal

The main goal of this project is to understand the basic architecture ofan LLM application and the importance of controlling model requeststhrough rate limiting.
