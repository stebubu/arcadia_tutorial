# Climate Risk Assessment Toolbox

This repository is a **template** for a Climate Risk Assessment Toolbox designed to help cities and regions assess climate risks and implement Nature-Based Solutions (NbS). It contains structured documentation (Markdown files organized for GitBook) and automation to publish the content as a website (e.g., via GitBook or GitHub Pages).

## Getting Started

### Prerequisites
- **Node.js and GitBook CLI:** To build or preview the documentation locally, install Node.js and the GitBook CLI (`npm install -g gitbook-cli`).
- **GitHub Pages (optional):** If publishing via GitHub Pages, ensure Pages is enabled on this repository (the included workflow will deploy to the `gh-pages` branch).

### Installation & Local Preview
1. **Clone the repository** to your local machine:  
   `git clone https://github.com/your-org/climate-risk-toolbox.git`
2. **Install dependencies (if any):** If there is a `book.json` or plugins, run `gitbook install` in the repository root to install GitBook plugins.
3. **Serve the documentation locally:**  
   `gitbook serve`  
   This will build the site and serve it at `http://localhost:4000`, so you can view the documentation in your web browser.

You can edit the Markdown files to update content. If you don't want to use GitBook locally, you can still edit and preview the Markdown directly on GitHub or using a Markdown editor of your choice.

## Repository Structure

- **SUMMARY.md:** Defines the table of contents for the documentation (used by GitBook to generate the nav menu).
- **Docs Folders:** Each main section of the toolbox has its own folder (e.g., `Introduction/`, `RiskAssessmentMethodology/`, etc.) containing a `README.md` (and possibly additional pages) for that topic. These correspond to chapters in the GitBook.
- **CaseStudies/**: Contains example case studies. (e.g., `Emilia-Romagna.md` as a sample case study page.)
- **References/**: Contains the `README.md` with reference list for all citations in the documentation.
- **.github/workflows/**: Contains the GitHub Actions workflow for deploying the documentation.
- **README.md:** (this file) Setup instructions and contribution guidelines for the repository.

## Publishing Updates

Any changes pushed to the **main** branch will automatically trigger the GitHub Actions workflow to build and deploy the updated documentation to **GitHub Pages**. Make sure to enable GitHub Pages for this repository (using the `gh-pages` branch as the source). After deployment, you can access the documentation site at `https://<your_username>.github.io/<repository_name>/`.

If you prefer to use **GitBook.com** for hosting, you can import this repository into GitBook or use GitBook’s integration to pull from GitHub. In that case, you might disable the GitHub Pages workflow to avoid confusion.

## Contribution Guidelines

Contributions to improve this toolbox are welcome! To contribute, please follow these guidelines:

- **Content Structure:** Adhere to the existing structure. For example, if adding a new section, create a new folder (with a `README.md`) and update `SUMMARY.md` accordingly. If adding a new case study, create a new markdown file in the `CaseStudies/` folder.
- **Writing Style:** Use clear and concise language. Follow the style of existing content (short paragraphs, informative headings, bullet points for lists, etc.) to maintain consistency.
- **Markdown Formatting:** Use proper Markdown syntax for headings, lists, links, and emphasis. Refer to existing files for examples. Avoid very long paragraphs – break text into logical segments for readability.
- **Citations and References:** If you include information from external sources, use the citation format `【#†L#-L#】` in-text and add the source details to the `References/README.md` file. There are examples of how to do this throughout the content.
- **Data Links:** When referring to data (indicators, maps, etc.), link to the source dataset (for instance, a CKAN open data portal or other source). If the data is not yet available, you can use a placeholder link or note.
- **Submitting Changes:** Fork the repository and create a pull request with your changes. Ensure that the GitBook build remains successful (you can run `gitbook build` locally to catch any errors such as broken links or invalid Markdown).

By following these guidelines, you’ll help keep the toolbox useful and up-to-date. Thank you for contributing to climate resilience knowledge!
