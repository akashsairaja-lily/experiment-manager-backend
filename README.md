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

## 3. **Implementation Options**

### 3.1 **For Frontend Engineers: Mock API Implementation**

- Create a mock API server using provided JSON files in `demo/mock/` directory.
- Use **Node.js** and **Express** or **NestJS** for the mock server implementation.
- Mock endpoints should replicate the full functionality and data structure as defined in the OpenAPI specification.

### 3.2 **For Backend/Full Stack Engineers: Database Integration**

Backend developers should implement a fully functional API with database integration.

#### Database Options

#### Implementation Steps
1. Choose your preferred database system
2. Request the appropriate database setup scripts from the interviewer
3. Configure your database connection in `src/config/database.config.ts`
4. Implement the necessary data models and repositories

#### Data Generation and Seeding (Optional)
When implementing a database-backed solution, you have several options for generating and seeding mock data:

1. **Automatic Seeding on Startup**:
   - Implement a service that runs on application startup to check if the database is empty
   - If empty, seed with initial mock data from the JSON files in `demo/mock/`
   - Example approach:
     ```typescript
     // In your app module or a dedicated seeding module
     @Injectable()
     export class DataSeedService implements OnModuleInit {
       async onModuleInit() {
         const isEmpty = await this.checkIfDbIsEmpty();
         if (isEmpty) {
           await this.seedDatabase();
         }
       }
     }
     ```

2. **Database Migrations**:
   - Create migration scripts that not only set up the schema but also populate with sample data
   - This ensures consistent data across all development environments
   - For TypeORM, place these in a migrations directory with up/down methods

3. **Manual Seeding via CLI**:
   - Implement a CLI command to seed the database on demand
   - Useful for testing and development environments
   - Example command: `npm run seed:db`

4. **Hybrid Approach**:
   - Use migrations for schema changes
   - Implement a separate seeding mechanism for test data
   - Allow different data sets for different environments (dev, test, staging)

Regardless of the approach chosen, ensure that the seeded data matches the structure and relationships expected by the API specification.

---

## 4. **Technical Stack**

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
- **TypeORM/Mongoose**: For database ORM (Backend/Full Stack implementation)

---

## 5. **Pull Request and Branching Standards**

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
