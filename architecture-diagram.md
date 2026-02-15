# Service Architecture & Operating Model

```mermaid
flowchart TB
  %% Customer & Channels
  C[Customers\n(Global / France / Secure)] --> V[VIBE / My Services Portal\nSingle Pane of Glass]

  %% Digital + AI
  V --> AI[AI Assist / Virtual Agent\nDeflection • Triage • Guided forms]
  V --> KB[Knowledge & Self-Service\nHow-to • Known errors • Status]

  %% Workflow / ITSM
  V --> SN[ServiceNow Platform\nITSM • CSM • SLA/Entitlements\nIncident • Request • Change • Problem • MIM]

  %% Service Assurance
  subgraph SA[Service Assurance Layer]
    SPL[Splunk\nObservability • AIOps correlation\nNoise reduction • Dashboards]
    BP[Ciena Blue Planet\nNetwork/service assurance\nTopology • Correlation]
  end
  SPL --> SN
  BP --> SN

  %% Integration / APIs
  SN --> API[API & Integration Layer\nTMF-aligned APIs • iPaaS\nEvent & Ticket APIs]
  V --> API

  %% Service Bridge product
  API --> SB[Service Bridge (Commercial)\nCustomer ITSM Integration\nBi-directional ticket sync\nStatus/Change notifications]

  %% Domains / Fulfillment & Ops
  API --> DOM[Domain Platforms\nConnectivity • Voice • Security\nNewco Lead-to-Cash stack\nOrder/Inventory/Provisioning]
  SN --> DOM

  %% Operating model / SIAM
  subgraph OPS[Operating Model (SIAM)]
    SMI[Global Service Mgmt Integrator (SMI)\nProcess owners • Tool owners • KPI owners\nStandards • Governance • Reporting]
    ENT[Operational Entities (federated execution)\nInternational • France • Secure\nL1/L2 operations]
    COE[L3 Center of Excellence\nAutomation • AIOps tuning • Reliability\nOnboarding kits • Innovation]
  end

  SN --- SMI
  SA --- COE
  DOM --- ENT
  SMI --- ENT
  COE --- ENT
```
