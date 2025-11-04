sequenceDiagram
    participant C as Committee
    participant CE as Committee.Emp
    participant CH as Chancellerie
    participant CHE as Chancellerie.Emp
    participant COL as Collectors
    participant COLE as Collectors.Emp
    participant V as Voters
    participant COM as Commune
    participant COME as Commune.Emp

    %% 1. Initiative Creation & Authentication
    CE->>C: Create [*Initiative*] (title, scope, deadline)
    C->>CE: Issue Mandate (role/task-based)
    CE->>CH: Submit [*Initiative*] for verification
    CHE->>CH: Validate [*Initiative*] (legal/procedural)
    CH->>C: Return authenticated [*Initiative*] + approval stamp
    Note over CH,C: *Initiative* immutable after approval. Signed/hash-chained.

    %% 2. Mandating Collectors
    CE->>C: Issue mandate to COL (per batch/region)
    C->>COL: Distribute [*Initiative*] + Collector credentials
    COLE->>COL: Receive mandate + tools
    Note over COL,CE: Mandates bound to *Initiative* ID + Collector identity. Revocable.

    %% 3. Signature Collection
    COLE->>V: Request [*Support signature*] (name, address, Commune ID)
    V->>COLE: Provide [*Support signature*]
    COLE->>COL: Bundle [*Support signatures*] per *Commune*
    COL->>C: Transfer [*Support signatures*] (encrypted, signed, batched)
    Note over COL,C: Tamper-evident packaging. No cross-Commune bundling.

    %% 4. Commune Verification & Certification
    C->>COM: Submit [*Support signatures*] (per Commune batch)
    COME->>COM: Verify voter eligibility + uniqueness (per Commune)
    COM->>C: Return [*Signature certificates*] (per signature/batch)
    Note over COM,C: *Signature certificates* include: Voter ID (anonymized), Commune ID, timestamp, hash of original, Commune signature.

    %% 5. Committee Aggregation & Chancellerie Submission
    C->>CE: Aggregate [*Signature certificates*] + count
    CE->>CH: Submit [*Signature certificates*] + count report
    Note over CE,CH: Count verifiable + auditable. No double-counting.

    %% 6. Chancellerie Final Verification & Confirmation
    CHE->>CH: Verify [*Signature certificates*] (authenticity, eligibility, count)
    alt Threshold met
        CH->>C: Issue [*Confirmation of the initiative success*] (signed, timestamped)
        Note over CH,C: Triggers: destruction of *Support signatures*, launch of popular vote.
    else Threshold not met
        CH->>C: Issue [*Rejection*] (with reason)
    end
    Note over CH,C: *Confirmation* is public, signed, and auditable. Non-repudiable.