# Agentforce action mapping

Use this as the build sheet for the Agentforce action described in the project document.

**Subagent**
- Name: Support Ticket Priority Analysis
- API Name: `Support_Ticket_Priority_Analysis`

**Flow action**
- Flow: `Support_Ticket_Intellegence`
- Input: `varAccountName`
- Outputs:
  - `varAccountId`
  - `varTicketId`
  - `varPriorityLevel`
  - `varAssignedTo`
  - `varActionMessage`

**Expected conversation**
1. User provides an Account Name.
2. Agentforce invokes the Flow.
3. Flow retrieves the latest ticket.
4. Flow classifies the description.
5. High priority creates `Urgent Ticket Handling`.
6. Flow returns the result.
7. Agentforce displays the result.

The Agentforce builder UI and metadata availability can vary by Salesforce org/release, so this file is intentionally a configuration guide rather than fabricated org-specific metadata.
