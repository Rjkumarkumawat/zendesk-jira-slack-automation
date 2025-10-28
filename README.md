
# 🎯 Zendesk → Google Sheets → Jira → Slack  
### Automated Ticket Triage & Engineering Notifications (Built with n8n)

This workflow monitors Zendesk for new support tickets, automatically categorizes them, creates Jira issues, logs the ticket data in Google Sheets, and sends real-time alerts to Slack.  
A powerhouse workflow for support and engineering collaboration. ⚙️💬

---

## 🚀 Key Capabilities

| Feature | Benefit |
|--------|---------|
| Auto-poll Zendesk for new tickets | No manual monitoring |
| Categorizes into Bug / Story / Task | Clean engineering intake |
| Creates Jira issues instantly | Faster fix & development |
| Logs tickets into Google Sheets | Reporting and insights |
| Slack alert to engineering/support team | Real-time visibility |
| Fully automated | Set → Forget ✅ |

---

## 🧠 Ticket Type Mapping Logic

Zendesk Ticket Type | Jira Issue Type | Explanation
|-|:-:|--|
incident | Bug | Production breakages |
problem | Story (CHR) | Change or new feature request |
question | Task | Support guidance |

Mapping Code Snippet:
```js
const typeMap = {
  incident: 'Bug',
  problem: 'Story',
  question: 'Task'
};
```

---

## 🏗️ Workflow Architecture (n8n)

```
[Manual / Cron / Schedule Trigger]
              |
          [Zendesk]
              |
[Append / Update Google Sheet]
              |
   [Filter - Last 5 Minutes]
              |
   [Transform Type (JS Code)]
      /           |            \
 [Bug]        [Story]        [Task]
    |            |             |
[Jira Bug]   [Jira Story]   [Jira Task]
      \         |         /
       \      📨 Slack Alert
        \___________/
```

---

## ✍️ Issue Formatting Examples

### 🐛 Bug
```
Bug: Pre-processor pipeline not working for last 2 days  
Impact: Reports not updated.  
Expected: ETL workflow should execute.  
```

### 📘 Story (CHR Request)
```
Story: On-demand summary application required for reports  
Business Value: Faster decision making for operations  
```

### ✅ Task
```
Task: Arrange meeting to understand workflow  
Outcome: Clarity for support task handling  
```

---

## 🔐 Credentials Required

| System | Credential Type | Permissions Required |
|--------|------------------|--------------------|
| Zendesk | API Token | Agent API access |
| Jira Cloud | API Token | Create Issues |
| Google Sheets | OAuth2 | Read/Write |
| Slack | Bot Token | chat:write |

---

## ⏱️ Trigger Options

Trigger | Best Use
|---|---|
Manual Trigger | Testing or one-time sync  
Cron (5 min) | Standard production  
Schedule Trigger (2 min) | Faster detection in live support

> Enable only one trigger node in production ✅

---

## 📦 Folder Structure (Recommended)

```
📦 zendesk-jira-slack-automation
 ┣ 📂 workflow-json
 ┃ ┗ workflow.json
 ┣ 📂 images
 ┃ ┣ workflow.png
 ┃ ┣ slack-message.png
 ┃ ┗ google-sheet.png
 ┣ 📜 README.md
 ┗ 📜 LICENSE
```

---

## 📸 Add Screenshots Here

```
### Workflow UI
![Workflow Screenshot](./images/workflow.png)

### Slack Notification Example
![Slack Message](./images/slack-message.png)

### Ticket Log in Sheet
![Google Sheet](./images/google-sheet.png)
```

---

## 🌱 Future Enhancements

✅ Auto-assignment to Jira component owners  
✅ Priority badges in Slack messages  
✅ Sync Jira status → Zendesk  
✅ AI summary generation for long tickets  

---

## 💡 Who Should Use This?

Team | Benefit
---|---
Support | Faster escalation to engineering  
Dev / QA | Organized backlog creation  
Management | Transparent ticket tracking and metrics  

---

---

## 💜 Author

Built with 💡 automation brainpower by **Rajkumar**  
Powered by **n8n Open Source Workflow Automation**
