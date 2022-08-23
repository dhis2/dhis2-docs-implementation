# DHIS2 server hosting

This chapter outlines the challenges of setting up a DHIS2 system in production.  It describes various approaches that we commonly see in practice and looks critically at the advantages and disadvantages of each.  It aims to provide practical and pragmatic advice to organisations planning a DHIS2 implementation.  The document refers to a national Ministry of Health (MOH) as the typical system owner, but most of the considerations apply to other types of organisations as well.

## Architecture

### Most basic DHIS2 installation

DHIS2 is a database backed java web application which can be setup to run very simply, using just a java servlet engine such as tomcat or jetty and a postgresql database server.  A person with reasonable technical ability can read the DHIS2 reference guide and setup the two packages and the database connection between them relatively simply on a laptop machine.  This type of setup is quite common for developers or people who just want to try DHIS2 out locally and see what it looks like.  The DHIS2 web application file (the WAR file) is downloaded from the https://dhis2.org/downloads page, the database connection is configured in dhis.conf and the DHIS2 application is accessed via a web browser connecting to the running tomcat server. 

![Simple architecture](resources/images/simple_architecture.png "Simple architecture")

Setting up and running DHIS2 in production involves a lot more than this.

### DHIS2 in production

Planning for a DHIS2 server that is running in a production environment is a much more detailed and extensive exercise due to the fact that:
- the application will typically need to be continuously available 24x7 with very little scheduled or unscheduled downtime
- the data it will hold is valuable and potentially sensitive
- large sites may have tens of thousands of users and millions of records
- the system will need to be actively maintained and updated over many years

All of the above give rise to quite complex requirements regarding physical infrastructure, security and performance constraints and a broad range of technical skill, none of which are immediately visible when viewing the simple architecture above.  It is essential that the server implementation is properly planned for when an implementation is in its planning stage in order to be able to mobilize the physical and human resources to meet these requirements.

## Making a plan
Budget, inventory, one-off vs routine activities, monitoring etc

## Physical environment


|Approach|Description|Cost|Skills|Security|
|--------|-----------|----|------|--------|
|In the basement|Server is installed in the ministry, typically in a re-purposed room|Setup costs can be high, getting the room up to standard regarding power, aircon etc|High level of skill required ranging from system admin, network admin and data centre knowledge|Physical and network security are additional challenges|
|National government data centre|MOH applications are hosted in a purpose builty data centre managed as a cross-government service|Cost to the MOH varies according to the cost recovery mechanisms of the data centre.  Ranges from zero to considerably higher than commercial cloud|Skills required by to run the system limited to system administration.  Dependency that other skills related to networks and virtual machine management and provisioning are available at the data centre|Security concerns are shared across implementers and data centre provider|
|Commercial cloud 1 (Infrastructure as a service)|MOH has an account with a commercial cloud company and pays for the use of server resources|Generally the lowest cost option.  Considerable variation of pricing plans across the market|Mostly just sysadmin skills required to setup and run the system.  Management processes need to be in place to manage the budget and ensure bills are paid.|Security concerns are shared across implementers and cloud provider|
|Commercial cloud 2 (Software as service)|MOH has an account with a commercial cloud company which offers DHIS2-as-a-service|More expensive than infrastructure as a service, but no need to pay for expensive system administrator salaries|Management processes need to be in place to manage the budget and ensure bills are paid|Most security concerns are managed by the service provider|


Pros and cons of spectrum of choices
- in the basement
- national government data centre
- in-country co-location or virtual hosting
- commercial cloud providers
    - generic infrastructure as a service (linode, aws, azure etc)
    - specialized DHIS2 service providers - Software as a service (BAO, BlueSquare, HISP SA etc)

## Required Skillset
DHIS2 is a relatively complex system to administer.  The system administration team will need expertise and experience in:
ubuntu linux
Apache2 or nginx web proxy
Apache tomcat 
Postgresql database
If this experience is not available in-house, the ministry would be well advised to outsource some of the management to a local entity with such a skills portfolio, even if this is seen as a transitory arrangement.

## Maintenance

Beyond installation, the ongoing activities typically consists of : 
1. provisioning of staging/test/training instances as required; 
2. monitoring performance and tuning the software to suit 
3.  managing and testing backups 
4.  patching (typical frequency 4-6 weeks) of minor version upgrades 
5.  plan and execute major DHIS2 instance upgrade (annually)
6.  major operating system/database server upgrades (every 2-3 years)

UIO can provide training on the overall architecture and all things DHIS2-specific and also link the maintainers into the global community of practice in DHIS2 system administration.  Note that there are pre-requisite requirements in terms of the skills listed above.  It is not practical or sensible to depend on system administrators who do not have the requisite experience.
