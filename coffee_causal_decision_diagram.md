# Causal Decision Diagram: What Coffee to Buy

This Causal Decision Diagram (CDD) replicates the structure provided in the example image, illustrating the causal chains from actions (levers) and outside factors (externals) to the final goals (outcomes).

```mermaid
flowchart LR
    %% Styling definitions to match the visual groupings
    classDef lever fill:#fae6d1,stroke:#333,stroke-width:2px,color:#000;
    classDef intermediate fill:#c85250,stroke:#333,stroke-width:2px,color:#fff;
    classDef external fill:#f7931e,stroke:#333,stroke-width:2px,color:#000;
    classDef outcome fill:#a8cce4,stroke:#333,stroke-width:2px,color:#000;
    classDef cluster stroke:#333,stroke-width:2px;

    %% Subgraphs for categorization
    subgraph Levers [Levers]
        direction TB
        L1["Buy fair-trade, <br/> bird-friendly <br/> (FTBF) coffee"]:::lever
        L2["Buy regular <br/> coffee"]:::lever
        L3["Number of <br/> pounds of <br/> coffee I buy"]:::lever
    end

    subgraph Externals [Externals]
        direction TB
        E1["Price per <br/> pound for <br/> FTBF coffee"]:::external
        E2["Price per <br/> pound for <br/> regular coffee"]:::external
    end

    subgraph Intermediates [Intermediates]
        direction TB
        I1["Impact on workers and <br/> growers: <br/> • Revenues to growers <br/> • Wages to workers"]:::intermediate
        I2["Environmental impact: <br/> • Birds <br/> • Deforestation"]:::intermediate
    end

    subgraph Outcomes [Outcomes]
        direction TB
        O1["Total social and <br/> environmental <br/> impact of my <br/> choice"]:::outcome
        O2["How much <br/> money I pay <br/> for coffee"]:::outcome
    end

    %% Dependency Links (Causal Chains)
    L1 --> I1
    L1 --> I2
    
    L2 --> I1
    L2 --> I2
    
    L3 --> I1
    L3 --> O2
    
    E1 --> O2
    E2 --> O2
    
    I1 --> O1
    I2 --> O1
```