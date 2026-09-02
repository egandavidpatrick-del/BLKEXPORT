
![GitHub Stars](https://img.shields.io/github/stars/egandavidpatrick-del/saubon-synogen?style=social)
![GitHub Issues](https://img.shields.io/github/issues/egandavidpatrick-del/saubon-synogen)
![License](https://img.shields.io/github/license/egandavidpatrick-del/saubon-synogen)
![Last Commit](https://img.shields.io/github/last-commit/egandavidpatrick-del/saubon-synogen)

#  BLKEXPORT (Case Study – Proprietary Production Application)

A bespoke **C# WinForms desktop application** developed to automate the preparation and completion of Document Issue Registers within the AEC (Architecture, Engineering & Construction) industry.

Document Issue Registers are commonly maintained as bespoke Excel workbooks, with each organisation using its own structure, formatting, document requirements and issue workflows. This makes a universal solution impractical; however, where a defined register format and workflow are established, significant parts of the process can be automated.

The Auto Document Issue Register Updater demonstrates this approach by combining **PDF drawing discovery and validation, Excel register integration, document revision management, recipient management, issue controls and automated PDF generation** into a single desktop workflow.

The application is designed to work alongside existing project documentation and file-system processes rather than requiring organisations to replace their established register format or introduce a new document-management platform.

### Repository Scope

The production application was developed as a bespoke solution and its source code is therefore private. This repository provides the **technical documentation, application screenshots, architecture overview, user guide and video demonstration material** for the solution.


## At a Glance

✔ Winforms application
✔ Comprehensive documentation

# The problem

Completing a Document Issue register typically is a time consuming, tedious and error intensive task completed manually. This manual approach is how most organisations complete a Document Issue Register even today.

# 🧭 BLKEXPORT (Case Study – Proprietary Production Application)
<i>BLKEXPORT allows the user to generate a BOM (Bill of Material) the quick and easy way.</i>
<p align="left">
<img src="/images/image1.png" width=100%" alt="Auto Document Issue Updater Main User Interface">
</p>
💡 **Tip:** Click the hero image to view the full-size version.

---
<a id="enterprise-project"></a>

## 📑 Table of Contents

| 📖 Overview | 🛠️ Technical | 📚 Resources | 📈 About |
|:-----------:|:------------:|:------------:|:----------:|
| 🌐 [Platform Overview](#platform-overview) | ✨ [Key Features](#key-features) | 📦 [Contents](#repository-contents) | 📊 [Results](#results) |
| 💡 [Solution](#solution) | 🛠️ [Tech Stack](#tech-stack) | 📚 [Documentation](#documentation) | 🚦 [Project Status](#project-status) |
| 👥 [Who Is It For](#who-is-it-for) |🏗️ [Updater Architecture](#enola-architecture) | 🖼️ [Screenshots](#screenshots-project-navigator--enola) | 👤 [Author](#author) |
| 🚀 [Why It's Better](#why-is-it-better-than-traditional-workflows)  | ⚙️ [Infrastructure](#operational-infrastructure) | 🔴 [Live Demo](#live-demo) | |
 | | |


---
[Back to top](#enterprise-project)
<a id="platform-overview"></a>
## 🌐 Platform Overview
The BLKEXPORT was originally developed for the AEC (Architecture, Engineering & Construction) industry, where organisations commonly create BOMs (Bill of Material) from their drawings.

[Back to top](#enterprise-project)
<a id="repository-contents"></a>
## 📦 Repository Contents

```text

/guide/user-guide
  Blkexport User Guide Version 1.0.(PDF)

/images/
  Blkexport screenshots

```

---
[Back to top](#enterprise-project)
<a id="documentation"></a>
## 📚 Documentation

This repository includes:

* User Guide
* Application Screenshots
---
[Back to top](#enterprise-project)
<a id="key-features"></a>
## ✨Key Features

- Auto-detects PDF drawings in selected directory - shows [ 10 Drawing(s) ] count in title bar
- Implements aggressive drawing filename validation prior to updated in Excel register See section 23.1 in the Auto Document Register Updater User Guide in this repository
- Browse and link to Document Issue Register Excel file - Document Issue Register.xls or Document Issue Register.xlsx
- Sets Document Issue Register Directory - P:\2019 Projects\...\_Standards\
- Sets Mechanical / Electrical Drawings Directory containing PDFs
- Auto-generates Document Issue Register PDF File Name - Document Issue Register 02-09-26.pdf
- Sets Document Issue Register Output PDF Directory
- Manages Recipients List - Client, Architect, Project Manager, Quantity Surveyor, Main Contractor, Mechanical Contractor, Electrical Contractor, Structural Engineer with Initials + Name fields
- Issue Date picker - 02-09-26
- Clear controls - Clear Recipients List, Clear Issue Register Fields, Clear Drawing Fields, Clear All Revisions Fields
- Open in Excel / Open Drawing Directory / Open Register Directory / View Register PDF
- Optional Contract Specification Documents with Revision - Electrical Contract Specification, Electrical Pricing Document, Mechanical Contract Specification, Mechanical Pricing Document
- Optional Additional Supporting Documentation with Revision - Design Risk Assessment, Preliminary Inspection Plan, BCAR M&E Submittal Schedule
- Issued For - Mandatory - Preliminary, Tender, Information, Scheme, Planning, Construction
- Document Delivery - Mandatory - Prints, Shared Folder, WeTransfer, Email
- PDF Output Sheet Size - A4 / A3
- One-click <b>Update Register</b> - updates Excel and generates PDF register

---
[Back to top](#enterprise-project)
<a id="tech-stack"></a>
## 🛠 Tech Stack

| Component          | Technology                        | Responsibility                                     |
| ------------------ | --------------------------------- | -------------------------------------------------- |
| Operator client    | C# WinForms                       | Auto Document Issue Register Client application    |


<h4>Integrated Development Environment</h4>

- Microsoft Visual Studio 2022
  
<h4>Packager-Deployment</h4>

- Microsoft Visual Studio 2022 Installer Projects
--- 

[Back to top](#enterprise-project)
<a id="enola-architecture"></a>
## 🏗️ Auto Document Issue Register Updater (Case Study – Proprietary Production Application) Architecture 

This is a standalone on-premises WinForms C# desktop application.

**1. Presentation Layer - WinForms UI**

- Single-form UI shown above hero image
- Grouped panels: Register File, Register Directory, Drawings Directory, PDF Output, Recipients List, Contract Specs, Supporting Docs, Issued For, Delivery, Sheet Size
- Browse dialogs, date picker 02-09-26, checkboxes with revision textboxes, radio groups, action buttons - Clear, Open, View, Update Register

**2. File System Layer**

- Input: Scans Mechanical or Electrical Drawings Directory Containing PDF Files - C:\...\Drawings PDF\P2\ - counts [ 10 Drawing(s) ]
- Input: Reads P:\2019 Projects\19L233 Oaklands School Fire Alarm Installation\05_RESOURCES\01_Standards\
- Output: Writes to Document Issue Register Output PDF Directory & Updates Excel Document Issue Register

**3. Data Processing Layer**

- Excel Interop: Opens Document Issue Register.xls, populates drawing list, revision, date, recipients, issued for, delivery
- PDF Generation: Creates Document Issue Register 02-09-26.pdf - A4/A3 selectable
- Revision Manager: Handles T1 / X revision values for 7 optional documents - Electrical/Mechanical Spec/Pricing + Design Risk Assessment, Inspection Plan, BCAR Schedule

**4. Integration Layer**

- Open Register in Excel - Process.Start Excel
- Open Drawing Directory / Open Register Directory - File Explorer
- View Register PDF - Default PDF viewer
- No database - operates directly on file system and Excel

**5. Deployment**

- Built with Microsoft Visual Studio 2022
- Packaged as x64 executable via Microsoft Visual Studio 2022 Installer Projects
- Runs on Windows 11 Pro
- All data stays local/on-prem user computer

---

[Back to top](#enterprise-project)
<a id="screenshots-project-navigator--enola"></a>
## 🖼️ Screenshots Auto Document Issue Register Updater (Case Study – Proprietary Production Application)

<h3>Auto Document Issue Register Updater - File Menu & Help Menu Options</h3>

<p align="left">
  <img src="./images/image2.png" width="49%" alt="alt="Auto Document Issue Register  - File Menu Options">
  <img src="./images/image3.png" width="49%" alt="Auto Document Issue Register - Help Menu Options">
</p>
<h3>Auto Document Issue Register Updater - About Dialog & Interactive ToolTip help</h3>
<p align="left">
  <img src="./images/image4.png" width="49%" alt="alt="Auto Document Issue Register  - File Menu Options">
  <img src="./images/image5.png" width="49%" alt="Auto Document Issue Register - Help Menu Options">
</p>

💡 **Tip:** Click the image for the full-size version.

---

<a id="solution"></a>
[Back to top](#enterprise-project)
## 💡 Solution

The application solves the manual, time-consuming, tedious and error-prone process of completing a Document Issue Register for AEC projects.

How it works:

1. User selects the master Excel register - Document Issue Register.xls or Document Issue Register.xlsx
2. User points to a folder containing Mechanical or Electrical PDF drawings - app auto-detects [ 10 Drawing(s) ]
3. User confirms Recipients List - Client, Architect, PM, QS, Contractors with initials
4. User selects optional contract docs - Electrical / Mechanical Spec & Pricing with revision, plus supporting docs - Design Risk Assessment, Inspection Plan, BCAR Schedule
4. User sets mandatory issue data - Issue Date, Issued For - Information, Delivery Method - WeTransfer, Sheet Size - A4
6. Clicks <b>Update Register</b> - app automatically populates the Excel register with drawing names, revisions, recipients and generates the dated PDF Document Issue Register 02-09-26.pdf in the output directory

Replaces manual copying of drawing names, dates and recipient details with an automated WinForms C# workflow that ensures consistency, accuracy and auditability across document issues.

---
[Back to top](#enterprise-project)
<a id="who-is-it-for"></a>
## 👥 Who Is It For?

Completing a Document Issue Register can be done by the following people:

* Architects
* Engineers
* BIM Coordinators
* BIM Technicians
* CAD Technicians
* Document Controllers

---
[Back to top](#enterprise-project)
<a id="why-is-it-better-than-traditional-workflows"></a>
## 🚀 Why Is It Better Than Traditional Workflows?

Auto Document Issue Register Updater is better than the traditional manual workflow because it replaces a tedious, time-consuming and error-intensive task that typically takes hours with a single-click process that completes a register in seconds. 

The software imposes aggressive drawing file import validation rules, only accepting valid PDF drawings from the selected directory and auto-detecting the drawing count in the title bar before any update can proceed. 

Instead of manually typing drawing names, dates and recipient details, it auto-generates the dated PDF register and locks input and output to the correct project standards location. 

It enforces mandatory completion of Issued For, Document Delivery and Sheet Size, maintains consistent revision control for electrical and mechanical specifications and supporting documents, centralises the eight AEC recipient roles with initials, and simultaneously generates both the Excel register and PDF output with instant access via Open in Excel and View PDF, eliminating copy and paste errors, inconsistent file locations and missing fields while keeping all data on-premises.

---
[Back to top](#enterprise-project)
<a id="operational-infrastructure"></a>
## ⚙️ Operational Infrastructure

**Development and Test Environment**

- Developed and tested on Windows 11 Pro box.

**Software Requirements**
- Computer Aided Design CAD Application to generate DXF file.

---
[Back to top](#enterprise-project)
<a id="live-demo"></a>
## 🔴 Live Demo

[Blkexport Demo](https://youtu.be/Ml7knu5_0QA)

---
[Back to top](#enterprise-project)
<a id="results"></a>
## 📊 Results

- Completes Document Issue Register in seconds vs hours manually
- Eliminates manual data entry for 10+ drawings - auto-detected from drawings directory
- Eliminates file naming errors - auto-generates Document Issue Register 02-09-26.pdf
- Eliminates directory navigation errors - fixed input/output paths to P:\2019 Projects\...01_Standards\
- Ensures consistent recipient information for the current issue
- Ensures consistent revision control for contract specs - T1, X tracking for the current issue
- Ensures mandatory fields are completed - Issued For, Document Delivery, Sheet Size for the current issue
- Generates both Excel Document Issue Register.xls or Document Issue Register.xlsx and PDF output simultaneously
- Provides one-click access to register, drawing folder, and PDF via Open buttons

[Back to top](#enterprise-project)
<a id="project-status"></a>
## 🚦 Project Status

✅ Completed Project  

---
[Back to top](#enterprise-project)
<a id="author"></a>
## 👤 Author

David Egan

Sole Software Developer, Systems Designer, and Solutions Architect for the Auto Document Issue Register Updater (Case Study – Proprietary Production Application)

<a href="https://www.linkedin.com/in/davidpatrickegan">LinkedIn</a> 
