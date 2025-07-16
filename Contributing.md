# 🤝 Contributing to AI Builder Labs

First off, thanks for your interest in helping build out this community resource! Whether you’re filing bug reports, suggesting new lab ideas, or submitting a complete step-by-step lab, your contributions are welcome and appreciated.

---

## 📋 How to File an Issue

If you spot a typo, broken link, or want to request a new lab scenario:

1. 1. 1 Go to **Issues** in this repo.  
1. 1. 1 Click **New Issue**.  
1. 1. 1 Select the **Lab idea** or **Bug report** template.  
1. 1. 1 Fill in the details—clear titles and descriptions help us triage faster!

---

## 🆕 Propose a New Lab

Have a great AI Builder or Prompt use case? Here’s how to submit a lab idea:

1. 1. 1 Open a **New Issue** → choose the **Lab idea** template.  
1. 1. 1 Describe your use case: industry, business value, difficulty level, prerequisites.  
1. 1. 1 Optionally sketch out high-level steps or point to reference code/resources.  
1. 1. 1 Submit and let others 👍 or comment to help refine.

Once the idea gains traction, you (or anyone!) can turn it into a full lab by following the steps below.

---

## 📂 Adding or Updating a Lab

Use our built-in template so every lab follows the same structure:

1. 1. 1 Go to `labs/_TEMPLATE_/` and **copy that entire folder**.  
1. 1. 1 Rename the folder to your lab’s slug (e.g., `labs/automated-certificates`).  
1. 1. 1 Inside, open `README.md` and:
   - Replace `<!-- LAB TITLE HERE -->` with your lab’s title.  
   - Fill in **Description**, **Tags**, **Objectives**, **Prerequisites**, **Instructions**, etc.  
   - Update or remove placeholder emojis/icons as needed.  
1. 1. 1 Add any supporting files:
   - Put screenshots, templates, sample docs in `assets/`.  
   - Put exported flow JSON or code snippets in `scripts/`.  
1. 1. 1 Preview in your Markdown editor to ensure formatting looks good.

---

## 🚀 Updating the Lab Index

After you add a new lab folder:

1. 1. 1 Open `README.md` (or `INDEX.md`) at the repo root.  
1. 1. 1 Add a new bullet under **Lab Index**:

   ```markdown
   - [Your Lab Title](labs/your-lab-slug/README.md)  
     *Short description…*  
     **Tags:** tag1, tag2, tag3
