# **Contributing to Ragnaroc**

Thank you for your interest in contributing to Ragnaroc! This project is built on a foundation of architectural rigor and a unique hybrid development model. To maintain our velocity and quality, we adhere to a strict set of guidelines. This document outlines that process.

## **Our Core Philosophy**

Before you begin, please familiarize yourself with our core engineering mandates, which are the constitution of this project:

* **RAGNAROC_PRINCIPLES.md**: The permanent expression of our development philosophy.  
* **RAGNAROC_PROMPT.md**: The master directive for all AI-driven development.

All contributions will be measured against these principles.

## **The Development Workflow**

All development in this project follows a precise, story-driven, test-first methodology. We do not accept unsolicited code pushes. The process is as follows:

1. **Create an Issue / Define a Story:** All work must begin with a well-defined objective. This can be a new feature (a "Story"), a bug fix, or a refactoring task. The issue must clearly state the goal and the acceptance criteria.  
2. **Write a Failing Test:** In accordance with our "Test-Driven Implementation is Mandatory" principle, the first code you write will be a test that fails because the feature or fix does not yet exist. This test must be added to the appropriate file in the tests/ directory.  
3. **Implement the Code:** Write the minimum amount of application code necessary to make the failing test pass. Your implementation must adhere to all principles outlined in our guiding documents, especially regarding dependency injection, data contracts, and leveraging existing frameworks.  
4. **Ensure All Tests Pass:** Run the entire test suite to ensure your changes have not introduced any regressions.  
5. **Submit a Pull Request:** Create a pull request that includes:  
   * A link to the issue/story it resolves.  
   * The new application code.  
   * The new test code that validates the implementation.

## **Definition of Done**

A contribution is considered "done" and ready for merge only when it meets all of the following criteria:

* **Adherence to Principles:** The code fully complies with all mandates in RAGNAROC_PRINCIPLES.md.  
* **Test Coverage:** The new functionality is accompanied by passing unit and/or integration tests that prove its correctness.  
* **CI/CD Pipeline Passes:** All automated quality checks, linting, and tests in the CI/CD pipeline must pass.  
* **Architecturally Sound:** The change does not introduce technical debt or violate the established architectural patterns of the system (e.g., CQRS, stateless services).

## **Special Guidelines for AI Contributors**

As a project that leverages AI as a core development partner, we have specific protocols for AI-driven contributions:

1. **Master Directive Adherence:** All AI-generated code is bound by the RAGNAROC_PROMPT.md. The AI partner is expected to proactively identify and reject requests that would violate the project's mandates.  
2. **Justification is Required:** AI contributions must be accompanied by a clear explanation of the "why" behind the implementation, referencing the specific stories and principles that guided its decisions.  
3. **YAPS Analysis:** Before finalizing a file, the AI partner will perform a "Yet Another Percentage Score" (YAPS) analysis to audit the code against all project requirements. The goal is a 100% score, indicating full compliance and completion.  
4. **Human-in-the-Loop:** The human project lead has the final authority on all architectural decisions and pull request merges. The AI's role is to provide superior, compliant, and well-reasoned proposals, not to operate with full autonomy.