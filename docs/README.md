# Customer Support Ticket Priority Prediction and Automated Assignment System

This Salesforce DX project is based on the uploaded project specification.

## What is included

- Custom object: `Support_Ticket_Intelligence__c`
- Ticket number auto-number: `TKT-{0000}`
- Account and Contact lookups
- Issue Type: Technical / Billing / General
- Description
- Priority: Low / Medium / High
- Status: New / In Progress / Resolved
- Created Date
- Assigned To (User lookup)
- SLA Breach Risk checkbox
- Resolution Time (hrs)
- Auto-Launched Flow: `Support_Ticket_Intellegence`
- Permission set: `Support_Ticket_Intelligence_Access`
- Agentforce subagent/action configuration template

## Priority rules from the project document

High:
- urgent
- not working
- failure

Medium:
- issue
- slow
- delay

Low:
- none of the above

## Flow behavior

Account Name -> latest Account -> latest Support Ticket -> description analysis -> priority -> High decision -> urgent Task when High -> assigned support level -> final message.

## Deployment

Prerequisites:
- Salesforce CLI (`sf`)
- A Salesforce Developer/Trailhead org with the required Flow/Agentforce features enabled
- Appropriate permissions to deploy metadata

From the project root:

```bash
sf org login web --alias support-ticket-org
sf project deploy start --target-org support-ticket-org --source-dir force-app
```

Or deploy with the manifest:

```bash
sf project deploy start --target-org support-ticket-org --manifest manifest/package.xml
```

Then assign the permission set:

```bash
sf org assign permset --name Support_Ticket_Intelligence_Access --target-org support-ticket-org
```

## Important

The Agentforce subagent/action itself is represented as a configuration template because Agentforce setup and metadata availability are org/release dependent. Build the subagent in Agentforce Builder using `config/agentforce_subagent_template.json` and `config/agentforce_action_mapping.md`.

Also create a test Account and Support Ticket record before testing the Agentforce conversation.

## Test cases

1. "Server failure - customer cannot access portal" -> High -> urgent task.
2. "Application is slow and there is a delay" -> Medium.
3. "Request for general information" -> Low.

## Notes

The source document calls the Flow `Support_Ticket_Intellegence` (with the spelling "Intellegence"). This package preserves that name so the project documentation and configuration remain aligned.
