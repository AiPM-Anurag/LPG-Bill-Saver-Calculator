# ⚡ Local Smart Helper (B2B2C MVP)

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![Architecture](https://img.shields.io/badge/architecture-Serverless-orange.svg)

A high-conversion, scalable B2B2C platform designed to digitize local distributors in Hyderabad. The application currently features the **LPG Smart Audit & Induction Sales Module**, acting as a sales enablement tool that calculates wasted energy costs and funnels high-intent buyers directly to local dealers via WhatsApp. 

The architecture is built to easily expand into local Kirana ordering and other neighborhood services.



---

## 🎯 The Vision
Local distributors lack accessible, modern digital storefronts. Cloud databases are expensive and complex to maintain. 
**The Solution:** A completely serverless frontend that uses **Google Sheets as a CMS (Content Management System)**. Distributors simply update a spreadsheet, and the web app instantly reflects new inventory, pricing, and stock status. Orders are captured via an optimized UI and routed seamlessly to the distributor's WhatsApp.

## ✨ Core Features
* **Progressive Disclosure UX:** Users aren't overwhelmed with forms. The UI behaves like a guided conversation.
* **Smart Energy Calculator:** Dynamically computes annual financial waste based on commercial (19kg) vs. home (14.2kg) LPG usage and current electrical conversion rates.
* **Multi-Lingual Support:** Built-in dynamic localization for English, Telugu, and Hindi to maximize local conversion.
* **No-Code Database Sync:** Integrates `PapaParse` to fetch and render product catalogs directly from a published Google Sheet CSV in real-time.
* **Dynamic Lead Routing:** * "Just Exploring" users -> Generates a downloadable PDF Energy Audit Report.
  * "Immediate Need" users -> Skips the PDF and routes directly to the e-commerce catalog and WhatsApp checkout.
* **Zero-Friction Checkout:** Captures user details via a Glassmorphism modal and deep-links directly to WhatsApp with a pre-formatted order receipt.

---

## 🛠️ Technical Stack
* **Frontend:** HTML5, CSS3, Vanilla JavaScript.
* **Styling:** Tailwind CSS (via CDN) with custom CSS Glassmorphism and animations.
* **Icons:** Lucide Icons.
* **Data Parsing:** PapaParse (for robust CSV to JSON conversion).
* **Document Generation:** jsPDF (for client-side PDF creation).
* **Backend / Database:** Google Sheets (Published to Web as CSV).

---

## 🚀 Quick Start / Setup Guide

### 1. Configure the Database (Google Sheets)
The application relies on a strictly formatted Google Sheet. Create a sheet with the following exact column headers in Row 1:
`Product_ID` | `Brand` | `Model_Name` | `Category` | `Burners` | `Price` | `MRP` | `Image_URL` | `Review_Summary` | `In_Stock`

* *Note on Images:* Ensure `Image_URL` links are direct image links ending in `.jpg` or `.png` (e.g., via Postimages or ImgBB). 
* Go to **File > Share > Publish to web**. Select **CSV** and copy the generated link.

### 2. Configure the Frontend
Clone the repository and open `index.html`. Update the `config` object located near the bottom of the script:

```javascript
const config = { 
    wa_num: "91XXXXXXXXXX", // Replace with Distributor's WhatsApp Number
    csvUrl: "YOUR_GOOGLE_SHEETS_CSV_URL_HERE" // Paste your published CSV link
};
