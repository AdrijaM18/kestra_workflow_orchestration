Kestra Workflow Automation — Personal Learning Project
A hands-on exploration of Kestra, an open-source workflow orchestration tool, run locally via Docker. This project covers two workflows built and executed through Kestra's UI.

🛠️ SetupKestra Workflow Automation — Personal Learning Project
A hands-on exploration of Kestra, an open-source workflow orchestration tool, run locally via Docker. This project covers two workflows built and executed through Kestra's UI.
________________________________________
🛠️ Setup
•	Platform: Kestra (self-hosted)
•	Infrastructure: Docker containers (local)
•	Language: YAML (workflow definitions), Python (scripting task)
________________________________________
📂 Workflows
1. email_notification_flow — Scheduled Email Notification
Namespace: dev.flows
Sends an automated email notification on a daily schedule using Gmail's SMTP server.
What it does:
•	Sends a plain-text email with flow metadata (namespace, flow ID, execution ID, trigger time)
•	Runs every day at 12:10 PM IST (cron: "10 12 * * *", timezone: Asia/Kolkata)
•	Credentials are managed securely via Kestra's built-in secrets ({{ secret('SMTP_PASSWORD') }})
Key config:
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
🔑 Concepts Covered
Concept	Details
Scheduling	Cron-based trigger with timezone support
Secrets management	{{ secret('...') }} for sensitive credentials
Dynamic templating	Pebble expressions for flow/execution metadata
Containerised tasks	Python scripts run in isolated Docker containers
Parameterised inputs	Typed inputs with default values
Task chaining	Sequential task execution within a flow



Platform: Kestra (self-hosted)
Infrastructure: Docker containers (local)
Language: YAML (workflow definitions), Python (scripting task)


📂 Workflows
1. email_notification_flow — Scheduled Email Notification
Namespace: dev.flows
Sends an automated email notification on a daily schedule using Gmail's SMTP server.
What it does:

Sends a plain-text email with flow metadata (namespace, flow ID, execution ID, trigger time)
Runs every day at 12:10 PM IST (cron: "10 12 * * *", timezone: Asia/Kolkata)
Credentials are managed securely via Kestra's built-in secrets ({{ secret('SMTP_PASSWORD') }})

Key config:

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

Key concepts demonstrated:

inputs with defaults
io.kestra.plugin.scripts.python.Script with containerImage
io.kestra.plugin.core.log.Log with inline expression: {{inputs.n1 + inputs.n2}}


🔑 Concepts Covered
ConceptDetailsSchedulingCron-based trigger with timezone supportSecrets management{{ secret('...') }} for sensitive credentialsDynamic templatingPebble expressions for flow/execution metadataContainerised tasksPython scripts run in isolated Docker containersParameterised inputsTyped inputs with default valuesTask chainingSequential task execution within a flow
