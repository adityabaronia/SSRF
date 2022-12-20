# SSRF

Server side request forgery is a web vulnerability that allows an atacker to induce  the server side application ti make requests to an unintened location.

**In a typical SSRF attack, the attacker might cause the server to make a connection to internal-only services within the organization;s infrastructure.**


What is the impact of SSRF attacks?
A successful SSRF atack can often results in unauthorized action or access to data within the org, either in the vulnerable application itself or on other back-end systems that the application can communicate with. In some situations , the SSRF vulnerability might allow an attacker to perform arbitrary command execution.
