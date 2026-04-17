```mermaid
flowchart TB

    subgraph Presentation Layer
        UI[User Interface]
        API[API Controllers]
    end

    subgraph Business Logic Layer
        FACADE[Facade]
        SERVICES[Services]

        subgraph Domain Models
            USER[User]
            PLACE[Place]
            AMENITY[Amenity]
            REVIEW[Review]
        end
    end

    subgraph Persistence Layer
        REPO[Repositories]
        DB[(Database)]
    end

    UI --> FACADE
    API --> FACADE

    FACADE --> SERVICES

    SERVICES --> USER
    SERVICES --> PLACE
    SERVICES --> AMENITY
    SERVICES --> REVIEW

    SERVICES --> REPO
    REPO --> DB
``
