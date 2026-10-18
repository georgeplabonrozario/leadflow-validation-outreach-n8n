<!-- Fill every [BRACKET] before publishing. Delete any line that does not match your real workflow. -->

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=170&section=header&text=Lead%20Validation%20%26%20Outreach&fontSize=36&fontColor=ffffff&fontAlignY=40&desc=Clean%20the%20list.%20Keep%20the%20good%20leads.%20Email%20them.&descAlignY=62&descSize=16" width="100%" alt="Lead Validation and Outreach"/>

![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![JavaScript](https://img.shields.io/badge/Code_Node-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Email](https://img.shields.io/badge/Email_Outreach-EA4335?style=for-the-badge&logo=gmail&logoColor=white)

</div>

## The problem

Lead lists collected from forms, scrapers or events are messy. They hold duplicates, broken email addresses, empty fields and dates in five different formats. Sending outreach to that list wastes time and hurts sender reputation.

This n8n workflow takes a raw Excel lead file, cleans and validates it, separates good leads from bad ones, and sends an email only to the good ones.

## What it does

1. **Reads the Excel file** with the raw leads.
2. **Removes duplicates** so one person is never contacted twice.
3. **Validates each record.** Records with missing or invalid fields are marked as bad leads.
4. **Normalizes dates** into one consistent format.
5. **Sorts leads** into good and rejected.
6. **Sends an email** to every good lead.
7. **Builds a summary report** with the totals: records received, duplicates removed, rejected, and emailed.

## Workflow

```
Excel file
    |
    v
Code node: dedupe -> validate -> normalize dates -> flag good / bad
    |
    +-----------------+
    |                 |
 Good leads       Rejected leads
    |                 |
 Send email       Kept for review
    |                 |
    +--------+--------+
             |
             v
      Summary report
```

## Validation rules

<!-- Replace with the exact rules from your Code node. -->

| Check | Rule |
|---|---|
| Email | [Must match a valid email pattern] |
| Name | [Must not be empty] |
| Phone | [Rule, or remove this row] |
| Duplicates | [Matched by email, case-insensitive] |
| Date | [Converted to YYYY-MM-DD] |

A lead counts as **good** when [write your exact condition, for example: email is valid and all required fields are filled].

## Sample summary report

<!-- Replace with a real output from your workflow. -->

```
Total records received : [N]
Duplicates removed     : [N]
Rejected (invalid)     : [N]
Good leads emailed     : [N]
```

## Tech stack

| Part | Tool |
|---|---|
| Automation | n8n |
| Data cleaning and validation | n8n Code node (JavaScript) |
| Input | Excel file |
| Email sending | [Gmail node / SMTP, write the one you use] |

## Design choice

All cleaning logic sits in a single Code node. This keeps the workflow short and easy to read, and the validation rules live in one place that is simple to edit.

## Screenshots

| Workflow | Email sent | Summary report |
|---|---|---|
| ![Workflow](docs/workflow.png) | ![Email](docs/email.png) | ![Report](docs/report.png) |

## Setup

1. Import `workflow.json` into n8n.
2. Add your own email credentials inside n8n.
3. Point the first node to your Excel file.
4. Edit the rules in the Code node if your lead fields differ.
5. Run with a small test file first.

Credentials and real lead data are not stored in this repo. The sample file uses fake data only.

## Author

**George Joseph Rozario Plabon**
[LinkedIn](https://bd.linkedin.com/in/georgeplabonrozario) | [Email](mailto:george.plabon@gmail.com)
