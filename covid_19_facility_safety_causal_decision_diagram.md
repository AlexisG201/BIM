# Causal Decision Diagram: COVID-19 Facility Safety

This Causal Decision Diagram (CDD) replicates the structure provided in the example image, illustrating the causal chains for deciding on opening a building and keeping people safe from a pandemic.

```mermaid
graph LR

&#x20;   classDef lever fill:#ffebcd,stroke:#333,stroke-width:2px;

&#x20;   classDef intermediate fill:#d9534f,stroke:#333,stroke-width:2px,color:#fff;

&#x20;   classDef outcome fill:#d9edf7,stroke:#333,stroke-width:2px;

&#x20;   classDef external fill:#f0ad4e,stroke:#333,stroke-width:2px;



&#x20;   subgraph Levers \["Decision levers (choices of actions)"]

&#x20;       direction TB

&#x20;       L1\["Occupancy schedule(s)"]:::lever

&#x20;       L2\["Investment in<br>facility modification"]:::lever

&#x20;       L3\["Investment in HVAC"]:::lever

&#x20;       L4\["Investment in distancing"]:::lever

&#x20;       L5\["Investment in<br>mask compliance"]:::lever

&#x20;       L6\["Investment in<br>safety marketing"]:::lever

&#x20;       L7\["Pricing"]:::lever

&#x20;   end



&#x20;   subgraph Externals \["Externals (context, things we can't control)"]

&#x20;       direction TB

&#x20;       E1\["Building shape"]:::external

&#x20;       E2\["Local infection rate"]:::external

&#x20;       E3\["Demographics of<br>facility population(s)"]:::external

&#x20;       E4\["Virus infection behavior"]:::external

&#x20;       E5\["Regulatory constraints"]:::external

&#x20;       E6\["Business constraints"]:::external

&#x20;   end



&#x20;   subgraph Intermediates \["Intermediates and dependency links"]

&#x20;       direction TB

&#x20;       I1\["Occupancy level"]:::intermediate

&#x20;       I2\["Human movement patterns"]:::intermediate

&#x20;       I3\["Movement of<br>susceptible people"]:::intermediate

&#x20;       I4\["Movement of<br>infectious person(s)"]:::intermediate

&#x20;       I5\["Facility virus exposure patterns<br>(including hot spots)"]:::intermediate

&#x20;       I6\["Social distancing<br>compliance rate"]:::intermediate

&#x20;       I7\["Mask compliance rate"]:::intermediate

&#x20;       I8\["Virus movement patterns"]:::intermediate

&#x20;       I9\["Demand for our<br>products/services"]:::intermediate

&#x20;       I10\["Awareness of our commitment<br>to Covid-19 safety"]:::intermediate

&#x20;       I11\["Virus shed rate"]:::intermediate

&#x20;       I12\["Population susceptibility"]:::intermediate

&#x20;       I13\["Population infection rate"]:::intermediate

&#x20;   end



&#x20;   subgraph Outcomes \["Outcomes"]

&#x20;       direction TB

&#x20;       O1\["Future illnesses<br>(goal: fewer)"]:::outcome

&#x20;       O2\["Future deaths<br>(goal: fewer)"]:::outcome

&#x20;       O3\["Profitability"]:::outcome

&#x20;   end



&#x20;   %% Lever Dependencies

&#x20;   L1 --> I1

&#x20;   L2 --> I2

&#x20;   L3 --> I8

&#x20;   L4 --> I6

&#x20;   L5 --> I7

&#x20;   L6 --> I10

&#x20;   L7 --> I9

&#x20;   

&#x20;   %% External Dependencies

&#x20;   E1 --> I2

&#x20;   E2 --> I13

&#x20;   E3 --> I12

&#x20;   E4 --> I13

&#x20;   E5 -.-> L1

&#x20;   E6 -.-> L7



&#x20;   %% Intermediate Dependencies

&#x20;   I1 --> I2

&#x20;   I2 --> I3

&#x20;   I2 --> I4

&#x20;   I3 --> I5

&#x20;   I4 --> I5

&#x20;   I6 --> I2

&#x20;   I7 --> I11

&#x20;   I8 --> I5

&#x20;   I10 --> I9

&#x20;   I11 --> I5

&#x20;   I12 --> I13

&#x20;   I13 --> I4

&#x20;   

&#x20;   %% Outcome Dependencies

&#x20;   I5 --> O1

&#x20;   O1 --> O2

&#x20;   I9 --> O3

