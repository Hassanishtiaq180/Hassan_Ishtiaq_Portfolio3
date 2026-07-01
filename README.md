# 🌐 Hassan Ishtiaq Minhas — Professional Academic Homepage

This repository contains the source code and production markdown assets for my personal academic and engineering portfolio homepage, hosted live via GitHub Pages. 

The site is built as a modular single-page static application that leverages dynamic front-end parsing engines to render structured hardware project histories, embedded systems architectural layers, and peer-reviewed research papers directly from clean Markdown and YAML configurations.

---

## 🛠️ Portfolio Architecture & Tech Stack

* **Front-End Layout & Styling:** Static HTML5 + CSS3 + Bootstrap 5 (with Bootstrap Icons) for responsive UI components.
* **Markdown Compilation:** `marked.js` integrated to dynamically parse and render text data into structured HTML elements at runtime.
* **Configuration Management:** `js-yaml` utilized to parse systemic environment variables from a centralized configuration file.
* **Mathematical Typesetting:** `MathJax` library embedded to render formal LaTeX-style formulas and state-space control loop parameters cleanly.
* **Typography Engine:** Google Fonts optimization.

---

## 📂 Repository Content Structure

```text
├── index.html                  # Main single-page interface & core rendering engine script
├── assets/                     # Physical hardware pictures, 3D PCB layouts, and schematics
└── contents/
    ├── config.yml              # Central navbar configurations, footers, and page taglines
    ├── home.md                 # Technical bio, engineering toolstack, and education overview
    ├── experience.md           # Deep engineering history (Sabro Technologies & Enertia Pvt Ltd)
    ├── publications.md         # Peer-reviewed academic entries (MDPI Sensors & IEEE RAEE)
    └── awards.md               # Honors, deployment milestones, and strategic R&D recognition
