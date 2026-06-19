# Mermaid Diagram Cheat Sheet

---

## 1. Flowchart

```mermaid
flowchart TD
    A[Start] --> B{Decision?}
    B -- Yes --> C[Do Something]
    B -- No --> D[Do Something Else]
    C --> E[End]
    D --> E
```

**Syntax Tips:**
- `flowchart TD` — top-down; use `LR` for left-right, `BT` for bottom-top, `RL` for right-left
- `[Text]` — rectangle, `(Text)` — rounded, `{Text}` — diamond, `((Text))` — circle
- `-->` — arrow, `---` — line, `-- label -->` — labeled arrow

---

## 2. Sequence Diagram

```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>Bob: Hello Bob!
    Bob-->>Alice: Hi Alice!
    Alice->>Bob: How are you?
    Note over Alice,Bob: A friendly chat
    Bob-->>Alice: Doing great!
```

**Syntax Tips:**
- `->>` — solid arrow, `-->>` — dashed arrow
- `->` — solid line (no arrowhead), `-->` — dashed line
- `Note over A,B:` — note spanning participants
- `activate` / `deactivate` — show activation bars

---

## 3. Class Diagram

```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +makeSound() void
    }
    class Dog {
        +String breed
        +fetch() void
    }
    Animal <|-- Dog : inherits
    class Owner {
        +String name
    }
    Owner "1" --> "0..*" Dog : owns
```

**Syntax Tips:**
- `<|--` inheritance, `*--` composition, `o--` aggregation, `-->` association
- `+` public, `-` private, `#` protected
- `<<interface>>` or `<<abstract>>` for stereotypes

---

## 4. Entity Relationship Diagram

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE_ITEM : contains
    PRODUCT ||--o{ LINE_ITEM : "included in"
    CUSTOMER {
        int key PK
        string name
        string email
    }
    ORDER {
        int id PK
        date created_at
        int customer_id FK
    }
```

**Syntax Tips:**
- `||--o{` — one to zero-or-many, `||--|{` — one to one-or-many, `}o--o{` — many to many
- Attribute syntax: `type name PK/FK`

---

## 5. State Diagram

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Processing : start
    Processing --> Success : done
    Processing --> Error : fail
    Success --> [*]
    Error --> Idle : retry
```

**Syntax Tips:**
- `[*]` — start/end state
- `StateA --> StateB : event` — transition with label
- `state "Description" as alias` — named states
- Use `state X { ... }` for composite/nested states

---

## 6. Gantt Chart

```mermaid
gantt
    title Project Timeline
    dateFormat  YYYY-MM-DD
    section Planning
    Requirements    :done,    req,  2024-01-01, 2024-01-07
    Design          :active,  des,  2024-01-08, 2024-01-14
    section Development
    Backend         :         be,   2024-01-15, 14d
    Frontend        :         fe,   2024-01-22, 10d
    section Launch
    Testing         :crit,    test, after fe, 7d
    Deploy          :crit,    dep,  after test, 2d
```

**Syntax Tips:**
- `dateFormat` sets the input date format
- `done`, `active`, `crit` are task modifiers
- `after taskId` — sets dependency
- Duration: `7d`, `2w`, or explicit end date

---

## 7. Pie Chart

```mermaid
pie title Browser Market Share
    "Chrome"  : 65
    "Safari"  : 19
    "Firefox" : 4
    "Edge"    : 4
    "Other"   : 8
```

**Syntax Tips:**
- `title` is optional
- Values are relative (don't need to sum to 100)

---

## 8. Git Graph

```mermaid
gitGraph
    commit id: "Initial commit"
    commit id: "Add README"
    branch feature/login
    checkout feature/login
    commit id: "Add login form"
    commit id: "Add auth logic"
    checkout main
    merge feature/login id: "Merge login"
    commit id: "Hotfix typo"
```

**Syntax Tips:**
- `branch name` — create branch
- `checkout name` — switch branch
- `merge name` — merge into current branch
- `commit id: "label"` — named commit

---

## 9. Mindmap

```mermaid
mindmap
  root((Mermaid))
    Diagrams
      Flowchart
      Sequence
      Class
    Charts
      Gantt
      Pie
    Other
      Git Graph
      Mindmap
      Timeline
```

**Syntax Tips:**
- Indentation defines the tree hierarchy
- `((text))` — circle root, `[text]` — box, `(text)` — rounded, `{{text}}` — hexagon

---

## 10. Timeline

```mermaid
timeline
    title History of Computing
    1940 : First electronic computers
    1970 : Microprocessors invented
    1980 : Personal computers
         : IBM PC released
    1990 : World Wide Web
    2000 : Smartphones emerge
    2020 : AI revolution
```

**Syntax Tips:**
- Year or label on the left, events on the right with `:`
- Multiple events per time point — just add more `: event` lines

---

## Quick Reference: Common Shapes (Flowchart)

```mermaid
flowchart LR
    A[Rectangle]
    B(Rounded)
    C((Circle))
    D{Diamond}
    E[/Parallelogram/]
    F[\Parallelogram alt\]
    G[[Subroutine]]
    H[(Database)]
    I>Asymmetric]
    A --- B --- C --- D --- E --- F --- G --- H --- I
```

---

## Quick Reference: Link Styles (Flowchart)

```mermaid
flowchart LR
    A -->  B
    C --- D
    E -.-> F
    G ==> H
    I --label--> J
    K -.label.-> L
```

| Syntax       | Meaning                  |
|--------------|--------------------------|
| `-->`        | Arrow                    |
| `---`        | Line (no arrow)          |
| `-.->` / `-.->`| Dotted arrow          |
| `==>`        | Thick arrow              |
| `--text-->`  | Labeled arrow            |
| `o--o`       | Circle ends              |
| `<-->`       | Bidirectional            |
