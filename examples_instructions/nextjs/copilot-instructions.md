# Contributing to the Next.js Repository

Welcome! This repository is a Next.js-based application responsible for ingesting and recording metered usage data for GitHub through provided APIs. It utilizes TypeScript and adheres to modern React best practices. We appreciate your contributions and ask that you follow the guidelines below to maintain code quality and consistency.

## 📌 Code Standards

### ✅ Required Before Each Commit

Before committing any changes, please ensure the following:

* **Format Code:** Run `npm run format` to format your code using Prettier.
* **Lint:** Run `npm run lint` to identify and fix linting issues with ESLint.
* **Type Check:** Run `npm run type-check` to ensure there are no TypeScript errors.

### 🔄 Development Flow

* **Install Dependencies:** `npm install`
* **Start Development Server:** `npm run dev`
* **Build Project:** `npm run build`
* **Run Tests:** `npm run test`
* **Full CI Check:** `npm run ci` (includes format, lint, type-check, test, and build)

## 📁 Repository Structure

* `app/`: Next.js App Router structure (routes/pages).
* `components/`: Reusable React components.
* `lib/`: Utility functions and shared logic.
* `hooks/`: Custom React hooks.
* `services/`: API calls and integration logic (including GitHub API interactions).
* `types/`: TypeScript definitions and interfaces.
* `config/`: Application-wide configuration files (environment variables, defaults).
* `scripts/`: Build scripts and automation tasks.
* `styles/`: Global CSS and design tokens.
* `public/`: Static assets (images, fonts, etc.).
* `tests/`: Unit and integration tests.
* `docs/`: Documentation and developer guidelines.

## 🛠️ Key Guidelines

1. **Next.js Best Practices**

   * Utilize server components, server actions, and client components appropriately.
   * Prefer `use server` for server-side actions when feasible.

2. **React and TypeScript**

   * Write functional React components using TypeScript.
   * Ensure strong type safety and explicit interfaces.
   * Keep components small, focused, and reusable.

3. **State and Data Management**

   * Prefer React Server Components and Next.js built-in fetching methods (`fetch`, SWR) over complex client-side solutions.
   * Use dependency injection patterns and context providers where appropriate.

4. **Testing**

   * Write unit and integration tests for all significant functionality using Jest and React Testing Library.
   * Use descriptive test names and follow a clear, consistent testing structure.

5. **Documentation**

   * Clearly document public APIs, utility functions, and complex logic.
   * Update or add to the `docs/` folder when introducing new features or major changes.

6. **Performance**

   * Optimize images and static assets using Next.js built-in optimization.
   * Be mindful of loading times; use dynamic imports (`next/dynamic`) for heavy components.

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
  * Improving accessibility.
  * Addressing technical debt.

Avoid assigning complex, ambiguous, or sensitive tasks that require deep domain knowledge or involve critical business logic.

### 💬 Iterating on Pull Requests

* **Reviewing Copilot's Work:** Treat Copilot-generated pull requests as you would those from human contributors. Review the code thoroughly and provide feedback through comments.

* **Batching Comments:** If you have multiple comments, batch them using GitHub's "Start a review" feature. This approach allows Copilot to process all feedback collectively, leading to more coherent updates.

### 🛡️ Security and Best Practices

* **Code Review:** Always review and test Copilot's code suggestions to ensure they meet security standards and do not introduce vulnerabilities.

* **Prompt Engineering:** When interacting with Copilot, craft thoughtful prompts. Be specific about requirements and provide examples when possible to guide Copilot towards desired outcomes.

* **Stay Informed:** Keep up-to-date with Copilot's features and best practices by referring to the [official documentation](https://docs.github.com/en/copilot/using-github-copilot).

---

By following these guidelines, you help maintain the quality and integrity of the codebase. Thank you for your contributions!
