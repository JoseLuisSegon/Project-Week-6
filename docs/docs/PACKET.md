PACKET: Civil Protection Training-as-a-Service (TaaS) & Compliance Verification Layer

Author: Mónica Zaragoza (Role: MONEY)

Target Vacuum: Compliance-Upgrade & Measurement Bridge

Blueprint Condition Honored: Condition 4 (Fit existing Mexican civil-protection workflow & support safety consultants)

1. Problem & Exact User

Problem: Mexican companies spend millions of MXN annually on mandatory Civil Protection programs (PIP) solely to satisfy legal compliance (fines up to ~MX$565,000). However, this spending buys "preparation theater" rather than actual, measurable rehearsal.

Exact User: External Civil Protection Consultants (Consultores de Protección Civil) and Corporate Safety Leads (Responsables de Higiene y Seguridad) in Mexico who need to issue compliance reports without purchasing expensive VR hardware.

2. Success Definition

Before the module closes, a functional B2B dashboard and payment gateway will be deployed. It will allow a safety consultant to purchase "Rehearsal Session Credits" (SaaS/pay-per-rehearsal), assign them to a corporate client, track real-time rehearsal participation, and generate an aggregate compliance certificate backed by behavioral event logs.

3. Mockup Description & Prompt

UI Mockup Concept: A clean B2B Enterprise SaaS Dashboard (Dark mode, professional slate/blue accents).

Key Elements: A metric card showing "Active Rehearsal Credits", a Stripe-powered checkout modal for purchasing credit tiers (e.g., $4,999 MXN / 100 Rehearsals), an active team progress bar, and a button to "Export Official Civil Protection Audit Log".

4. System Architecture & Flow (Mermaid Swimlane)

sequenceDiagram
    autonumber
    actor C as Safety Consultant (Money Layer)
    actor E as Employee / Rehearser
    participant S as TaaS Platform (Next.js / Stripe)
    participant D as Supabase DB & Event Log

    C->>S: Selects "Rehearsal Credit Tier" & pays via Stripe
    S->>D: Credits added to Consultant Account (RLS Enabled)
    C->>S: Generates Pseudonymous Access Codes for Company
    E->>S: Enters Access Code (No PII requested)
    S->>E: Launches Browser Micro-Rehearsal Session
    E->>S: Completes Rehearsal (Event Trace logged)
    S->>D: Consumes 1 Credit & logs Aggregate Metrics
    C->>S: Downloads "Audit-Ready Civil Protection Proof"
