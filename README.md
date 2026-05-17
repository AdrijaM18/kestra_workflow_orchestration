## Kestra Workflow Automation 
A hands-on exploration of Kestra, an open-source workflow orchestration tool, run locally via Docker. This project covers two workflows built and executed through Kestra's UI.

## 🛠️ SetupKestra Workflow Automation
A hands-on exploration of Kestra, an open-source workflow orchestration tool, run locally via Docker. This project covers two workflows built and executed through Kestra's UI.
________________________________________
## 🛠️ Setup
•	Platform: Kestra (self-hosted)
•	Infrastructure: Docker containers (local)
•	Language: YAML (workflow definitions), Python (scripting task)

#### Install Kestra
Before you begin, make sure you have Docker installed. Once installed, download the Docker Compose file from GitHub or using the command below in the terminal:

### Linux/macOS:

curl -o docker-compose.yml \
https://raw.githubusercontent.com/kestra-io/kestra/develop/docker-compose.yml
### Windows:

Invoke-WebRequest -Uri "https://raw.githubusercontent.com/kestra-io/kestra/develop/docker-compose.yml" -OutFile "docker-compose.yml"

Once the file is downloaded, you can start Kestra with the following command:

docker compose up -d
________________________________________

## 📂 Workflows
1. email_notification_flow — Scheduled Email Notification
Namespace: dev.flows
Sends an automated email notification on a daily schedule using Gmail's SMTP server.
What it does:
•	Sends a plain-text email with flow metadata (namespace, flow ID, execution ID, trigger time)
•	Runs every day at 12:10 PM IST (cron: "10 12 * * *", timezone: Asia/Kolkata)
•	Credentials are managed securely via Kestra's built-in secrets ({{ secret('SMTP_PASSWORD') }})

### Key config:
•	SMTP Host: smtp.gmail.com, Port: 587

•	Transport Strategy: SMTP_TLS

•	Uses Pebble templating ({{ flow.id }}, {{ execution.id }}, etc.) for dynamic content
________________________________________
2. ams — Sum Calculator with Python Script
Namespace: company.team
Demonstrates parameterised inputs, a Python scripting task, and a logging task.
What it does:
•	Accepts two integer inputs (n1, n2) with defaults of 10 and 20
•	Runs a Python script inside a python:3.14.5 container that prints a confirmation message
•	Logs the computed sum using Kestra's Log task and Pebble expression evaluation
Key concepts demonstrated:
•	inputs with defaults
•	io.kestra.plugin.scripts.python.Script with containerImage
•	io.kestra.plugin.core.log.Log with inline expression: {{inputs.n1 + inputs.n2}}
________________________________________

Platform: Kestra (self-hosted)
Infrastructure: Docker containers (local)
Language: YAML (workflow definitions), Python (scripting task)

# 📂 Workflows
1. email_notification_flow — Scheduled Email Notification
Namespace: dev.flows
Sends an automated email notification on a daily schedule using Gmail's SMTP server.
What it does:

Sends a plain-text email with flow metadata (namespace, flow ID, execution ID, trigger time)
Runs every day at 12:10 PM IST (cron: "10 12 * * *", timezone: Asia/Kolkata)
Credentials are managed securely via Kestra's built-in secrets ({{ secret('SMTP_PASSWORD') }})

### Key config:
SMTP Host: smtp.gmail.com, Port: 587
Transport Strategy: SMTP_TLS
Uses Pebble templating ({{ flow.id }}, {{ execution.id }}, etc.) for dynamic content

2. ams — Sum Calculator with Python Script
Namespace: company.team
Demonstrates parameterised inputs, a Python scripting task, and a logging task.
What it does:

Accepts two integer inputs (n1, n2) with defaults of 10 and 20
Runs a Python script inside a python:3.14.5 container that prints a confirmation message
Logs the computed sum using Kestra's Log task and Pebble expression evaluation

### Key concepts demonstrated:

inputs with defaults
io.kestra.plugin.scripts.python.Script with containerImage
io.kestra.plugin.core.log.Log with inline expression: {{inputs.n1 + inputs.n2}}


