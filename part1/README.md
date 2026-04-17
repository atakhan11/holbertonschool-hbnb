## High-Level Package Diagram

```mermaid
graph TD
    Presentation -->|via Facade| BusinessLogic
    BusinessLogic -->|via Facade| Persistence
```
