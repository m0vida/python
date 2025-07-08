# GLPI KPI Automation Script

This Python script automates the collection and reporting of monthly KPIs for an IT department using the [GLPI](https://glpi-project.org/) service management platform. It connects to the GLPI REST API, fetches tickets created during a specific month (default: **July 2025**), calculates key performance indicators (KPIs), and generates reports in both **Excel** and **HTML** formats.

## 📌 Features

- ✅ Authenticates using GLPI API (username/password + app token)
- 📅 Filters tickets created during a specific month
- 📊 Calculates the following KPIs:
  - Total tickets
  - Average resolution time (hours)
  - SLA compliance (% of tickets resolved within 24 hours)
  - Backlog count (open/unresolved tickets)
  - Reopened ticket count
- 📁 Exports:
  - `.xlsx` report with ticket list, KPI summary, and status breakdown
  - HTML summary of KPIs and status breakdown
- 📧 Sends HTML summary via email (supports Office 365 via app password)

---

## 🧪 Requirements

- Python 3.8+
- GLPI with REST API enabled
- Python packages:
  - `requests`
  - `openpyxl`
  - `smtplib` (built-in)
  - `email` (built-in)

Install dependencies:

```bash
pip install openpyxl
```

---

## ⚙️ Configuration

Edit the following fields in `kpi.py`:

```python
GLPI_URL = "https://your-glpi-domain/apirest.php"
APP_TOKEN = "your-glpi-app-token"
GLPI_USER = "your-username"
GLPI_PASSWORD = "your-password"

smtp_server = "smtp.office365.com"
smtp_user = "your_email@yourcompany.com"
smtp_password = "your_outlook_app_password"
to_email = "recipient@yourcompany.com"
```

> ✅ **Use an Outlook App Password** if MFA is enabled.

---

## 📤 Output

- `glpi_kpi_report_july_2025.xlsx`
  - Sheet 1: Raw ticket list
  - Sheet 2: KPI summary
  - Sheet 3: Status breakdown

- HTML summary emailed with:
  - Tickets grouped by status
  - KPI summary metrics

---

## ⏱️ Coming Soon

- Auto-run via cron (e.g. monthly)
- SLA working hours support (9am–5pm)
- Attachment of Excel file to email

---

## 🔒 Security Notes

- Avoid hardcoding passwords. Use `.env` files or environment variables for production.
- SSL verification is disabled by default (`verify=False`) for internal GLPI servers. Enable it for production systems.

---

## 📃 License

MIT License — Feel free to use, modify, and improve.
