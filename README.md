# 🛡️ Guardians – AI-Powered Marketing Automation Workflow

**Guardians** is an intelligent marketing automation workflow built using **n8n**, designed to discover and engage potential business leads automatically.  
It integrates data scraping, AI-based content generation, and Google Workspace automation to streamline outbound marketing campaigns.

---

## 🚀 Features

- **Lead Generation:** Automatically finds businesses in your target industry and location using Google Places data.  
- **Smart Filtering:** Filters out results without valid websites for accurate lead lists.  
- **AI-Powered Email Extraction:** Uses a Large Language Model (LLM) to extract valid contact emails from company websites.  
- **Google Sheets Integration:** Appends lead data (company name, website, email, phone) into a Google Sheet for easy management.  
- **Personalized Email Generation:** Uses Anthropic’s Claude Sonnet model to craft personalized, high-quality promotional emails.  
- **Email Draft Automation:** Creates email drafts in Gmail automatically for review and sending.

---

## ⚙️ Workflow Overview

| Step | Description |
|------|--------------|
| **1. Form Trigger** | Collects user inputs (industry, location, country, city, and preferred email style). |
| **2. Data Scraping** | Calls the Apify Google Places API to fetch potential business leads. |
| **3. Filtering** | Ensures that only businesses with valid websites proceed. |
| **4. Information Extraction** | Uses an AI model to find a valid business email address. |
| **5. Validation** | Ensures extracted emails are in proper format. |
| **6. Data Storage** | Appends the extracted leads into a Google Sheet (`Guardians_Leads`). |
| **7. AI Email Generation** | Generates customized marketing emails using Claude Sonnet. |
| **8. Draft Creation** | Creates Gmail drafts with the generated email body for review. |

---

## 🧠 Tech Stack

- **n8n (Automation Platform)**
- **Apify API (Google Places Crawler)**
- **Anthropic Claude Sonnet 4 (AI Model)**
- **Google Sheets API**
- **Gmail API**
- **JavaScript (for custom parsing)**

---

## 🗂️ File Structure

├── Guardians.json # n8n workflow export file
└── README.md # Project documentation


---

## 🔧 Setup Instructions

1. **Import the Workflow**
   - Open your **n8n** instance.
   - Click on **Import Workflow**.
   - Upload the file `Guardians.json`.

2. **Configure Credentials**
   - **Apify API Token** → For Google Places data scraping  
   - **Anthropic API Key** → For Claude Sonnet model integration  
   - **Google Sheets OAuth2** → For storing leads in Sheets  
   - **Gmail OAuth2** → For creating email drafts  

3. **Setup Google Sheet**
   - Create a Google Sheet named **Guardians_Leads**.
   - Include columns:
     ```
     company_name | website | contact_email | Phone_Number | LinkedIn_link
     ```

4. **Run the Workflow**
   - Open the form trigger link in your n8n instance.
   - Fill in details such as **Target Industry**, **Location**, **Target Country**, **City**, and **Email Style**.
   - Click **GO 🚀** to start.
   - The workflow will:
     - Scrape leads  
     - Extract valid emails  
     - Generate personalized emails  
     - Create Gmail drafts automatically  

---

## 🧩 Example Use Case

**Scenario:**  
A marketing team wants to target construction companies in *Colombo, Sri Lanka*.

**Input via form:**
- Target Company Industry: `Construction`
- Your Location: `Kandy, Sri Lanka`
- Target Country: `Sri Lanka`
- Target City: `Colombo`
- Email Style: `Professional`

**Result:**
- Google Sheet populated with company names, websites, emails, and phone numbers.  
- Gmail drafts created automatically with personalized marketing emails.

---

## 📊 Automation Flow

```mermaid
flowchart TD
    A[Form Trigger] --> B[Apify Google Places API]
    B --> C[Filter Valid Websites]
    C --> D[Information Extractor (LLM)]
    D --> E[Check Valid Email]
    E --> F[Append to Google Sheets]
    F --> G[Claude AI Email Generation]
    G --> H[Create Gmail Drafts]



