# Cross Domain Multi-Agent Identity and Authorization 
## Usecase : Multi Enterprise, Cross Domain, Agent driven Vulnerability Remediation workflow 

### High Level Business Workflow 
Sarah, a ‘X Enterprise’ (Dell) security engineer, delegates a vulnerability scan task to a Claude Code agent on her Dell-managed machine. The workflow that follows traverses three enterprises and four agents:
* Dell Code Scanner Agent (Claude Code with /security-review): Scans Dell's internal repository, identifies CVE in a Python dependency, decides to file a remediation ticket.
* Cross-domain hop A — Dell → ServiceNow: Agent presents Sarah's Dell-issued ID token + its AGNTCY badge to ServiceNow's federated Okta tenant, receives ID-JAG, exchanges for scoped access token at ServiceNow's resource server, creates incident.
* ServiceNow Now Assist Remediation Agent (Claude Opus 4.5 backed, native to ServiceNow AI Platform): Picks up the incident, plans remediation, determines a sub-agent is needed for PyPI dependency resolution + GitHub PR creation.

POC Workflow Expansion(if time permits) : 

* Sub-agent spawn: ServiceNow agent spawns a GitHub Remediation Sub-Agent. The sub-agent receives a narrower AGNTCY badge with a nested act chain (Sarah → Dell Scanner → ServiceNow → GitHub Sub-Agent) and a delegation_depth counter.
* Cross-domain hop B — ServiceNow → GitHub: Sub-agent presents the chained identity to GitHub's federated Okta tenant, receives ID-JAG scoped to PR creation in Dell's repository, exchanges for access token, creates PR via Anthropic's Claude Code GitHub Action.
* Audit chain complete: PR appears in Dell GitHub(TBD : with cryptographic provenance) back to Sarah's original delegation. CloudTrail / GitHub audit / ServiceNow incident table / Dell SIEM all contain consistent identity records.

### High Level Architecture Overview and Components 

<img width="3980" height="2579" alt="IMG_6197" src="https://github.com/user-attachments/assets/bd280f93-5e38-4653-9b8a-c387cb395955" />

### Architecture Workflow Diagram 

<img width="4380" height="2780" alt="IMG_6196" src="https://github.com/user-attachments/assets/0a415f79-26a3-4633-9130-99b3d4f87bb8" />




