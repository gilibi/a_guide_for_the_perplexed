**Development**
=================
Software development is the process of computer programming, documenting, testing, 
and bug fixing involved in creating and maintaining applications and frameworks resulting in a software product

*Source to target*
------------------
The basic fundamental of BI software development process starts with the source to target document (S2T). 
the purpose of this document is to map source system fields (from files or DB  tables ) to the fields of
a target system in our case dim/ fact tables in the data warehouse / data mart. 
other important information that the S2T document will include:
  - Business logic required in order to create fields.
  - Loading frequency for the mapping described by the document.
  - What should be the joins in order to get the desired dataset.
  - Data types of both the source as well as the target fields.
  - Any conversion logic that is applied to convert between data types.
  - Any business rules that need to be applied.

*Design of reports*
-------------------
Designing BI report is a major step in order to succeed in every BI implementation.
Bad design may lead to confusion and mislead BI end users or cause bad business decisions. 
good designed BI reports and dashboards may help the company to reveal unusual patterns or to get to important decisions.
3 key questions need to be answered while designing BI reports: 

**WHO** - the first answer will be who is your target audience: 
- business users, and/or
- management users, and/or
- board of directors
	
**WHAT** - the basic fundamental of the reports are the metrics and kpi's
	 via interviews you will find out what metrics and KPIs are currently in use to monitor the organization business processes 

**HOW** - the last question that will be answered will be how to present the data and metrics. 
for example, which diagram/ chart will be easier to understand and will present the information in the right context. 

based on the answers the next step will be creating a mockup containing all key information 
and relevant charts and get a sign off on it from the stakeholder/clients of the reports. 

*Performing code reviews*
-------------------------
Code Review, is a systematic and intended act to perform a check on a developer code searching for mistakes, bugs, 
inefficiency or lack of use of best practices.
Code review is done in order to improve the overall quality of code written in the project
and to help the developers to learn from each other's mistakes - without blaming!. 
It is very important to take in mind and reserve time from the beginning to perform code reviews.
Code review can be done by several persons:
- Peer developer
- PM
- Other PM
- Architect 

*Recurring team meetings*
-------------------------
In order to establish Work routine, a recurring team meetings is a must. 
when project is at work-in-process state it is recommended  to have a daily team meeting where all members can update their status of current task and/or ask for guidance and/or raise flags regarding progress of their tasks.
Weekly team meetings will be the place to share concepts define agenda for development, perform design reviews 
and connect all team members to the "big" picture of the project.

*On-going documentation*
------------------------
It is highly important to maintain and keep the project documentation up to date. 
Any new columns , features and other functionality added to the project must be updated. 
If possible it is recommended to use tools that will automate documentation straight for code. 
Another possibility is to extend logging in the project and use logs as documentation.
  
