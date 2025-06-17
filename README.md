# Product Type Review API - Backend Implementation

This repository implements a backend API for the **Product Type Review / Control Flow** feature, which supports reviewing, filtering, and approving products in the context of experiments.

---

## 1. **API Overview**

The backend provides endpoints for:
- Getting and filtering experiments
- Retrieving and filtering products with pagination
- Approving products
- Getting product type distributions
- Marking experiments as complete

### API Structure
See the OpenAPI specification in `demo/swagger.yaml` for detailed API documentation.

---

## 2. **Backend Implementation Requirements**

### Core Requirements
- You must implement a mock API server that follows the OpenAPI specification.
- Your implementation must support all the functionality needed by the frontend:
    - Experiment listing and filtering
    - Product filtering, pagination, and sorting
    - Product approval
    - Product type statistics
    - Experiment completion

### Data Models
The API works with the following core data models:
- **Experiment**: Contains experiment metadata and status
- **Product**: Represents product data with approval status
- **ProductType**: Contains product type statistics and distributions

---

## 3. **Backend Mocking Requirements**

- You must **hardcode the API responses**.
- Use **Node.js** and **Express** for the mock server implementation.
- Your mock endpoints must replicate the full functionality and data structure expected by the frontend (products, experiments, filters, approval actions, etc.).
- No real database integration is required—just return hardcoded/mock data for all endpoints.
- If you use **NestJS** (a progressive Node.js framework), this will be considered a **bonus point** as it demonstrates knowledge of scalable backend architecture and TypeScript-first server development.

---

## 4. **Mocking Guidance**
To fully mock the backend for this flow:
- All experiment, product, and filter data must be mocked.
- Endpoints for product fetching, approving, and status updates must return realistic payloads.
- Support search, filtering, pagination, and status change flows in the mock server.
- Ensure responses are consistent with the OpenAPI specification.

---

## 5. **Technical Stack**

### Core Stack

- **TypeScript**: All code should be written in TypeScript.
- **Node.js**: Runtime environment for the backend.
- **Express**: Web framework for creating API endpoints.

### Additional/Bonus Tools

- **NestJS**: A progressive Node.js framework for building efficient and scalable server-side applications (bonus).
- **Lodash**: Utility library for common JS data operations.
- **Jest**: For unit and integration testing of API endpoints.
- **Swagger/OpenAPI**: For API documentation.
- **Prettier & ESLint**: For code linting and formatting.

---

## 6. **Pull Request and Branching Standards**

**It is mandatory to follow these PR and branch management standards for this task:**

- **Do NOT merge any code directly into the `main` branch.**
- Always work on feature branches.
- Use the following branching model:
    - Create a main parent feature branch:
      e.g., `feature/backend-mock` or `feature/api-endpoints`
    - For each new story, bugfix, or sub-feature, create a story branch on top of the parent feature branch:
      e.g., `story/experiments-api`, `story/products-api`
    - Raise PRs *from story branch to the parent feature branch*, never to `main`.
    - Merge each story/feature one at a time to the parent feature branch.
    - Use clear and descriptive PR names, referencing the feature or issue you are working on.

**Example flow:**
1. Create `feature/backend-mock`.
2. Create `story/products-api` from `feature/backend-mock`.
3. Implement the products API mock, then raise a PR from `story/products-api` to `feature/backend-mock`.
4. Repeat for other features or stories.
5. Only after all review cycles and QA merge the `feature/backend-mock` branch into `main` (if authorized).

---

## 7. **Full Stack Implementation (Optional)**

**If you are a full-stack engineer, we encourage you to implement a complete solution:**

- **Database Integration**: Instead of hardcoded responses, implement a proper database solution:
    - Use a relational database (PostgreSQL, MySQL) or NoSQL solution (MongoDB) based on your expertise
    - Implement proper data models with referential integrity between experiments and products
    - Create seed scripts to populate test data

- **Advanced Features**:
    - Implement proper data validation and error handling
    - Add authentication and authorization mechanisms
    - Include database migrations for schema changes
    - Set up proper environment configuration

- **Testing & Documentation**:
    - Write integration tests that test database operations
    - Document your database schema and relationships
    - Add API documentation that reflects your actual implementation

This full implementation is optional and goes beyond the core requirements. Even if choosing this path, ensure you follow the branching strategy outlined in section 6.

---

## 8. **Kick-start Project**

- **To save your time, we have created a sample project to kick start your work.**
  You do not need to spend time configuring the environment or setting up boilerplate code—just focus on implementing the required functionality and tasks as described.
- Please use the provided structure and dependencies as your base.

---


## 9. **Additional Notes**

- A **recorded video** is attached to this task—please use it as a reference for expected API behaviors and edge cases.
- Use the simple UI design shown in the video to design your database tables according to the functionalities demonstrated.
- Make sure your implementation handles the flows and behaviors demonstrated in the video.
- If anything about the API requirements is unclear, refer to the video for clarification before reaching out.

---

## 10. **Summary**
**Key API endpoints** include:
- `/experiments` - For listing and retrieving experiments
- `/products` - For filtered product retrieval with pagination
- `/products/approve` - For approving one or multiple products
- `/product-types` - For product type statistics
- `/experiment/{experimentId}/complete` - For marking experiments complete

---
