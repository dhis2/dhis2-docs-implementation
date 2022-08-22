# DHIS2 server hosting

## Architecture

### Most basic DHIS2 installation

DHIS2 is a database driven java web application which can be setup to run very simply, using just a java servlet engine such as tomcat or jetty and a postgresql database server.  A person with reasonable technical ability can read the DHIS2 reference guide and setup the two packages and the database connection between them relatively simply on a laptop machine.  This type of setup is quite common for developers or people who just want to try DHIS2 out locally and see what it looks like.  

Setting up and running DHIS2 in production involves a lot more than this.

### DHIS2 in production

Planning for a DHIS2 server that is running in a production environment is a much more detailed and extensive exercise due to the fact that:
- the data it will hold is valuable and potentially sensitive
- large sites may have tens of thousands of users and millions of records
- the system will need to be maintained and updated over many years

All of the above give rise to quite complex requirements regarding physical infrastructure, security and performance constraints and a broad range of technical skills.    

## Making a plan
Budget, inventory, one-off vs routine activities, monitoring etc

## Physical environment
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
