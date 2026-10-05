# Causal Decision Diagram: COVID-19 Facility Safety

This Causal Decision Diagram (CDD) replicates the structure provided in the example image, illustrating the causal chains for deciding on opening a building and keeping people safe from a pandemic.

```mermaid
flowchart LR
    %% Styling definitions to match the visual groupings
    classDef lever fill:#fae6d1,stroke:#333,stroke-width:2px,color:#000;
    classDef intermediate fill:#c85250,stroke:#333,stroke-width:2px,color:#fff;
    classDef external fill:#f7931e,stroke:#333,stroke-width:2px,color:#000;
    classDef outcome fill:#a8cce4,stroke:#333,stroke-width:2px,color:#000;
    classDef key fill:#fff,stroke:#333,stroke-width:2px,color:#000;
    
    %% Asset icons (using unicode or text representations since mermaid doesn't support complex custom shapes easily inside nodes without HTML which can be brittle)
    %% [EM] = Econometric/financial model (Square)
    %% [ML] = Machine learning model (Triangle)
    %% [CFD] = CFD simulation (U-shape)
    %% [BM] = Behavioral/psych model (Smiley)
    %% [MM] = Medical model/RCT results (Heart)
    %% [AM] = Agent-based model (Cross)
    %% [OD] = Observation/data capture (Eye)

    %% Subgraphs for categorization
    subgraph Levers [Decision levers (choices of actions)]
        direction TB
        L1["Occupancy <br/> schedule(s)"]:::lever
        L2["Investment <br/> in facility <br/> modification"]:::lever
        L3["Investment <br/> in HVAC"]:::lever
        L4["Investment <br/> in distancing"]:::lever
        L5["Investment in <br/> mask <br/> compliance"]:::lever
        L6["Investment <br/> in safety <br/> marketing"]:::lever
        L7["Pricing"]:::lever
    end

    subgraph Externals [Externals (context, things we can't control)]
        direction TB
        E1["Building shape"]:::external
        E2["Local infection <br/> rate"]:::external
        E3["Demographics <br/> of facility <br/> population(s)"]:::external
        E4["Virus infection <br/> behavior"]:::external
        E5["Regulatory <br/> constraints"]:::external
        E6["Business <br/> constraints"]:::external
    end
    
    %% Note pointing to observation icons in Externals
    MonitorNote["Monitor frequently, may change over time"]:::key
    MonitorNote -.-> E2
    MonitorNote -.-> E4
    MonitorNote -.-> E5

    subgraph Intermediates [Intermediates and dependency links]
        direction TB
        I1["Occupancy <br/> level"]:::intermediate
        I2["Human movement <br/> patterns"]:::intermediate
        I3["Movement of <br/> susceptible people"]:::intermediate
        I4["Social <br/> distancing <br/> compliance rate"]:::intermediate
        I5["Movement of <br/> infectious <br/> person(s)"]:::intermediate
        I6["Facility virus <br/> exposure patterns <br/> (including hot spots)"]:::intermediate
        I7["Mask compliance <br/> rate"]:::intermediate
        I8["Virus movement <br/> patterns"]:::intermediate
        I9["Demand for <br/> our products/ <br/> services"]:::intermediate
        I10["Awareness of our <br/> commitment to <br/> Covid-19 safety"]:::intermediate
        I11["Virus shed rate"]:::intermediate
        I12["Population <br/> susceptibility"]:::intermediate
        I13["Population <br/> infection rate"]:::intermediate
    end

    subgraph Outcomes [Outcomes]
        direction TB
        O1["Future <br/> illnesses <br/> (goal: fewer)"]:::outcome
        O2["Future <br/> deaths <br/> (goal: fewer)"]:::outcome
        O3["Profitability"]:::outcome
    end
    
    subgraph KeyBox [Key to decision assets]
        direction TB
        K1["[EM] Econometric/ <br/> financial model"]:::key
        K2["[ML] Machine learning <br/> model"]:::key
        K3["[CFD] CFD simulation"]:::key
        K4["[BM] Behavioral/psych <br/> model"]:::key
        K5["[MM] Medical model/ <br/> RCT results"]:::key
        K6["[AM] Agent-based (human <br/> movement) model"]:::key
        K7["[OD] Observation/data <br/> capture"]:::key
    end

    %% Dependency Links (Causal Chains)
    
    %% Levers to Intermediates
    L1 -->|[EM]| I1
    L2 --> I2
    L3 --> I8
    L4 -->|[BM]| I4
    L5 -->|[ML]| I7
    L6 -->|[BM]| I10
    L7 -->|[EM]| I9
    
    %% Externals to Intermediates
    E1 -->|[AM]| I2
    E2 -->|[OD][ML]| I13
    E3 -->|[MM]| I12
    E4 -->|[OD]| I13
    
    %% Intermediates to Intermediates
    I1 -->|[AM]| I2
    I4 --> I2
    I2 -->|[AM]| I3
    I2 --> I5
    I5 --> I6
    I7 -->|[CFD]| I6
    I7 -->|[CFD]| I8
    I8 --> I6
    I11 --> I8
    I10 --> I9
    I12 -->|[MM]| I13
    
    %% To Outcomes
    I3 -->|[ML]| O1
    I6 -->|[MM]| O1
    I13 -->|[MM]| O1
    O1 -->|[MM]| O2
    I9 -->|[ML]| O3
    L7 -.->|[EM]| O3
    
    %% Feedback loops (Orange arrows in diagram)
    I10 -.->|[Orange]| O3
    O3 -.->|[Orange]| L7

    %% Dashed constraints/boundaries
    L1 -.-> L6
    E5 -.-> L6
    E6 -.-> L7
    O3 -.-> O2
    
```