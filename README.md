# 🧠 Second Brain for ADHD – n8n + Notion + Telegram Reminders

A personal task management automation designed for people with ADHD, built using n8n, Notion, and Telegram.
Automatically reminds you about tasks until you mark them as Done or Abandoned.


# 📌 Overview

This workflow turns your Notion database into a central task hub.

* If a task’s status is In Progress, the system will periodically send reminders via Telegram until it is updated to Done or Abandoned.
* Reminders stop automatically once the task is updated.
* Works best for people who forget tasks despite good intentions.

# Workflow Logic:

1. Notion Database → stores tasks and their statuses.
2. n8n → checks task status and decides whether to send reminders.
3. Telegram Bot → delivers periodic reminders directly to your phone.


# 🛠 Requirements
| Requirement                           | Why Needed                     | Setup Guide                                                                                                          |
| ------------------------------------- | ------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| **Notion Account + API Access Token** | Allows n8n to read/write tasks | [Video: How to get Notion API Token](https://www.youtube.com/watch?v=Ue4sC-PuVxw&ab_channel=AustinReed%7CHorizonDev) |
| **Telegram Bot**                      | Sends reminders                | [Guide: Create a Telegram Bot](https://www.directual.com/lesson-library/how-to-create-a-telegram-bot)                |
| **n8n Instance** (VPS or Cloud)       | Runs the automation            | Self-host or use [n8n Cloud](https://n8n.io). ⚠ **Local hosting on your machine with ngrok not recommended**        |
| **Telegram Chat ID**                  | Required for sending messages  | Use `@userinfobot` in Telegram                                                                                       |


# 📂 Notion Database Structure

Create a dedicated database for this workflow.
All fields below must exist (even if unused).

| Field Name             | Type                  | Example Values / Notes                    |
| ---------------------- | --------------------- | ----------------------------------------- |
| **Name**               | Page (rename default) | "Finish Proposal"                         |
| **Status**             | Select                | To Do, Done, In Progress, Abandoned (Write it as here do **not** change them)       |
| **Last Touched**       | Last Edited Time      | *(auto)*                                  |
| **Type**               | Select                | Voice Memo, Note, Idea, Task              |
| **Mood Tag**           | Select / Multi-select | Foggy, Anxious                            |
| **Created At**         | Created Time          | *(auto)*                                  |
| **Transcription**      | Text                  | Notes, ideas, etc.                        |
| **Tags**               | Multi-select          | Work, Home, Urgent                        |
| **Due Date**           | Date                  | *(date only)*                             |
| **Priority**           | Select                | High, Medium, Low                         |
| **Next Reminder Time** | Date                  | *(leave blank when adding tasks and never touch it)*         |
| **Reminder Set**       | Status                | True, False, Midnight *(default = False)* (Do **not** touch it afterwards) |



# 🚀 Deployment Steps:
1. Clone or import the n8n workflow into your instance.
2. Create the Notion database with the required fields.
3. Get your Notion API token and share the database with the integration.
4. Set up your Telegram Bot and get your chat ID.
5. Update the workflow variables in n8n with your:
    * Notion API token
    * Telegram Bot token
    * Chat ID
6. Deploy & let it run.



# ⚠ Notes

**Local hosting without a static IP/webhook exposure will not work (use VPS or cloud).**

**ngrok is not recommended for long-running reminder loops.**

**You can add more fields to your Notion DB, but required fields must exist for the workflow to function.**

# 📜 License
MIT License – Free to use and modify.
