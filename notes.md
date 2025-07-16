## 🗒️ `notes.md` — Setup Notes for Gophish Phishing Simulation

### 🔧 Tools Used

* [Gophish](https://getgophish.com/) — phishing framework
* [Railway](https://railway.app/) — deployed Gophish instance
* [Mailtrap](https://mailtrap.io/) — SMTP sandbox for safe email testing

---

### 🚀 Deployment Steps

#### 1. **Deploy Gophish on Railway**

* Forked the Railway template from [alphasec.io guide](https://alphasec.io/phishing-attack-simulation-with-gophish/)
* Waited for Railway logs to show Gophish password:

  ```
  Please login with the username admin and the password XXXXXXXXXXXXX
  ```
* Admin Panel URL:
  `https://<project-name>.up.railway.app:3333`

---

#### 2. **Login to Gophish Admin Panel**

* Username: `admin`
* Password: (from Railway logs)

---

### 🛠️ Gophish Setup

#### ✅ Users & Groups

* Created group `Test Group`
* Added test user with name/email for tracking

#### ✅ Email Template

* Name: `Test Email`
* From: `IT Support <it-support@example.com>`
* Subject: `Password Expiry Notice`
* Used HTML with `{{.FirstName}}` and `{{.URL}}` placeholder

#### ✅ Landing Page

* Name: `Test Login`
* Custom HTML login form
* Enabled:

  * Capture Submitted Data
  * (Optional) Capture Passwords
  * Redirect to: `https://www.office.com`

#### ✅ Sending Profile

* Name: `Mailtrap Test`
* Host: `sandbox.smtp.mailtrap.io`
* Port: `587`
* Auth credentials from Mailtrap
* Sent test email to verify SMTP connection

---

### 🎯 Campaign Launch

* Campaign Name: `Test Campaign`
* Email Template: `Test Email`
* Landing Page: `Test Login`
* Sending Profile: `Mailtrap Test`
* Group: `Test Group`
* URL: `https://<project>.up.railway.app`

---

### 📊 Results

* Email Opened: ✅
* Link Clicked: ✅
* Credentials Submitted: ✅
  (Tracked via Gophish dashboard)

---

### 🗂️ Files Stored in Repo

* `email_template.html` – email body
* `landing_page.html` – custom fake login
* `campaign-report.md` – incident-style summary
* `screenshots/` – setup & dashboard visuals


