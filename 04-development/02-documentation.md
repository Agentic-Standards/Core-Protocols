# 03-documentation-guidelines.md

## 1. Documentation Philosophy
*   **Code tells you how, Documentation tells you why.**
*   **Living Documentation**: Documentation should evolve with the codebase.
*   **Audience-Centric**: Tailor documentation to different audiences (developers, users, stakeholders).
*   **Consistency**: Maintain consistent structure, terminology, and formatting.
*   **Accessibility**: Ensure documentation is accessible to all users.

## 2. Documentation Types & Hierarchy
*   **README.md**: Project overview, quick start guide, and key links.
*   **Architecture Documentation**: High-level design, components, and data flow.
*   **Technical Documentation**: API references, database schemas, code structure.
*   **User Guides**: How-to guides, tutorials, and best practices.
*   **Process Documentation**: Development workflows, deployment procedures, troubleshooting.
*   **Decision Records**: Architectural Decision Records (ADRs) for significant choices.

## 3. Format Standards
*   **Markdown**: Standard format for all documentation.
*   **Kebab-case**: All filenames use kebab-case naming convention.
*   **Numbered**: All files must have a prefix index (`01-`, `02-`) to ensure reading order.
*   **UTF-8 Encoding**: All files must use UTF-8 encoding.
*   **Line Length**: Maximum 100 characters per line for readability.
*   **Headings**: Use proper heading hierarchy (H1, H2, H3, etc.).

## 4. Structure Guidelines
*   **Table of Contents**: Include auto-generated TOC for longer documents.
*   **Front Matter**: Include metadata for documentation management.
*   **Sections**: Organize content into logical sections with clear headings.
*   **Code Blocks**: Use appropriate language specification for syntax highlighting.
*   **Lists**: Use bulleted or numbered lists for better readability.
*   **Links**: Use relative links for internal references.

## 5. Diagram Standards
*   **Mermaid.js**: Use **Mermaid.js** for all diagrams for easy maintenance.
*   **Diagram Types**: 
    *   Flowcharts for processes
    *   Sequence diagrams for interactions
    *   Class diagrams for structure
    *   ER diagrams for data models
*   **Static Images**: Avoid static images when possible; use Mermaid or SVG instead.
*   **Alt Text**: Provide descriptive alt text for all diagrams and images.
*   **Legend**: Include legends for complex diagrams.

## 6. Content Guidelines
*   **Clarity**: Write in clear, concise language.
*   **Active Voice**: Prefer active voice over passive voice.
*   **Present Tense**: Use present tense for instructions.
*   **Second Person**: Address the reader as "you".
*   **Consistent Terminology**: Use a glossary for consistent term usage.
*   **Examples**: Include practical examples and use cases.
*   **Versioning**: Document version-specific information clearly.

## 7. API Documentation Standards
*   **OpenAPI/Swagger**: Use OpenAPI specification for REST APIs.
*   **Auto-generation**: Auto-generate API docs from code annotations.
*   **Endpoints**: Document all endpoints with examples.
*   **Parameters**: Clearly define all parameters and their constraints.
*   **Responses**: Document all possible response codes and formats.
*   **Authentication**: Detail authentication methods and requirements.

## 8. Code Documentation
*   **JSDoc/TSDoc**: Use standardized documentation comments for code.
*   **Function Docs**: Document all public functions with parameters and return values.
*   **Class Docs**: Document all public classes with purpose and usage.
*   **Inline Comments**: Use sparingly and explain why, not what.
*   **TODO Comments**: Use standardized TODO comments with issue references.

## 9. Version Control for Documentation
*   **Co-located**: Documentation should live with the code it describes.
*   **Reviewed**: Documentation changes should be part of code reviews.
*   **History**: Maintain documentation history and changelogs.
*   **Branching**: Documentation updates should follow the same branching strategy as code.

## 10. Accessibility Standards
*   **Screen Readers**: Ensure compatibility with screen readers.
*   **Contrast**: Maintain sufficient color contrast.
*   **Structure**: Use proper heading structure for navigation.
*   **Images**: Provide descriptive alt text for all images.
*   **Tables**: Use proper table headers and structure.

## 11. Internationalization
*   **Localization**: Plan for translation and localization.
*   **Cultural Sensitivity**: Consider cultural differences in examples and references.
*   **Date/Time Formats**: Use ISO standard formats or configurable formats.

## 12. Maintenance & Review
*   **Regular Audits**: Schedule regular documentation audits.
*   **Stale Detection**: Identify and update stale documentation.
*   **Feedback Loop**: Provide mechanisms for documentation feedback.
*   **Ownership**: Assign documentation ownership for each component.