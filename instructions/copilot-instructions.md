# Contributing to the Agent Setup Repository

Welcome! This repository is a comprehensive collection of GitHub Copilot instructions and configurations for different project structures. It serves as a central resource for teams looking to standardize their approach to AI-assisted development. We appreciate your contributions and ask that you follow the guidelines below to maintain quality and consistency.

## 📌 Content Standards

### ✅ Required Before Each Contribution

Before submitting a contribution, please ensure the following:

* **Format Markdown:** Ensure consistent formatting in markdown files.
* **Check Links:** Verify that all links in documentation are valid and accessible.
* **Review Examples:** Ensure that examples are clear, concise, and follow best practices.

### 🔄 Contribution Flow

* **Fork Repository:** Create your own fork of the repository.
* **Create Branch:** Make your changes in a new branch.
* **Submit PR:** Open a pull request with a clear description of your changes.
* **Address Feedback:** Respond to review comments and make necessary updates.

## 📁 Repository Structure

* `instructions/`: Contains template instructions for different project structures.
  * `nextjs/`: GitHub Copilot instructions specifically tailored for Next.js projects.
  * `rust/`: GitHub Copilot instructions specifically tailored for Rust projects.
  * `template_for_agents.md`: General template for AI agent instructions.
  * Additional language/framework-specific directories (as they are added).
* `mcp/`: Model Context Protocol configurations.
  * `mcpServers.json`: Configuration for different MCP servers.
* `README.md`: Overview of the repository and usage instructions.

## 🛠️ Key Guidelines

1. **Template Consistency**

   * Maintain a consistent structure across all instruction templates.
   * Use similar headings, emoji usage, and formatting styles.
   * Include sections for code standards, repository structure, key guidelines, and Copilot usage.

2. **Documentation Quality**

   * Write clear, concise, and accurate documentation.
   * Include examples where appropriate to illustrate concepts.
   * Use proper markdown formatting for readability.

3. **Framework-Specific Guidelines**

   * When creating instructions for specific frameworks/languages, highlight best practices unique to that technology.
   * Include relevant commands, tools, and workflows.
   * Reference official documentation where appropriate.

4. **MCP Configuration**

   * Ensure MCP server configurations are up-to-date and functional.
   * Include clear instructions for setup and integration.
   * Document the benefits and use cases of each MCP server.

5. **Accessibility**

   * Make instructions accessible to users with varying levels of experience.
   * Explain technical concepts clearly without assuming advanced knowledge.
   * Provide links to additional resources for deeper learning.

## 🤖 Using GitHub Copilot as a Coding Agent

To effectively leverage GitHub Copilot in this repository, please adhere to the following best practices:

### 🧩 Assigning Tasks to Copilot

* **Well-Scoped Issues:** Ensure that issues assigned to Copilot are clear and well-defined. Include:

  * A concise description of the problem or task.
  * Acceptance criteria outlining what a successful solution entails.
  * Specific files or areas of the repository that need to be addressed.

* **Appropriate Tasks:** Assign tasks that are suitable for Copilot, such as:

  * Creating new instruction templates for additional frameworks/languages.
  * Updating existing templates with new best practices.
  * Enhancing documentation clarity and completeness.
  * Improving formatting and structure.
  * Adding examples to illustrate concepts.

Avoid assigning complex, ambiguous, or sensitive tasks that require deep domain knowledge or involve critical organizational policies.

### 💬 Iterating on Pull Requests

* **Reviewing Copilot's Work:** Treat Copilot-generated pull requests as you would those from human contributors. Review the content thoroughly and provide feedback through comments.

* **Batching Comments:** If you have multiple comments, batch them using GitHub's "Start a review" feature. This approach allows Copilot to process all feedback collectively, leading to more coherent updates.

### 🛡️ Security and Best Practices

* **Content Review:** Always review Copilot's contributions to ensure they meet quality standards and do not introduce misinformation or inappropriate content.

* **Prompt Engineering:** When interacting with Copilot, craft thoughtful prompts. Be specific about requirements and provide examples when possible to guide Copilot towards desired outcomes.

* **Stay Informed:** Keep up-to-date with Copilot's features and best practices by referring to the [official documentation](https://docs.github.com/en/copilot/using-github-copilot).

## 🔄 Model Context Protocol (MCP) Integration

The Model Context Protocol (MCP) enhances AI-assisted development by providing additional context to AI models like GitHub Copilot. This repository includes configurations for several MCP servers:

### Available MCP Servers

* **Playwright MCP**: For browser automation and testing of web applications, useful for examples and demonstrations.

* **Context7 MCP**: For enhanced context-aware AI responses, particularly valuable when working with complex documentation structures.

* **Sequential Thinking MCP**: For breaking down complex problems into sequential steps, especially helpful when creating detailed instruction templates.

### Benefits for Repository Development

* **Enhanced Context Understanding**: MCP helps Copilot better understand the structure and purpose of instruction templates.
* **Improved Suggestions**: Get more accurate content suggestions that follow the established patterns and styles.
* **Sequential Problem Solving**: Break down complex documentation tasks into manageable steps.

---

By following these guidelines, you help maintain the quality and consistency of this repository. Thank you for your contributions!