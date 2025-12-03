**Agency**

"The capacity of individuals to act independently and to make their own free choices." - Wiktionary

**Goal**

Free and open "Decentralized AIs (DeAI)" and "Decentralized Physical Infrastructure Networks (DePIN)".

**Forum**

https://discord.gg/3CEcMa9wex

**Information**

https://github.com/Aegency/Aegency/wiki

## Diagram

``` mermaid
graph TD
    %% Node Styling
    classDef client fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
    classDef agent fill:#fff9c4,stroke:#fbc02d,stroke-width:2px;
    classDef infra fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px;
    classDef compliance fill:#ffebee,stroke:#c62828,stroke-width:2px,stroke-dasharray: 5 5;

    %% --- CLIENT SIDE ---
    User((User / Client)):::client
    ClientAgent[Client Agent<br/><i>The Orchestrator</i>]:::client

    %% --- THE NETWORK ---
    subgraph "Web3 Meta Network"
        direction TB
        
        %% Core Agents
        NetAgent[Network Agent<br/><i>Worker / Executor</i>]:::agent
        
        %% Infrastructure Nodes
        Reg[Registry Node<br/><i>Address Book</i>]:::infra
        ID[Identity Node<br/><i>DID & Credentials</i>]:::infra
        State[State Node<br/><i>World Knowledge / Graph DB</i>]:::infra
        Rep[Reputation Node<br/><i>Trust Scores</i>]:::infra
        Store[Storage Node<br/><i>Payload Data</i>]:::infra
        
        %% Compliance Logic (Virtual)
        Comp{Compliance<br/>Check}:::compliance
    end

    %% --- FLOWS / EDGES ---

    %% 1. User Intent
    User -->|1. Define Goal| ClientAgent

    %% 2. Discovery & Setup
    ClientAgent -->|2. Lookup Service| Reg
    Reg -.->|Returns Address| ClientAgent
    
    %% 3. Workflow Delegation
    ClientAgent == "3. Send Workflow (Intent)" ==> NetAgent

    %% 4. Authentication & Compliance loop
    NetAgent -->|4. Auth & Verify| ID
    ID -.->|Valid/Invalid| Comp
    Comp -->|5. Gatekeeper| NetAgent

    %% 5. Execution Context
    NetAgent <-->|6. Read/Write Knowledge| State
    NetAgent -->|7. Store Results| Store

    %% 6. Feedback Loop
    NetAgent --"8. Rate Interaction"--> Rep
    ClientAgent --"9. Rate Network Agent"--> Rep
    Rep -.->|Updates Score| Reg

    %% Legende für Edges
    %% linkStyle default stroke-width:1px,fill:none,stroke:#333;
    %% linkStyle 2 stroke-width:3px,stroke:#0277bd; %% Workflow line thicker
```
