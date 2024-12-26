Below is a rough draft of the current submitting patches workflow based on [Submitting Contributions](https://docs.djangoproject.com/en/dev/internals/contributing/writing-code/submitting-patches/)

```mermaid
flowchart TD
    start[Start Contribution] --> isTrivial{Is it trivial?}
    
    %% Trivial path
    isTrivial -->|Yes| directPR[Submit GitHub PR]
    directPR --> completed[Contribution Complete]
    
    %% Non-trivial path
    isTrivial -->|No| existingTicket{Existing Ticket?}
    existingTicket -->|No| createTicket[Create Trac Ticket]
    existingTicket -->|Yes| checkClaimed{Is ticket claimed?}
    
    createTicket --> checkClaimed
    
    checkClaimed -->|Yes| contactDev[Contact Current Developer]
    checkClaimed -->|No| claimTicket[Claim Ticket]
    
    contactDev -->|Collaborate| claimTicket
    contactDev -->|Find Another| existingTicket
    
    claimTicket --> develop[Develop Solution]
    
    develop --> addTests[Add Tests]
    addTests --> addDocs[Add Documentation]
    
    addDocs --> submitPR[Create GitHub PR]
    submitPR --> review{Review Process}
    
    review -->|Needs Work| develop
    review -->|Approved| completed
    
    %% Styling
    classDef decision fill:#ffeecc,stroke:#333
    classDef process fill:#ccffcc,stroke:#333
    class isTrivial,existingTicket,checkClaimed,review decision
    class develop,addTests,addDocs,submitPR,createTicket,claimTicket process
    
    %% Notes
    subgraph Requirements
        direction TB
        note1[Must include tests]
        note2[Must include documentation]
        note3[Sign CLA if new contributor]
    end
```