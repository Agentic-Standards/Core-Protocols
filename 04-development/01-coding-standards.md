# 01-coding-standards.md

## 1. General Principles
*   **DRY**: Don't Repeat Yourself - Eliminate redundant code and logic.
*   **KISS**: Keep It Simple, Stupid - Favor simplicity over complexity.
*   **YAGNI**: You Aren't Gonna Need It - Implement only what is needed.
*   **Clean Code**: Variables must be descriptive (e.g., `ideaCreationDate` not `d`).
*   **SOLID Principles**: 
    *   Single Responsibility Principle
    *   Open/Closed Principle
    *   Liskov Substitution Principle
    *   Interface Segregation Principle
    *   Dependency Inversion Principle
*   **Boy Scout Rule**: Leave the code cleaner than you found it.

## 2. Clean Architecture Compliance
*   **Separation of Concerns**: Clearly separate business logic from presentation and data layers.
*   **Dependency Rule**: Inner layers should not depend on outer layers.
*   **Entities**: Business objects that encapsulate enterprise-wide business rules.
*   **Use Cases**: Application-specific business rules.
*   **Interface Adapters**: Convert data from convenient formats for use cases and entities.
*   **Frameworks & Drivers**: Outermost layer with databases, UI, web frameworks.

## 3. 12-Factor App Compliance
*   **Codebase**: One codebase tracked in revision control, many deploys.
*   **Dependencies**: Explicitly declare and isolate dependencies.
*   **Config**: Store config in the environment.
*   **Backing Services**: Treat backing services as attached resources.
*   **Build, Release, Run**: Strictly separate build and run stages.
*   **Processes**: Execute the app as one or more stateless processes.
*   **Port Binding**: Export services via port binding.
*   **Concurrency**: Scale out via the process model.
*   **Disposability**: Maximize robustness with fast startup and graceful shutdown.
*   **Dev/Prod Parity**: Keep development, staging, and production as similar as possible.
*   **Logs**: Treat logs as event streams.
*   **Admin Processes**: Run admin/management tasks as one-off processes.

## 4. TypeScript Guidelines
*   **Strict Mode**: Enabled with `strict: true` in tsconfig.json.
*   **Interfaces**: Use `interface` over `type` for object definitions.
*   **Types**: Use `type` for unions, primitives, and tuples.
*   **Any**: Avoid `any` at all costs. Use `unknown` or specific types.
*   **Enums**: Prefer union types over enums for better compatibility.
*   **Null/Undefined**: Use strict null checks and explicit typing.
*   **Generics**: Leverage generics for reusable, type-safe code.
*   **Modules**: Use ES modules over namespaces.
*   **Async/Await**: Prefer async/await over callbacks.

## 5. React/Next.js Patterns
*   **Functional Components**: Arrow functions preferred over class components.
*   **Hooks**: Custom hooks for logic abstraction, components for UI.
*   **Folder Structure**: Feature-based organization with clear separation.
*   **Component Composition**: Favor composition over inheritance.
*   **State Management**: Use appropriate state management (local, context, Redux, etc.).
*   **Performance**: Implement memoization and lazy loading where appropriate.
*   **Testing**: Write unit and integration tests for components.
*   **Accessibility**: Ensure WCAG compliance and proper semantic HTML.
*   **SEO**: Implement proper meta tags and structured data.

## 6. API Design Standards
*   **RESTful Principles**: Follow REST conventions for API design.
*   **Versioning**: API versioning in URL path (e.g., `/api/v1/resource`).
*   **Status Codes**: Use appropriate HTTP status codes.
*   **Error Handling**: Consistent error response format.
*   **Pagination**: Standardized pagination approach.
*   **Rate Limiting**: Implement rate limiting for API protection.
*   **Documentation**: Auto-generated API documentation with OpenAPI/Swagger.

## 7. Security Standards
*   **Input Validation**: Validate all inputs on both client and server.
*   **Authentication**: Implement secure authentication mechanisms.
*   **Authorization**: Role-based and attribute-based access control.
*   **Data Protection**: Encrypt sensitive data at rest and in transit.
*   **OWASP Compliance**: Follow OWASP Top 10 security recommendations.
*   **Security Headers**: Implement proper HTTP security headers.
*   **Dependency Scanning**: Regular scanning for vulnerable dependencies.

## 8. Performance Standards
*   **Bundle Optimization**: Minimize bundle size through tree-shaking and code splitting.
*   **Caching**: Implement appropriate caching strategies.
*   **Lazy Loading**: Load resources only when needed.
*   **Image Optimization**: Use modern image formats and responsive images.
*   **Database Queries**: Optimize database queries and implement indexing.
*   **Monitoring**: Implement performance monitoring and alerting.

## 9. Testing Standards
*   **Test Pyramid**: Unit tests, integration tests, and end-to-end tests.
*   **Code Coverage**: Maintain minimum code coverage thresholds.
*   **Test Isolation**: Tests should be independent and isolated.
*   **Mocking**: Use appropriate mocking strategies for dependencies.
*   **Continuous Testing**: Integrate testing into CI/CD pipeline.
*   **Test Data Management**: Proper management of test data and environments.

## 10. Documentation Standards
*   **Inline Comments**: Explain why, not what.
*   **Function Documentation**: Use JSDoc/TSDoc for all public functions.
*   **Architecture Decisions**: Record architectural decision records (ADRs).
*   **API Documentation**: Auto-generated and manually curated API docs.
*   **Deployment Guides**: Clear deployment and rollback procedures.