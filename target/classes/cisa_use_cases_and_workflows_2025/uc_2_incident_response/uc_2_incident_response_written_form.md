# Use Case 2: Incident Response

1. CISA customer requests incident response assistance. ServiceNow ticket is automatically created if request comes in by web intake or help desk personnel create ticket manually. 
2. Tier 1 analyst reviews ticket in ServiceNow, following up with customer to collect critical information for response team. Additional information is captured in the ticket.
3. Tier 1 analyst assigns ticket to Cyber Case Manager.
4. Cyber Case Manager reviews tickets if needed schedules scoping call with CISA customer to understand nature of IR request and ensure and validate availability of data for forensic analysis is accessible to CISA .  Non-federal entities require legal agreements in place to allow for CISA to analyze their data and for the deployment of CISA's tools to capture data
5. In the case of ongoing and active intrusion, CCM may evaluate and plan for the deployment of additional data collection in CISA customer environments
6. CCM assigns ticket to Incident Response engagement lead or Tier 2 analyst
7. Tier 2 analyst reviews ticket information and  analyzes customers cloud, network, and host data.. IR analysts will require accounts with required level of permissions in order to access and collect logs and data from customer's cloud environments. CISA will need to deploy network sensors to the affected entity's enterprise network (requiring either a network TAP or a SPAN for collection of network traffic) and/or their operational technology network. The customer will need to deploy EDR agents to all devices capable of running the agent without causing performance issues. Endpoints not able to have an EDR agent installed will need to have forensic images/triage images created, with that data normalized and ingested into the SEIM to allow for collaborative analysis. If customer is Critical Infrastructure and they invoke Protected Critical Infrastructure Information protections, ALL data must be segregated and access controlled to ONLY the specific personnel that are working that engagement.)
	o Customer data is uploaded to warm storage in the CISA Ops Environment. Data is triaged using a canned set of analytics in Databricks. Data is automatically labeled for future use in supervised learning detection models. (I have never seen "canned set of analytics" be effective in forensic examinations. Nation State Adversaries are constantly creating new ways to exploit network environments and devices, which would negate the usefulness of automatic analysis, except in the very basic of triage artifacts.)
	o Tier 2 analyst reviews results of triage analytics and uses Databricks and an AWS analytic workspace to complete forensic analysis of the incident data. (I can't assess how well these tools would work compared to our current toolset as I have never seen these.) Tools include notebook interface in Databricks and a variety of forensic analysis tools preloaded into the analytic workspace image. When handling large volumes of customer data the analytic workspace is a shared environment that facilitates concurrent analysis by several Tier 2 analysts.
	o While Tier 2 analyst captures critical information following standardize incident terminology and key data points in ServiceNow ticket. Critical information automatically populates a report template. (This would be awesome if it works)
	o Tier 2 analyst hands off ticket in ServiceNow to Production staff to complete report. (I feel that there will be more interaction from the analytical team on the report generation, as Production is not technical and would need assistance from the analysts to "tell the story". Again, if this is able to be done in Snow, then great!)
	o Tier 2 analyst captures and catalogs analysis artifacts, as appropriate, for archive in Analytic Knowledge Base (ServiceNow front end, AWS S3 back end).
8. Production staff receives notification of ticket via ServiceNow. Staff begins reviewing and developing product.
	o After review/acceptance, staff kicks off ServiceNow workflow for automated template creation of product, incorporating data from ticket, and notifications and coordination of internal collaboration partners from across CISA (or external partners, if possible).
	o Staff finalizes product in ServiceNow and stages for release, including collateral (i.e. social media, etc.) which is created using LLM and templates.
	o Staff closes Production workflow as well as ticket workflow, as appropriate, in ServiceNow.
	
**EDR**: Endpoint Detection and Response.
**CCM**: Cyber Case Manager.
**LLM**: Large Language Model.
**SPAN**: Switched Port Analyzer.
**TAP**:  Test Access Point.
