**Agency**

"The capacity of individuals to act independently and to make their own free choices." - Wiktionary

**Goal**

Free and open "Decentralized AIs (DeAI)" + "Decentralized Physical Infrastructure Networks (DePIN)".

**Software**

Protocol to make any Web3 service usable.

**Forum**

https://discord.gg/3CEcMa9wex

**Information**

https://github.com/Aegency/Aegency/wiki

## Diagram

``` mermaid
graph BT
    %% STYLING
    classDef client fill:#e3f2fd,stroke:#1565c0,stroke-width:2px;
    classDef netAgent fill:#fff9c4,stroke:#fbc02d,stroke-width:2px;
    classDef db fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px;
	
	
    %% USER SPACE
	User((User)):::client
	CA[Client Agent<br/><i>Sovereign Orchestrator</i>]:::client
	
	
    %% SHARED NETWORK SPACE
    subgraph "Shared Web3"
        direction TB
		
        Sett[Settlement Node<br/><i>Payment and Exchange</i>]:::netAgent
        Veri[Verification Node]:::netAgent
        AN[Agent Node<br/><i>Indipendend Agent</i>]:::netAgent
        Exec[Execution Node<br/><i>Compute / Script</i>]:::netAgent
        Data[Data Node<br/><i>Structured Data, Private&Public</i>]:::db
        Rep[Reputation Node<br/><i>Quality Control</i>]:::db
        Reg[Registry Node<br/><i>Service Discovery</i>]:::db
        State[Shared Knowledge Node<br/><i>World Knowledge Graph</i>]:::db
        Store[Storage Node<br/><i>Binary Data, Private&Public</i>]:::db
        ID[Identity Node<br/><i>DID</i>]:::db
    end
	
	
    %% CONNECTIONS
    AN -->|Read| Reg
    AN -.->|Rate Service| Rep
    AN -->|Read/Write| Data
    AN -->|Read/Write| State
    AN -->|Read/Write| Store
    AN -->|Result| CA
    AN -->|Run| Exec
    AN -->|Verify Identity| ID
    
    CA ==>|Delegation| AN
    CA -->|Read| Reg
    CA -->|Present| User
    CA -.->|Rate Service| Rep
    CA -->|Read/Write| Data
    CA -->|Read/Write| State
    CA -->|Read/Write| Store
    CA -->|Run| Exec
    CA -->|Verify Identity| ID
    
    Exec-->|Result| AN
    Exec-->|Result| CA
    
    Rep -.->|Feed Score| Reg
	
	Sett -->|Invoice| AN
	Sett -->|Invoice| CA
	
    User -->|Prompt| CA
	
	Veri -->|Report| CA
	
    %% Legende
    linkStyle default stroke-width:1px,stroke:#333,fill:none;
    linkStyle 4 stroke:#1565c0,stroke-width:3px;
```
