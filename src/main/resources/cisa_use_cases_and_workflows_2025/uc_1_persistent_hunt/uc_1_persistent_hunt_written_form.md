# Use Case 1: Persistent Hunt

1. New adversary tactic, technique, or procedure is observed or discovered by CISA incident responders, industry, or other entities.
2. Detection analytic based on observed or expected behavior is created by Tier 3 analyst in Elastic or Databricks, as appropriate. (This sub-workflow leverages multiple systems within the Ops Environment but is not described in detail within this use case.)
3. Detection analytic runs automatically on visibility data (network, endpoints, other logs and telemetry).
4. Detection alert sent to SIEM-like dashboard in Elastic. Alert is aggregated with similar alerts to automatically triage events.
5. Option: Events that meet a critical threshold automatically have tickets created in ServiceNow.
6. Tier 1 analyst investigates events in order of rank in automatically triaged dashboard.
    + Tier 1 analyst uses Elastic to investigate event and pivot across datasets, compiling links to relevant data within ServiceNow ticket. 
	+ Tier 1 analyst uses ServiceNow to assign tickets to Tier 2 analysts, as appropriate, or closes out investigation and ticket.
7. Tier 2 analyst receives notification of ticket via ServiceNow. Analyst continues investigation.
	+ Tier 2 analyst pivots from relevant data included in ticket to full records in Databricks. 
	+ Tier 2 analyst develops notebooks and queries in Databricks, as well as queries in Elastic, to complete investigation. 
	+ Tier 2 analyst uses ServiceNow to assign ticket to Tier 3 analyst backlog and/or Production staff backlog, as appropriate, or closes out investigation and ticket.
	+ Tier 2 analyst captures and catalogs analysis artifacts, as appropriate, for archive in Analytic Knowledge Base. Analytic Knowledge Base has a front-end in ServiceNow (SharePoint?), with links to artifacts in AWS S3. 
8. Production staff receives notification of ticket via ServiceNow. Staff begins reviewing and developing a product.
	+ After review/acceptance, staff kicks off ServiceNow workflow for automated template creation of product, incorporating data from ticket, and notifications and coordination of internal collaboration partners from across CISA (or external partners, if possible).
	+ Staff finalizes product in ServiceNow and stages for release, including collateral (i.e. social media, etc.) which is created using LLM and templates.
	+ Staff closes Production workflow as well as ticket workflow, as appropriate, in ServiceNow.
9. Tier 3 analyst receives notification of ticket via ServiceNow. Analyst uses ticket information to develop additional detection models.
	+ Tier 3 analyst pivots from relevant data included in ticket to development environments in Elastic and Databricks.
	+ Tier 3 analyst deploys new detection analytic in Elastic or Databricks, as appropriate.
	+ Tier 3 analyst closes out ticket in ServiceNow.
	+ Tier 3 analyst captures and catalogs analysis artifacts, as appropriate, for archive in Analytic Knowledge Base (ServiceNow front end, AWS S3 back end).