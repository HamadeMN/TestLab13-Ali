# Docker Lab: Containerizing a Three-Tier Application
**INET 4031 - Introductions to Systems**

This lab introduces Docker and Docker Compose by having you containerize a
real, multi-service application. You will package three components: Apache,
Flask, and MariaDB. These will be packaged into separate containers and wired together so they function as a complete application.

The application code and scaffolding are provided. Your job is to complete the Dockerfiles, verify the stack runs correctly, and document your work below.

> **Directions and explanations for this lab are on the repository Wiki.**
> Refer to the Wiki pages for step-by-step instructions.

---

*The sections below are for you to fill out. Replace each placeholder with your own content before submitting. Having a detailed README is the best practice for showing your work in future GitHub repositories.*

---

# Project Overview

<This application is a simple ticket system that lets users view and create support tickets through a web page. It solves the problem of keeping track of issues by storing them in a database instead of random notes or messages. The user interacts with a dashboard in their browser where they can see existing tickets and add new ones. Behind the scenes, Apache serves the webpage, Flask handles the logic, and MariaDB stores the ticket data. -->

# Prerequisit
Before running this lab, I needed a working Ubuntu VM with Docker and Docker Compose installed. Docker also had to be running, and my user needed to be added to the Docker group so I could run commands without permission errors. I also used VS Code with the Remote SSH extension to connect to the VM and work on the files more easily.

# Getting Started

A new teammate would first clone the repository and go into the project folder:

git clone <repo-link>
cd inet4031-testlab12

Then they would create the environment file:

cp .env.example .env

After that, they can start the full application with:

docker compose up --build

Once the containers are running, they can open the app in a browser at:

http://http://192.168.56.101/:80

# Configuration

The `.env` file is used to store the database settings and credentials for the application. It includes values like the database name, username, and passwords. These are not hardcoded into the project for security reasons.

The file contains:
- DB_ROOT_PASSWORD
- DB_NAME
- DB_USER
- DB_PASSWORD

Since this file is not included in the repository, each teammate needs to create their own `.env` file by copying the `.env.example` file and filling in their own values. This keeps sensitive information private and allows the app to connect to the database correctly.

# Verification

To confirm the stack is running correctly, I first checked that all containers were up by running:

docker compose ps

Then I tested the API with:

curl http://localhost:80/health

It should return:
{"database":"connected","status":"healthy"}

After that, I ran the provided check script:

./check-lab.sh

A successful run shows that all checks passed (for example: “9 passed, 0 failed”). This confirms that the containers are healthy, the API is working, and the database is connected. Finally, I opened the web app in a browser and verified that the dashboard loads, shows tickets, and allows creating new ones.

# Feedback (Optional)

<!-- Do you have any feedback you would like to give us after completing this lab? What are some things you enjoyed? What about others that you felt was lackluster? Or maybe there was something that we missed that you'd love for us to touch on! This will help us improve the INET 4031 lab experience. We appreciate everything we can get!  -->
