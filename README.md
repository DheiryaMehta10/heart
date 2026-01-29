graph TD
    Start([<b>START</b>]) --> Login[<b>1. Authentication</b><br/><i>Bcrypt / JWT Auth</i>]
    
    Login --> Scan[<b>2. Data Ingestion</b><br/>Scan Batch No, Expiry, & Photo]
    
    Scan --> SafetyGate{<b>3. SAFETY GATE</b><br/>Check vs Recall DB}
    
    %% Decision Path
    SafetyGate -- "Flagged / Expired" --> Rejected[<b>REJECTED</b><br/>Notify User: Item Not Safe]
    Rejected --> End([<b>END</b>])
    
    SafetyGate -- "Verified Safe" --> Ledger[<b>4. Ledger Listing</b><br/>React UI / Cloud Database]
    
    Ledger --> Sorting[<b>5. Proximity Logic</b><br/>Haversine Formula < 200m]
    
    Sorting --> Matching{<b>Match Found?</b>}
    
    Matching -- No --> Ledger
    Matching -- Yes --> Connect[<b>6. Connection</b><br/>Encrypted Chat & Meetup]
    
    Connect --> Swap[<b>7. Transaction</b><br/>Swap Complete + 2-Way Rating]
    
    Swap --> Stats[<b>8. Impact Dashboard</b><br/>Calculate Savings & Waste Saved]
    
    Stats --> End
