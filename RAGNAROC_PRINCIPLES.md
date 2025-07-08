# **The Constitution of Project Ragnaroc**

This document is the permanent expression of our development philosophy and ethical covenant. All development is measured against these principles. They are requirements.

### **I. The Ragnaroc Covenant**

We build for a better future. Technology inherits the values of its creators, so we choose to build a platform that is a force for empowerment and shared prosperity. Our work will be a testament to a constructive partnership between human and artificial intelligence, aligned to augment human intellect and potential.

## **II. Core Mission**

1. **The CPG is the Source of Truth:** Our primary technical mission is to build the most comprehensive and performant Code Property Graph (CPG) possible. The CPG is the "world model" from which all intelligence and agentic capability is derived. CPG+AST+CFG+DFG++
2. **We Build an Intelligent Repository:** We are not building an agent; we are building the intelligent information backbone that makes true agency possible. Our focus is on the platform.

### **III. The Tiered Computational Ethos**

To ensure reliability, performance, and trust, all computation must adhere to the following hierarchy, preferring the lowest tier possible.

* **Tier 1 (Deterministic):** Computable graph traversals, structural analysis. Fastest, most reliable, most trusted. **Always the preferred approach.**  
* **Tier 2 (Local AI - Embeddings/Classifiers):** Local, efficient models for semantic search and classification.  
* **Tier 3 (Local AI - Generative):** Smaller, local generative models for constrained tasks.  
* **Tier 4 (External AI - Expensive & Optional):** Powerful, external APIs. **Must always be optional and explicitly enabled by the user.** The system must be fully functional without it.

### **IV. The Engineering Mandates**

1. **Test-Driven Implementation:** Introduce all new logic via a failing test case first. The test suite is an executable specification of the system.  
2. **Architect for Enterprise Scale:** Design for high-concurrency and horizontal scalability. This mandates stateless services, asynchronous processing (Celery), and CQRS.  
3. **"Never Delete" - History is Sacred:** The CPG is an append-only, version-aware structure. Old nodes are marked inactive; never destroyed.  
4. **Automated Quality is Enforced:** All code must pass pre-commit hooks (black, isort, linters).  
5. **The User is in Control:** Agentic features default to a "human-in-the-loop" workflow, requiring explicit user approval for actions.

Code or architectural proposals that violate these principles will be rejected in favor of a compliant alternative.

### **1. Dependency Injection is the (other) Source of Truth.**

What it means: All shared services (GraphReader, GitService, etc.) are instantiated and managed exclusively by the DI container (containers.py).  
Why it matters: This ensures a single, explicit, and testable application graph. It eliminates hidden state and implicit dependencies, making the system predictable and maintainable. Manual instantiation of services in application code is strictly forbidden.

### **2. Test-Driven Implementation is Mandatory.**

What it means: All new features or logic modifications will be introduced via the creation of a failing test case first. The code implementation follows the test.  
Why it matters: The test suite is not an afterthought; it is an executable specification of the system's behavior. This practice forces us to design for testability from the outset and guarantees that our logic is verifiably correct.

### **3. Leverage the Framework First.**
**What it means:** Before writing custom infrastructure code (e.g., config managers, task dispatchers), we will always prefer the built-in solutions provided by our core frameworks like FastAPI, dependency-injector, and Celery.
**Why it matters:** Frameworks provide tested, documented, and idiomatic solutions. Using them reduces our maintenance burden, makes the code easier for new developers to understand, and prevents us from reinventing the wheel. Custom infrastructure should only be built when a framework's capabilities are insufficient for our specific, advanced needs.

### 4. Architect for Enterprise Scale.
**What it means:** The system must be designed for high-concurrency, horizontally-scalable deployments. This is not an optional feature but a core design constraint.

**Why it matters:** To serve 10k+ developers, the architecture must support independent scaling of its components. This mandates:

* **Command Query Responsibility Segregation (CQRS):** A strict separation between read-side components (GraphReader) and write-side components (GraphWriter) to allow query-serving and data-ingestion workloads to be scaled independently.
* **Stateless Services:** API endpoints and business logic services must be designed to be stateless wherever possible, enabling them to be easily replicated behind a load balancer without shared session state.
* **Asynchronous & Parallel Processing:** Computationally expensive work (e.g., file parsing, AI analysis) WILL be offloaded to a distributed task queue to ensure the user-facing API remains responsive and that ingestion can be parallelized across many workers.

### **5. Mocking via Container Overrides Only.**

What it means: Testing of services and API endpoints will use the container.override() pattern provided by our DI framework.  
Why it matters: This ensures that our tests are clean, robust, and reflect the true application structure. It prevents brittle tests that break on minor refactoring. The use of @patch for mocking container-managed services is forbidden as it breaks encapsulation.

### **6. Data Contracts are Immutable.**

What it means: Pydantic models defined in ragnaroc/schemas.py are the strict, canonical contracts for all data structures. All services and endpoints must accept and return these models.  
Why it matters: This enforces type safety at the boundaries of our system, eliminates ambiguity, and makes the flow of data explicit and predictable.

### **7. "Never Delete" - History is Sacred.**

What it means: The knowledge graph is an append-only, version-aware structure. We do not destroy historical information.  
Why it matters: When code changes, old nodes are marked as is_active=False and new nodes are created. This preserves the complete, queryable history of the codebase, enabling powerful features like semantic diffing and historical analysis. Data is a valuable asset; we do not throw it away.

### **8. Adherence to SRP and DRY.**

What it means: The Single Responsibility Principle and Don't Repeat Yourself. Each module, class, and function will have a single, well-defined responsibility. Common logic will be abstracted into reusable components.  
Why it matters: This is fundamental to clean architecture. It leads to code that is easier to understand, test, and maintain.

### **9. Automated Quality is Enforced.**

What it means: All committed code must be compliant with the project's pre-commit hooks, including black for formatting, isort for import sorting, and linters.  
Why it matters: The machine is better at enforcing style and catching simple errors than we are. Automation ensures a consistent, high-quality baseline for all code entering the repository, freeing up human review cycles for more important architectural concerns.
