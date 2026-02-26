# 🚀 GroupMe Bulk Member Adder

Because adding 100+ people to a group one-by-one is a special kind of manual labor nobody has time for.

This is a **single-page, client-side web application** that allows you to bulk-invite members to any GroupMe group using your Developer API token. It supports both manual entry and CSV uploads with intelligent column mapping.

---

## ✨ Features

* **Zero Setup:** No `npm install`, no servers, no backend. Just a single HTML file.
* **Two Ways to Add:**
* **Manual Entry:** Quickly type in names and phone/emails with a dynamic UI.
* **CSV Upload:** Upload any spreadsheet and map your columns (Name, Phone, Email) on the fly.


* **Smart Batching:** Automatically splits large lists into chunks of 10 to comply with GroupMe API preferences.
* **Asynchronous Polling:** Real-time logging that waits for GroupMe's server to confirm each member was successfully added.
* **Privacy First:** Your API token never leaves your browser. All requests are sent directly from your machine to GroupMe.

---

## 🛠️ Getting Started

### 1. Prerequisites

You will need a **GroupMe Access Token**.

1. Log in to the [GroupMe Developers Portal](https://www.google.com/search?q=https://developer.groupme.com/).
2. Click **"Access Token"** in the top right menu.
3. Copy that string of characters.

### 2. Finding your Group ID

1. Log in to [GroupMe Web](https://www.google.com/search?q=https://web.groupme.com/).
2. Click on the group you want to manage.
3. Look at the URL in your browser. The number at the end (e.g., `12345678`) is your **Group ID**.

### 3. Usage

1. Open the `index.html` file in any modern web browser.
2. Enter your **API Token** and **Group ID**.
3. **Manual Mode:** Fill out the rows. Click "+ Add 10 Rows" to expand quickly.
4. **CSV Mode:** * Upload your file.
* Select which columns represent the Name, Phone, and Email.
* Check the **Ready to Import!** preview to ensure your data is parsed correctly.


5. Hit **Start Adding Members** and watch the logs.

---

## 📊 CSV Requirements

For the best results, your CSV should have a header row.

* **Required:** A Name/Nickname column.
* **Required:** At least one contact method (Phone Number or Email).
* **Phone Format:** International format is best (e.g., `+15550001111`).

---

## 🧠 Technical Details

* **Library:** Uses [PapaParse](https://www.papaparse.com/) via CDN for robust CSV parsing.
* **State Management:** Vanilla JavaScript handles the tab switching and dynamic row generation.
* **API Flow:**
1. Generates a unique `guid` for every member request to prevent duplicates.
2. Sends a `POST` request to `/members/add`.
3. Captures the `results_id`.
4. Polls the `/members/results/{id}` endpoint every 2 seconds until confirmation is received.



---

## ⚠️ Important Considerations

* **Rate Limits:** While this tool batches requests, GroupMe may still rate-limit you if you add hundreds of people in a very short window.
* **Permissions:** You must be an owner or have administrative permissions in the group to add members via API.
* **Security:** **Never** share your API token. If you suspect your token has been compromised, reset it immediately on the GroupMe Developer site.

---

> **Disclaimer:** This tool is not affiliated with, maintained, or endorsed by GroupMe or Microsoft. Use responsibly and in accordance with the GroupMe Terms of Service.

Would you like me to add a specific **License** section (like MIT) or perhaps a troubleshooting guide for common API errors?
