# Databricks Orchestration and Jobs Setup

This repository contains the solution for creating, orchestrating, and scheduling notebooks in Databricks. The task involves comparing the performance of sequential vs. parallel execution of notebooks.

## Project Overview

- **Objective:** To create 4 Databricks notebooks that read from a single table and update data into 5 respective output Delta tables. Then, orchestrate the notebooks both sequentially and in parallel. Finally, compare the runtime of sequential and parallel jobs.

## Repository Structure

- **notebooks/**: Contains all the Databricks notebooks used in the solution.
  - **Notebook1.py**: Reads from the source table and updates Output Delta Table 1.
  - **Notebook2.py**: Reads from the source table and updates Output Delta Table 2.
  - **Notebook3.py**: Reads from the source table and updates Output Delta Table 3.
  - **Notebook4.py**: Reads from the source table and updates Output Delta Tables 4 and 5.
  - **SequentialOrchestration.py**: Orchestrates the above notebooks in sequence using `dbutils.notebook.run`.
  - **ParallelOrchestration.py**: Orchestrates the above notebooks in parallel using the Databricks Concurrent Notebook Workflow.
  
- **scripts/**: Contains shell scripts for creating and scheduling jobs using the Databricks Jobs API.
  - **create_jobs.sh**: Script to create jobs for sequential and parallel execution.
  - **schedule_jobs.sh**: Script to schedule the created jobs.

- **README.md**: Detailed instructions and explanation of the solution.

## Steps to Solve the Problem

### 1. Create 4 Databricks Notebooks
- **Notebook1**: Reads from the source table and inserts/updates data into Output Delta Table 1.
- **Notebook2**: Reads from the source table and inserts/updates data into Output Delta Table 2.
- **Notebook3**: Reads from the source table and inserts/updates data into Output Delta Table 3.
- **Notebook4**: Reads from the source table and inserts/updates data into Output Delta Table 4 and Table 5.

### 2. Create a Sequential Orchestration Notebook
- The `SequentialOrchestration.py` notebook sequentially calls the above 4 notebooks using `dbutils.notebook.run`.

### 3. Create a Parallel Orchestration Notebook
- The `ParallelOrchestration.py` notebook calls the above 4 notebooks in parallel using the Databricks Concurrent Notebook Workflow.

### 4. Create Jobs for Both Orchestration Notebooks
- Use the **create_jobs.sh** script to create jobs for the sequential and parallel orchestration notebooks. The jobs are created using the Databricks Jobs API.
  
  Example usage:
  ```bash
  bash scripts/create_jobs.sh
