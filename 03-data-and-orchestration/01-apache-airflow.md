# Apache Airflow: Workflow Orchestration & Pipelines

## Why We Use It at Federated Engineers
At Federated Engineers, we process, transform, and move massive volumes of data daily. A single production data flow might require pulling data from an external API, dumping it into an Amazon S3 bucket, spinning up an ephemeral container to process it, loading it into our cloud data warehouse, and finally running DBT transformations.

If we relied on basic shell scripts or cron jobs, a single network failure would silently crash the entire sequence with no auto-retries, no centralized logging, and no visualization. 

**Apache Airflow** acts as our centralized data operating system. It is the automated "traffic cop" that ensures workflows execute in a strict logical sequence, alerts us instantly if a single task fails, stores centralized execution history, and manages complex upstream and downstream dependencies with precision.

---

## What is Orchestration and a DAG?

Orchestration is the practice of coordinating automated, independent computing tasks into a unified, predictable workflow. 
In Airflow, workflows are defined as code using **DAGs (Directed Acyclic Graphs)**.


* **Directed:** The workflow has a specific direction, flowing sequentially from upstream tasks to downstream tasks.
* **Acyclic:** The workflow cannot contain loops. Task A cannot link back to Task A, preventing infinite execution loops.
* **Graph:** A mathematical design mapping structural relationships. Tasks represent the **Nodes**, and the dependencies between them represent the **Edges**.

---

## The 5 Core Components of Airflow (How They Work)

Airflow is not a single monolith; it is a distributed cluster of micro-services that collaborate continuously. 


### 1. The Metadata Database
The single source of truth for the entire environment. It records the status of every single task run, user credentials, connection variables, and DAG definitions. In our local setup, we use PostgreSQL to match what we run in production.

### 2. The Scheduler
A highly efficient daemon process that continuously monitors all DAG files and task states. When it recognizes that a task's upstream dependencies are completely met and its schedule time has arrived, it hands that task off to the executor.

### 3. The Webserver
The graphical user interface (UI) you open in your browser. It interacts directly with the Metadata Database to allow engineers to trigger DAGs manually, inspect code, read live execution logs, and clear failed tasks to re-run them.

### 4. The Executor & Workers
The Scheduler decides *when* a task runs, but the **Executor** determines *how* it runs, pushing the workload down to the **Workers** (which actually run your code). At Federated Engineers, we configure our staging and production clusters to leverage the `KubernetesExecutor` or `CeleryExecutor` to dynamically scale computational power.

### 5. The DAG File Processor
A background helper sub-process that constantly scans your designated `dags/` Python folder. It translates your Python script syntax into a serialized JSON format and updates the Metadata DB so the UI and Scheduler can instantly see your changes.

## Understanding Scheduling:

#### `schedule:` Accepts cron presets (like @hourly, @daily, @weekly) or custom cron expressions specifying 
exactly what minute, hour, day, and month to wake up.

#### `catchup=False:` Critical configuration flag. If your start_date is set to 6 months ago, setting catchup=True forces 
Airflow to instantly execute hundreds of historic backfill runs simultaneously, 
which can completely overwhelm your database and infrastructure.

## The Power of Operators
An Operator is a predefined template block used to create a single task inside your DAG. 
You don't write low-level code to open connections; you just pick the right tool for the job:

#### Action Operators:
Execute a distinct command or block of logic.

#### BashOperator:
Runs bash commands or custom shell scripts.

#### PythonOperator:
Calls an isolated custom Python function.

#### Transfer Operators:
Built specifically to move data from Source A to Destination B.

Examples: `S3ToRedshiftOperator`, `SQLExecuteQueryOperator`.


### Fast-Track Resources (Curated YouTube Videos)
To master modern Airflow structure and visual configurations, study these comprehensive, video resources:

📺 [Airflow Tutorial For Beginners | Apache Airflow Full Course](https://www.youtube.com/watch?v=IiczxlbQb8s) — A fantastic onestop 2026 masterclass by Ansh Lamba going deep into core concepts, modern SDK usage, structures, and practical local labs.

📺 [Apache Airflow Comprehensive Playlist](https://www.youtube.com/playlist?list=PLwFJcsJ61oujAqYpMp1kdUBcPG0sE0QMT) — A deeper, multi-part curriculum covering advanced scheduling, custom operator builds, task flow APIs, and optimization.
