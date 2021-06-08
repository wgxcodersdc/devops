# SysDesign Workshop 1 - Research and Notes
## Why are we building this system

* Who's the primary stakeholder/driver of this initiative?
    * Scenario: Imagine that your Systems/Platform/Infrastructure team needs an alerting and monitoring platform, but you've also been asked to have functionality for analytics and reporting. Company is very data focused, and the data engineers want to analyze operational impact and derive insights from end user interactions.
    * Primary driver: internal team
    * Secondary driver: data analytics team
* Who will be the end user of this system?
    * You and your systems team
    * Other teams that are on call
    * Integration with Data platforms/or host the data yourself
* Is there an expected life time for this system? 
    * 5 years
    * Needs to support AWS (IAM), EC2, EKS support, RDS
    * Don't need ECS, Lambda

* Understanding the above is about a week's worth of meetings, conversations, and basic internal research.

----
## What are our options and alternatives?

* Research is key
* What is your research budget?
    * Do you have time to experiment?
        * Multiple POCs?
        * Multiple Vendor test outs?
    * Window to finish the initial build out or MVP?
        * Get your stakeholders to understand and buy into these differences and make a decision on the solution type early
    * Do you have prior experience with this type of solution/software/hardware
* What is your fiscal budget?
    * Is this a project where you have a fixed and projected budget?
    * Is this a project where you have no known budget?
    * Is this a project with a known cost for the initial build out, but no O&M budget?
        * This is very common for external COTS solutions with one time customizations



### For this scenario
* Research time is going to be 3 weeks
* Budget is tight for recurring software, but are open to scalable virtual hardware costs
    * Your company is an AWS Partner, and gets sliding discounts on AWS Services
* Full build out is going to be 4 months

#### 20% of this project's time is Research


### Let's do some research
#### Free Options
| Solution Name | AWS Support | IAM | EKS | EC2 | RDS| Analytics| Alerting | Paid Support |
|---|---|---|---|---|---|---|---|---|
|Grafana|x|x|x||||x|x|
|Prometheus|x|x|x|||x|
|Kibana (ELK Stack)|x|x|x|x|x|x|x|x|
|CloudWatch|x|x|x|x|x||x|x|


#### Paid Options
| Solution Name | AWS Support | IAM | EKS | EC2 | RDS | Analytics| Alerting | Paid Support |
|---|---|---|---|---|---|---|---|---|
|Moesif|x|x|x|||x|x|x|
|New Relic|x|x|x|x|x|x|x|x|
|DataDog|x|x|x|x|x|x|x|x|

----
### How do we estimate the cost?
* Cost of Software
    * Free as in Beer Software (no license cost)
        * MIT/GPL/BSD
    * One time permanent licenses
        * Pay a one time cost, support may or may not be included
        * More often tied to hardware with software that needs limited support
    * Recurring Cost Contracts
        * Pay the vendor monthly, quarterly, yearly for service and support
        * SAAS, IAAS
    * Mixed upfront plus recurring cost
        * Very common for integrated solutions, big platforms
        * EX: Red Hat Open Shift
* Cost for Infrastructure
    * One time permanent licenses
        * Pay a one time cost, support may or may not be included
        * More often tied to hardware with software that needs limited support
    * Recurring cost for usage
        * Example EC2 bills hourly
* Cost of setup labor
    * Internal build out
        * This is the cost of you and everyone in your company to build the software/hw solution to a working system
        * Cost of training team members on the software throughout the company
        * Cost to initialize the solution, 
            * This is patching servers and desktops to required version etc
    * External vendor build out
        * Contracted upfront cost (One time bill) for the solution
        * Contracted upfront + additional expenses for the soluton
        * No upfront, pay per deliverable
            * Build to hire/freelancers/small consulting firms
* Cost of ongoing maintenance labor
    * Estimated yearly cost to maintain solution internally
    * Estimated yearly cost to maintain solution externally

#### Solution Estimate
 * Initial research shows Kibana as part of an ELK stack to be our prime solution
 * We'd configure this internally, but may investigate costs of a support contract
 * We'd be setting this up entirely in AWS, as 100% of our infrastructure is in AWS
 * For the initial MVP we'd like to focus only on Ops capabilities, around monitoring entire inventory, and alerting on critical 



----
Terms
* Legacy = 5+ years old, Current = within 5 years, Greenfield = New Development
* Minimum Viable Product - MVP 
    * Live or die form of delivering the smallest functional version possible
* ELK Stack (Elasticsearch, Logstash and Kibana) - is a combination of tools used to provide deep queryable, logging, analytics, monitoring and alerting
* SAAS - Software As A Service (Slack) - rule of thumb is you never log into the backend
* IAAS - Infrastructure As A Service (AWS EC2) - can log into the backend