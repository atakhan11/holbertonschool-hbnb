```mermaid
sequenceDiagram
participant User
participant API
participant Facade
participant UserService
participant DB

User->>API: POST /users (register)
API->>Facade: create_user(data)
Facade->>UserService: validate_and_create_user(data)
UserService->>DB: insert user
DB-->>UserService: user saved (id)
UserService-->>Facade: user created
Facade-->>API: success response
API-->>User: 201 Created
```


```mermaid
sequenceDiagram
participant User
participant API
participant Facade
participant PlaceService
participant DB

User->>API: POST /places
API->>Facade: create_place(data)
Facade->>PlaceService: validate_and_create_place(data)
PlaceService->>DB: insert place
DB-->>PlaceService: place saved
PlaceService-->>Facade: success
Facade-->>API: response
API-->>User: 201 Created
```


```mermaid
sequenceDiagram
participant User
participant API
participant Facade
participant ReviewService
participant DB

User->>API: POST /reviews
API->>Facade: create_review(data)
Facade->>ReviewService: validate_and_create_review(data)
ReviewService->>DB: insert review
DB-->>ReviewService: saved
ReviewService-->>Facade: success
Facade-->>API: response
API-->>User: 201 Created
```

```mermaid
sequenceDiagram
participant User
participant API
participant Facade
participant PlaceService
participant DB

User->>API: GET /places?filters
API->>Facade: get_places(filters)
Facade->>PlaceService: fetch_places(filters)
PlaceService->>DB: query places
DB-->>PlaceService: list of places
PlaceService-->>Facade: data
Facade-->>API: response
API-->>User: 200 OK (list of places)
```



## Explanation

### 1. User Registration
User sends registration data → system validates → user stored in database → success response returned.

### 2. Place Creation
Authenticated user creates a place → service validates data → place saved in database.

### 3. Review Submission
User submits review for a place → review service validates and stores it.

### 4. Fetch Places
User requests list of places → system queries database → returns filtered results.

---

## Flow Summary

All requests follow the same architecture:

User → API → Facade → Service → Database → Response
