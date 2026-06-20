![License](https://img.shields.io/badge/license-CC--BY--4.0-blue)
![Status](https://img.shields.io/badge/status-Experimental-orange)
![Documents](https://img.shields.io/badge/PST-1-blueviolet)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen)
[![Discussions](https://img.shields.io/github/discussions/daniilkorochansky/pst?label=discussions)](https://github.com/daniilkorochansky/pst/discussions)

<div align="center">
  [English
  /
  <a href="https://github.com/daniilkorochansky/pst/blob/main/README_ru.md">Русский</a>]
</div>

# PST — Pawn Standards and Techniques

PST is a collection of community standards, conventions and best practices
for Pawn development in open.mp and SA-MP projects.

The goal of PST is to improve code readability, maintainability,
tool compatibility and project organization.

## 2. Types of PST Files

All PST files fall into three categories:

1. **Standards:** Documents describing specific technical guidelines for writing code, mod architecture, database integration, and the use of tools (compilers, include files).
2. **Informational:** Guides, tutorials, best-practice overviews, and recommendations. They don't set strict rules, but they help the community grow.
3. **Process:** Documents describing the internal rules of the PST project itself.


## 3. PST Lifecycle and Statuses

Each proposal undergoes a rigorous selection and review process. The document's status is indicated in its title:

* **Draft:** Initial stage. The document is open for suggestions, feedback, and active editing in the Pull Request branch.
* **Review:** The document text has been finalized. The community is conducting a final technical review.
* **Accepted:** The standard has been officially approved and added to the main branch (`main`) of the repository. It is recommended for implementation in all modern projects.
* **Rejected:** The proposal has been deemed ineffective, outdated, or harmful. The document is archived, and the reasons for rejection must be specified.
* **Obsolete:** A previously adopted standard that is no longer relevant (for example, due to global updates to open.mp) and has been replaced by the new PST.

## 4. How to Submit Your PST: A Step-by-Step Guide

Any community member can become a standard author. The process is as follows:

1. **Discussion of the Idea:** Before writing the text, create an issue in the `Issues` section of the PST repository. Describe the problem you want to solve.
2. **Creating a Draft:** If the idea is approved, fork the PST repository and create a new file based on the [TEMPLATE](https://github.com/daniilkorochansky/pst/blob/main/pst-template.md) (for example, `pst-0001-code-style-guide.md`) with the status `Draft`.
3. **Opening a Pull Request (PR):** Submit your draft for review. A public discussion phase will begin, during which each point will be addressed in the code comments.
4. **Revision:** The author is required to respond to constructive criticism and make revisions to the PR.
5. **Recording the Decision:** The PST Editor (or panel of experts) makes a consensus-based decision to change a document's status to `Accepted` or `Rejected`.

---

## 5. Header Template (Metadata)

Each new proposal must begin with the following metadata block:

```text
PST: [Document number, issued by the editor]
Title: [Concise name of the standard]
Author: [Name/Nickname] <[Email or profile link]>
Status: [Draft / Review / Accepted / Rejected / Obsolete]
Type: [Standards / Informational / Process]
Created: [Date in the format DD-Mmm-YYYY, for example 20-Jun-2026]
```

## License

Pawn Standards and Techniques (PST) is licensed under a
Creative Commons Attribution 4.0 International License.

You should have received a copy of the license along with this
work. If not, see [LICENSE](https://github.com/daniilkorochansky/pst/blob/main/LICENSE).
