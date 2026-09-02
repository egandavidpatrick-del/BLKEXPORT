
![GitHub Stars](https://img.shields.io/github/stars/egandavidpatrick-del/saubon-synogen?style=social)
![GitHub Issues](https://img.shields.io/github/issues/egandavidpatrick-del/saubon-synogen)
![License](https://img.shields.io/github/license/egandavidpatrick-del/saubon-synogen)
![Last Commit](https://img.shields.io/github/last-commit/egandavidpatrick-del/saubon-synogen)

#  BLKEXPORT (Case Study – Proprietary Production Application)

BLKEXPORT is a bespoke C# WinForms desktop application developed to automate the generation of a Bill of Materials (BOM) from CAD drawings — a common but time-consuming workflow within the AEC (Architecture, Engineering & Construction) industry.

The application demonstrates this approach by parsing an AutoCAD 2018 DXF (ASCII or Binary) file into a single, streamlined desktop workflow. Once loaded, it inventories all block insertions, validates data integrity, and categorises them as Anonymous, Non-Attributed, or Attributed blocks.

The user can then export two distinct CSV outputs:

<b>1. Export to CSV</b> – Full Block Schedule with handle, insertion coordinate, drawing space, layout, block name and attribute data.

<b>2. Export BOM to CSV</b> – Consolidated Bill of Materials.

### Repository Scope
As BLKEXPORT was developed as a bespoke production development, its source code remains private. This repository therefore provides the supporting materials for the solution, including technical documentation, architecture overview, application screenshots, user guide, and video demonstration.


## At a Glance

✔ Winforms application
✔ Comprehensive documentation

# The problem

Generating a BOM from CAD drawings is typically still a manual process — the drawings are plotted, symbols are counted by hand using a highlighter, and the totals are recorded in something like an Excel spreadsheet. This remains the standard practice in most companies today.

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
| 👥 [Who Is It For](#who-is-it-for) |🏗️ [BLKEXPORT Architecture](#enola-architecture) | 🖼️ [Screenshots](#screenshots-project-navigator--enola) | 👤 [Author](#author) |
| 🚀 [Why It's Better](#why-is-it-better-than-traditional-workflows)  | ⚙️ [Infrastructure](#operational-infrastructure) | 🔴 [Live Demo](#live-demo) | |
 | | |


---
[Back to top](#enterprise-project)
<a id="platform-overview"></a>
## 🌐 Platform Overview
BLKEXPORT was originally developed for the AEC (Architecture, Engineering & Construction) industry, where creating a Bill of Materials (BOM) directly from drawings is a common requirement.

[Back to top](#enterprise-project)
<a id="repository-contents"></a>
## 📦 Repository Contents

```text

/guide/user-guide
  BLKEXPORT User Guide Version 1.0.(PDF)

/images/
  BLKEXPORT screenshots

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

- DXF Import: Loads AutoCAD 2018 DXF (ASCII or Binary) via File > Open DXF (Ctrl+O)
- Automated Block Inventory: Parses and counts all block insertions - e.g. 10,009 blocks from BLKEXPORT.dxf
- Block Categorisation: Automatically splits blocks into 3 filtered tabs - Anonymous Blocks, Non-Attributed Blocks, and Attributed Blocks
- Detailed Data Grid: Displays Handle, Insertion Coordinate, Drawing Space, Layout Name, Block Name, and Attribute Value for every insertion
- Dual Export Options: One-click export via top buttons or File menu - Export to CSV (Full Block Schedule) and Export BOM to CSV (Consolidated Bill of Materials)
- Integrity Summary & Validation: Shows Drawing name, Last Modified date, Total/Anonymous/Non-Attributed/Attributed counts, LUPREC precision, Anonymous blocks detected, and Integrity Status - PASS / FAIL verification
- Context-Sensitive Help: Info icons with tooltips that define terms in-place, e.g. Non-Attributed = Blocks that do not contain attribute data
- Application Metadata: About dialog (Help > About) showing designer, version 1.0, platform, operating system registered details and System Info
- User Guide Access: Built-in help via Help > User Guide (Ctrl+H)

---
[Back to top](#enterprise-project)
<a id="tech-stack"></a>
## 🛠 Tech Stack

| Component          | Technology                        | Responsibility                                     |
| ------------------ | --------------------------------- | -------------------------------------------------- |
| Operator client    | C# WinForms                       | BLKEXPORT Client application    |


<h4>Integrated Development Environment</h4>

- Microsoft Visual Studio 2022
  
<h4>Packager-Deployment</h4>

- Microsoft Visual Studio 2022 Installer Projects
--- 

[Back to top](#enterprise-project)
<a id="enola-architecture"></a>
## 🏗️ BLKEXPORT (Case Study – Proprietary Production Application) Architecture 

BLKEXPORT is a standalone C# WinForms (.NET) desktop application built as a single-workflow pipeline: DXF In > Parse > Validate > Categorise > Export.

**1. Presentation Layer (WinForms)**
- MainForm: Hosts the DXF path input, tabbed DataGridView (Anonymous / Non-Attributed / Attributed), Integrity Summary panel, and primary CTAs - -Export to CSV and Export BOM to CSV.
- Menu System: File (Open, Export, Exit) and Help (About, User Guide) with keyboard shortcuts (Ctrl+O, Ctrl+E, Ctrl+B, Ctrl+X, Ctrl+A, Ctrl+H).
Dialogs: About dialog for licensing/metadata and System Info for environment diagnostics.

**2. Application / Business Logic Layer**

- Load Controller: Handles file selection, validates file type (AutoCAD 2018 DXF ASCII/Binary), and triggers the parsing engine.
- Block Classification Service: Routes every INSERT entity into one of three collections:
  - Anonymous Blocks: *U / *D anonymous definitions
  - Non-Attributed Blocks: Standard blocks with no ATTRIB data
  - Attributed Blocks: Blocks with associated attribute values
- Integrity Engine: Calculates Total Blocks, verifies counts across tabs, reads header vars like LUPREC for coordinate precision, Last Modified, and sets Integrity Status: PASS/FAIL.
  
**3. Data / Parsing Layer**
  
- DXF Parser Engine: Low-level ASCII/Binary DXF reader that reads HEADER, TABLES, BLOCKS, and ENTITIES sections. Extracts only INSERT entities.
- Entity Model:
Handle | Insertion Coordinate (X,Y,Z) | Drawing Space (Model/Paper) | Layout Name | Block Name | Attribute Value
- LUPREC Handling: Uses the drawing's LUPREC (4 in the demo) to correctly format insertion coordinates.
  
**4. Export Layer**
  
- Export to CSV Engine: Serializes the currently active tab or full data grid to a flat schedule - 1 row = 1 block insertion.
- Export BOM to CSV Engine: Aggregates by Block Name + Attribute Value to generate a consolidated Bill of Materials with quantities.

---

[Back to top](#enterprise-project)
<a id="screenshots-project-navigator--enola"></a>
## 🖼️ Screenshots BLKEXPORT (Case Study – Proprietary Production Application)

<h3>BLKEXPORT - File Menu & Help Menu Options</h3>

<p align="left">
  <img src="./images/image2.png" width="49%" alt="alt="Auto Document Issue Register  - File Menu Options">
  <img src="./images/image3.png" width="49%" alt="Auto Document Issue Register - Help Menu Options">
</p>
<h3>BLKEXPORT - About Dialog & Interactive ToolTip help</h3>
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
