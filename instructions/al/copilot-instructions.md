# Contributing to the AL Repository

Welcome! This repository contains AL (Application Language) code for Microsoft Dynamics 365 Business Central extensions. AL is a domain-specific language designed for building business applications that interact with the Business Central platform. It enables you to create customizations, extensions, and integrations for Business Central while adhering to modern development practices. We appreciate your contributions and ask that you follow the guidelines below to maintain code quality and consistency.

This repository utilizes the Model Context Protocol (MCP) to enable AI-assisted development, providing additional context and capabilities for GitHub Copilot and other AI tools when working with AL codebases.

## 📌 Code Standards

### ✅ Required Before Each Commit

Before committing any changes, please ensure the following:

* **Format Code:** Use the AL Formatter in Visual Studio Code to format your code consistently.
* **Lint:** Use the CodeCop analyzer to identify and fix coding issues.
* **Check Syntax:** Run the AL: Validate Syntax command in VS Code to verify code correctness.

### 🔄 Development Flow

* **Install Dependencies:** Install Visual Studio Code with the AL Language extension.
* **Start Development:** Open the project folder in VS Code and make changes to AL files.
* **Build Project:** Press F5 or use the Run command to compile and deploy to a local Business Central instance.
* **Run Tests:** Use AL Test Runner to execute test codeunits.
* **Full CI Check:** Run CodeCop analysis, compile the extension, and execute all tests.

## 📁 Repository Structure

* `src/`: Main source code directory.
  * `AppSourceCop.json`: App source code analyzer configuration.
  * `app.json`: Extension configuration including dependencies, version, and publisher.
  * `.alpackages/`: Contains extension dependencies.
* `Objects/`: Contains AL object files organized by type.
  * `Tables/`: Table and table extension objects.
  * `Pages/`: Page and page extension objects.
  * `Codeunits/`: Codeunit objects (business logic).
  * `Reports/`: Report objects.
  * `Queries/`: Query objects.
  * `XMLports/`: XMLport objects for data import/export.
* `Test/`: Test codeunits and supporting objects.
* `Translations/`: Translation files for multi-language support.
* `Documentation/`: Documentation and developer guidelines.
* `.vscode/`: VSCode configuration files including launch.json and settings.json.
* `.azureDevOps/`: Build and release pipeline configurations.

## 🛠️ Key Guidelines

1. **AL Best Practices**

   * Follow consistent naming conventions (PascalCase for objects, camelCase for variables).
   * Use labels and tooltips for all UI elements to support localization.
   * Define object IDs within designated ranges to avoid conflicts.
   * Use AL features like enums instead of option fields where appropriate.

2. **Performance and Maintainability**

   * Avoid direct SQL statements where standard AL methods are available.
   * Use temporary records and InStream/OutStream for large data processing.
   * Implement proper error handling with TryFunction and Error messages.
   * Consider performance implications when using FINDSET and looping through records.

3. **State and Data Management**

   * Use proper transaction handling with COMMIT and database locking strategies.
   * Implement proper validation on all user inputs.
   * Use events for loosely coupled extensions.
   * Consider data security and privacy in your designs.

4. **Testing**

   * Write test codeunits for all business logic.
   * Use the Test Runner functionality for automated testing.
   * Create separate test libraries for reusable test functions.
   * Include both positive and negative test cases.

5. **Documentation**

   * Document all public procedures with XML documentation comments.
   * Create user documentation for custom functionality.
   * Document complex business rules and calculations.
   * Keep the README updated with extension capabilities and setup instructions.

6. **Dependencies**

   * Be mindful of adding dependencies to other extensions.
   * Document minimum required Business Central version.
   * Use proper dependency declarations in app.json.
   * Consider backward compatibility for upgradeability.

## 🤖 Using GitHub Copilot as a Coding Agent

To effectively leverage GitHub Copilot in this repository, please adhere to the following best practices:

### 🧩 Assigning Tasks to Copilot

* **Well-Scoped Issues:** Ensure that issues assigned to Copilot are clear and well-defined. Include:

  * A concise description of the problem or task.
  * Acceptance criteria outlining what a successful solution entails.
  * Specific files or areas of the codebase that need to be addressed.

* **Appropriate Tasks:** Assign tasks that are suitable for Copilot, such as:

  * Fixing bugs.
  * Enhancing test coverage.
  * Updating documentation.
  * Creating standard AL patterns like list pages or reports.
  * Addressing technical debt.

Avoid assigning complex, ambiguous, or sensitive tasks that require deep domain knowledge or involve critical business logic.

### 💬 Iterating on Pull Requests

* **Reviewing Copilot's Work:** Treat Copilot-generated pull requests as you would those from human contributors. Review the code thoroughly and provide feedback through comments.

* **Batching Comments:** If you have multiple comments, batch them using GitHub's "Start a review" feature. This approach allows Copilot to process all feedback collectively, leading to more coherent updates.

### 🛡️ Security and Best Practices

* **Code Review:** Always review and test Copilot's code suggestions to ensure they meet security standards and do not introduce vulnerabilities.

* **Prompt Engineering:** When interacting with Copilot, craft thoughtful prompts. Be specific about requirements and provide examples when possible to guide Copilot towards desired outcomes.

* **Stay Informed:** Keep up-to-date with Copilot's features and best practices by referring to the [official documentation](https://docs.github.com/en/copilot/using-github-copilot).

## 🔄 Model Context Protocol (MCP) Integration

The Model Context Protocol (MCP) enhances AI-assisted development by providing additional context to AI models like GitHub Copilot. This repository integrates with several MCP servers that can be leveraged during AL development:

### Available MCP Servers

* **Playwright MCP**: For browser automation and testing of Business Central web client interactions.

* **Context7 MCP**: For enhanced context-aware AI responses, particularly useful when developing complex AL extensions with intricate dependencies and business rules.

* **Sequential Thinking MCP**: For breaking down complex AL programming problems into sequential steps, especially helpful for challenging business logic or report designs.

### Benefits for AL Development

* **Enhanced Context Understanding**: MCP helps Copilot better understand AL syntax, Business Central object types, and common patterns.
* **Improved Suggestions**: Get more accurate code suggestions that follow AL best practices and Business Central development guidelines.
* **Sequential Problem Solving**: Break down complex business processes into manageable implementation steps.

---

By following these guidelines, you help maintain the quality and integrity of the codebase. Thank you for your contributions!