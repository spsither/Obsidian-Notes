# My presentation 
## Centralized Logging System
### Tech stack to use : ELK or Elastic Stack
-   Kibana
-   Elasticsearch
-   Logstash
-   Beats
### Points of Concern
-   System architecture
-   Security
### System architecture
1.  Configure various cloud platforms to push logs to the Elastic Cloud
2.  Set up a on premise Log server running ELK 
3.  Local servers push logs to the Log server using
	-   **_Metricbeats_** for system and service metric
	-   **_Filebeat_** for log
	-   **_Packetbeat_** for network data
	-   **_Auditbeat_** for user and process activity

1.  Configure cloud platforms to push log data to the Log Server
2.  Configure local servers to push log to the Elastic Cloud

### How to secure the system?
-   Two-Factor Authentication
-   secure internode communication with Transport Layer Security (TLS)
-   Encrypt connections between Elasticsearch and Kibana
-   Role-based access control and IP filtering
-   Maintain an audit trail
-   Use a dedicated, unprivileged user to run the stack

## Digital Tourism
- Phone application and website 
- part of Centralized learning resource 
- Hosted on the cloud ?
- Preparing the resources on religious objects

## IT Policy
### Overview
As the CTA progresses digitally with implementation of e-governance, there is a necessity for policy and guidelines to provide guidance, consistency, accountability, efficiency, and clarity.

- Policies and Guidelines work together with your technical security controls to protect confidential information from unauthorized access, disclosure, corruption, loss, and interference in both physical and electronic formats.

- Policies documents how CTA employee and other IT systems can access CTA data and network.

### PROBLEM STATEMENT
- Without any documented policies, every CTA employee will act according to their own understanding of how they should access data and IT systems. This will lead to havoc and inconsistency in operational tasks not to mention vulnerabilities in your security posture.

- As accountability for security continues to grow, a demand to know how you’re going to protect the data that you gather and store, it’s likely that we will  have to get serious about creating and enforcing IT policies and procedures really fast.


# People
- Tenzin Donyo
	- Program Advisor
	- International Foundation for Electoral System (IFES)
- Lobsang Sither
	- Director of Technology
	- Tibet Action Institute
- Steven Adair
	- President
	- Volexity
- Sean Koessel
	- Vice-President
	- Volexity
- K Venkatachalam 
	- Technical Director
	- Fortune Computers Technology Ltd.
- Evan Summers
	- Senior Cyber Security 
	- National Democratic Institute (NDI)
- Jamal Siddique
	- Deputy Chief of Party
	- National Democratic Institute (NDI)
- Anil Prakash
	- Institutional Strengthening Advisor
	- International City Management Association(ICMA)
- Shraddha K Pandey
	- Asia Program Director
	- International City Management Association(ICMA)


# Notes
## General notes
- Involve younger generations of skilled tibetans
- Meet with college students and improve relations with the TCRC
- Do TCRC have enough staff to implement all the projects
- TCRC will build sensitive projects
- avoid vendor lock in. Have an exit strategy.
- Look up Jenkins 

## Security network and web applications
- we tried central on premise AD but got hacked.
- Now looking at Centralized authentication system (`Microsoft Azure AD`, SSO)
- Microsoft Azure Active Directory (AD)
	- can be integrated with SSO
	- `intune` can be used to enforce Policy
- Azure Authenticator app
	- go for approve button and 2 digit number 
	- people sometimes press the approve button unintentionally
- Look into CloudFlair ZeroTrust offerings
	- Does it come under project Galileo ?
- ZeroTrust using `certificate` and `token` and `google security key` based access to Settlement Offices.
- use non-profit license given to SARD across CTA
- Reach out to Microsoft India
- Nasscom - TechSoup - MAANG
- Talk to the regional Indian manager in parallel
- look into Google workspace
- Problem of budget vs China
- Microsoft 365 only vs hybrid
- Microsoft 365 vs Google GCP
	- worth if we get charity status
	- easier SSO
	- good AD but not as good as Microsoft AD
- go from requirements to purchase
- get both Google and Microsoft to compete and then go with one

## **Inter-operability** principles
- Sharing Policies needs to be set up
- Legal matter needs to be worked out between departments before any implementation

## Centralized Logging system
- Cloud is better
- Elastic Stack covers different grounds as SentinelOne
- Look for non profit licence and prefer the cloud for security
- Look into Alternatives
	- [Splunk](https://www.splunk.com/en_us/download/splunk-enterprise.html?utm_campaign=google_apac_tier3_en_search_brand&utm_source=google&utm_medium=cpc&utm_content=Splunk_Enterprise_Demo&utm_term=splunk&_bk=splunk&_bt=611553566118&_bm=p&_bn=g&_bg=122197827023&device=c&gclid=Cj0KCQjw48OaBhDWARIsAMd966C91i5ODBSHSrY6YN2OUDhbd6nsp1JzZZnNbGt-r__GKgmoBKeN86saAvzTEALw_wcB)
		- Volexity has some friends there. Ask them for non-profit.
	- Microsoft Sentinel
	- Helix
	- Elastic

## e-school management portal
- Learning resource for DoE can be merged with a general Centralized learning resource centre
- For Centralized learning resource centre, consider hosting the content locally due to cost considerations.
- Look at software as a service like portal
	- blackboard
	- seesaw
	- canvas
- e-learning record good teachers
- e-library 
- SEEA learning
- CTA and news from inside tibet
- carrer counselling 
- out of syllabus topics

## GreenBook
- Putting the **GreenBook** on the cloud is a security concern and an opportunity.
- Place of birth and picture is sensitive
- Application process should be optimised
- Authenticate and validate people to prevent non-Tibetans to make GreenBook
- Expand the existing Chatrel web app for Green Book application related features
- Security audits
	- Use containers
	- Use VPC
	- Keep ports closed to the internet and use firewall
	- Penetration test
	- Vulnerability test
	- codebase assessment
	- static assessment
	- system architecture assessment
	- prefer having one web application rather than multiple mobile app for security reasons
- Chatrel payment ROI is low
	- can you provide incentives to use online Chatrel
	- expand to other countries
	- expand features of the app and integrate more with GreenBook

## Digital Identity
- Link with services to have more people sign up
- Same as digital GreenBook
- NID has a white paper on Digital Identity
	- People need help the most have the least connection
- Two-factor (`Phone or Email`) with digital GreenBook to make sure that you own the GreenBook number
- Validate with a government approved ID by matching name and date of birth
- Digital security training needs to go with the digital identity

## GIS mapping
- Expand the existing system into every aspect of Tibetan economy
- make it general and not specific to farming
- Look into `ArcGIS`
- garbage in, garbage out

## Religious Tourism
- Walking tour using GPS tracking
- Goal is to provide access to information
- Charge money down the line
- Accessibility audit. Make sure people with disability can use the app.

## E-filing
- Implement with Zero Trust and SSO.
- Keep using Azure 360
- How does it interface with Archival System
- Classify the data otherwise visibility into the data is lost

## Catalog of National Information System and Database
- Can be renamed to inventory management system
- May be able to use an off the shelf software for inventory management system 
- `Microsoft 365 In-tune` agent can be used to manage assets deployed

## Digitization of CTA budgetary process
- ICMA is working on it
- the process is being mapped 

## Political Prisoner Database
- One is in Department on Security and another one in Dharamsala Settlement office
- we can use encrypted thumb drive to transfer data from Settlement Office to DoS
- DIIR and DoS is building duplicate databases
- site to site connection
- data rich and information poor
- Can use `OnBase` to do OCR and digitize physical documents
- scraping websites on the web 

## IT Policy and Guidelines 
- start simple 
- make it meaningful 
- be careful with online templates, it may have stuff not related to you
- policy regarding purchase vendor and configuration relating to asset management 
- Keep an eye on framework for policy
- Start with [CIS controls](https://www.cisecurity.org/insights/blog/cis-controls-enterprise-asset-management-policy-template) and strip away the fat
- Standard hardware, software and operating system
- Reporting of recurring issues so that it bubbles up
- adoption and enforcement
	- make general staff part of the development
	- make it meaningful and simple
	- put some teeth to the policies
- Use tools such as [Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune) to enforce the Policies, and automate the enforcement process
- Needs to come from ground up
	- TCRC should develop IT Policy

## Digital signature
- we can use DocuSign for eSignature
- `DocuSign` is legal binding in India
- `e-Mudra` is an option
- when a document is tempered, you can tells the timestamp and IP

