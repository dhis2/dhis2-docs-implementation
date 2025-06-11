# Standard Operating Procedures [Templates] { #upgrade_sop_templates }

## 1. Pre-Upgrade Assessment

**Purpose:**

To establish a clear understanding of the current system environment, available resources, and team readiness before planning the upgrade.

This document also serves to justify the need for the upgrade.

**Inputs:**

- Current DHIS2 system and infrastructure details
- Team roster and availability

**Outputs:**

- Baseline system documentation
- Resource and team inventory

**Checklist:**

- [ ] Current System Analysis
  - [ ] DHIS2 Version: ____
  - [ ] Database Version: ____
  - [ ] OS Version: ____
  - [ ] Java Version: ____
  - [ ] Available Storage: ____
  - [ ] Available Memory: ____

**Resource Inventory**

| Resource Type | Current | Required | Gap |
| ------------- | ------- | -------- | --- |
| Storage       |         |          |     |
| Memory        |         |          |     |
| CPU           |         |          |     |
| Network       |         |          |     |

**Team Availability Matrix**

| Role                 | Primary Contact | Backup Contact | Availability Dates |
| -------------------- | --------------- | -------------- | ------------------ |
| System Administrator |                 |                |                    |
| Database Admin       |                 |                |                    |
| Network Engineer     |                 |                |                    |
| DHIS2 Expert         |                 |                |                    |

---

## 2. Evaluating Changes

**Purpose:**

To systematically review all changes introduced by the upgrade, assess their impact, and document actions required for a successful transition.

**Inputs:**

- Release notes for all relevant DHIS2 versions
- Upgrade notes (technical requirements)
- Feature and deprecation lists

**Outputs:**

- Documented list of relevant changes
- Categorized impact assessment
- Action plan for managing changes

**Change Impact Table:**

| Change Description       | Category (User/API/Config) | Impact Summary | Action Required | Owner | Due Date |
|-------------------------|----------------------------|---------------|-----------------|-------|----------|
|                         |                            |               |                 |       |          |

**Checklist:**

- [ ] Review release notes for all versions being upgraded through
- [ ] Review upgrade notes for technical requirements (Java, PostgreSQL, etc.)
- [ ] Identify new features and deprecated features
- [ ] Categorize changes:
  - [ ] End-user impact
  - [ ] API/database schema
  - [ ] Configuration changes
- [ ] Document relevant changes for your implementation

---

## 3. Budgeting & Upgrade Calendar

**Purpose:**

To estimate and allocate resources, develop a clear timeline, and assess risks for the upgrade process, ensuring all stakeholders are informed and prepared.

**Inputs:**

- List of required activities and resources
- Historical cost data (if available)
- Stakeholder availability

**Outputs:**

- Budget estimate
- Upgrade calendar with milestones
- Risk assessment
- Stakeholder communication plan

**Budget Table:**

| Cost Component           | Estimated Cost | Notes                |
|-------------------------|---------------|----------------------|
|                         |               |                      |

**Milestone Calendar:**

| Activity           | Start Date | End Date | Dependencies | Owner |
| ------------------ | ---------- | -------- | ------------ | ----- |
| System Assessment  |            |          |              |       |
| Backup Creation    |            |          |              |       |
| Test Environment   |            |          |              |       |
| Production Upgrade |            |          |              |       |
| Verification       |            |          |              |       |

**Risk Assessment Matrix:**

| Risk Description | Probability  | Impact | Mitigation Strategy | Owner |
| ---------------- | ------------ | ------ | ------------------- | ----- |
|                  | High/Med/Low |        |                     |       |
|                  |              |        |                     |       |

**Checklist:**

- [ ] Estimate costs for training, documentation, technical updates, testing, infrastructure, and support
- [ ] Allocate resources and assign responsibilities
- [ ] Develop an upgrade calendar with key milestones
- [ ] Communicate calendar to all stakeholders
- [ ] Complete risk assessment

---

## 4. Backup Implementation

**Purpose:**

To ensure all critical data, configurations, and customizations are securely backed up and verifiable before proceeding with the upgrade.

**Inputs:**

- Current system and application state
- Backup tools and storage

**Outputs:**

- Verified, restorable backups of all critical components

**Backup Checklist:**

- [ ] Database Backup
  - [ ] Full PostgreSQL dump created
  - [ ] Backup verified
  - [ ] Backup copied to secure location
  - Location: ____
  - Size: ____
  - Checksum: ____

- [ ] Configuration Files
  - [ ] dhis.conf backed up
  - [ ] Apache/nginx configurations
  - [ ] Custom scripts
  - Location: ____

- [ ] Custom Applications
  - [ ] Custom apps listed and backed up
  - [ ] Custom reports
  - [ ] Custom scripts
  - Location: ____

---

## 5. Metadata Cleaning (Optional)

**Purpose:**

To ensure all DHIS2 metadata is free from integrity issues that could disrupt the upgrade process. This step reduces the risk of upgrade failures and ensures a stable foundation for subsequent phases.

**Inputs:**

- Current DHIS2 metadata configuration
- Access to DHIS2 metadata integrity check tools

**Outputs:**

- List of identified metadata issues (critical, severe, warning)
- Resolved issues log
- Sign-off for metadata readiness

**Responsible:**

| Name           | Role                | Signature | Date       |
|----------------|---------------------|-----------|------------|
|                |                     |           |            |

**Key Issues Log:**

| Issue Description         | Severity  | Action Taken         | Responsible | Date       |
|--------------------------|-----------|----------------------|-------------|------------|
|                          |           |                      |             |            |

**Checklist:**

- [ ] Review current metadata for integrity issues
- [ ] Run DHIS2 metadata integrity checks
- [ ] Address all *critical* and *severe* issues
- [ ] Document any warnings for future review
- [ ] Confirm metadata is ready for upgrade

---

## 6. Testing

**Purpose:**

To validate that the upgraded DHIS2 system functions as expected, with all critical workflows, customizations, and integrations tested in a controlled environment.

**Inputs:**

- Test environment with production-like data
- Upgrade testing checklist
- List of user roles, custom apps, and integrations

**Outputs:**

- Completed test results log
- List of issues found and resolved
- Sign-off for upgrade readiness

**Test Plan Template**

| Test Case | Description | Expected Result | Actual Result | Status |
| --------- | ----------- | --------------- | ------------- | ------ |
|           |             |                 |               |        |
|           |             |                 |               |        |

**Performance Baseline**

| Metric               | Pre-Upgrade | Post-Upgrade | Acceptable Range |
| -------------------- | ----------- | ------------ | ---------------- |
| Response Time        |             |              |                  |
| CPU Usage            |             |              |                  |
| Memory Usage         |             |              |                  |
| Database Performance |             |              |                  |

**Test Results Log:**

| Test Scenario           | User Role      | Result (Pass/Fail) | Issues Found | Action Taken | Tester | Date |
|------------------------|---------------|--------------------|--------------|--------------|--------|------|
|                        |               |                    |              |              |        |      |

**Checklist:**

- [ ] Prepare a test environment with production-like data
- [ ] Use the [upgrade testing checklist](link-to-checklist) as a baseline
- [ ] Test with all relevant user roles (data entry, admin, viewers, etc.)
- [ ] Test all custom apps, scripts, and integrations
- [ ] Verify scheduled jobs and background processes
- [ ] Assess performance (response times, analytics, etc.)
- [ ] Conduct beta testing if possible
- [ ] Document all issues and resolutions

---

## 7. Implementation (Upgrade Execution)

**Purpose:**

To execute the upgrade in a controlled manner, minimizing downtime and ensuring a smooth transition to the new version.

**Inputs:**

- Finalized upgrade plan
- System backups
- Technical upgrade guide

**Outputs:**

- Upgraded DHIS2 system
- Upgrade execution log
- Initial validation results

**Pre-Execution Checklist:**

- [ ] All backups verified
- [ ] Test environment results approved
- [ ] Team members available
- [ ] Users notified
- [ ] Maintenance window confirmed

**Execution Steps**

| Step                | Command/Action | Timestamp | Result | Verified By |
| ------------------- | -------------- | --------- | ------ | ----------- |
| Stop Services       |                |           |        |             |
| Backup Database     |                |           |        |             |
| Update Dependencies |                |           |        |             |
| Deploy New WAR      |                |           |        |             |
| Start Services      |                |           |        |             |
| Verify Startup      |                |           |        |             |

**Rollback Plan**

| Step | Action | Command/Process | Verification |
| ---- | ------ | --------------- | ------------ |
| 1    |        |                 |              |
| 2    |        |                 |              |

---

## 8. Verification

**Purpose:**

To confirm that the upgraded system is fully functional, meets performance expectations, and that all critical workflows are operational.

**Inputs:**

- Post-upgrade system state
- Test results

**Outputs:**

- Verification report
- Approval to proceed to post-upgrade activities

**System Verification Checklist:**

- [ ] Core Functionality
  - [ ] User login
  - [ ] Data entry
  - [ ] Analytics
  - [ ] Reports
  - [ ] Custom features

**Performance Verification**

| Test Case | Pre-Upgrade | Post-Upgrade | Status |
| --------- | ----------- | ------------ | ------ |
|           |             |              |        |
|           |             |              |        |

---

## 9. Post-Upgrade Activities

**Purpose:**

To monitor the upgraded system, update documentation, and ensure all changes are properly logged and communicated.

**Inputs:**

- System monitoring tools
- Documentation resources

**Outputs:**

- Updated system and user documentation
- Monitoring and support logs

**Monitoring Plan**

| Metric | Tool | Frequency | Threshold | Action if Exceeded |
| ------ | ---- | --------- | --------- | ------------------ |
|        |      |           |           |                    |
|        |      |           |           |                    |

**Documentation Update Checklist:**

- [ ] System configuration documented
- [ ] Changes logged
- [ ] New features documented
- [ ] Known issues documented
- [ ] User guides updated

---

## 10. Final Review

**Purpose:**

To capture lessons learned, review the overall upgrade process, and obtain formal sign-off from key stakeholders.

**Inputs:**

- Feedback from all upgrade phases
- Documentation of issues and resolutions

**Outputs:**

- Lessons learned document
- Formal sign-off and approvals

**Lessons Learned Template**

| Category  | What Worked | What Didn't | Improvements |
| --------- | ----------- | ----------- | ------------ |
| Planning  |             |             |              |
| Execution |             |             |              |
| Testing   |             |             |              |

**Sign-off Document**

**Upgrade Details**
:   Previous Version: ____ 
    New Version: ____ 
    Date Completed: ____ 
    Performed By: ____ 

**Approvals**
:   System Administrator: ____ 
    Date: ____ 
    Technical Lead: ____ 
    Date: ____ 
    Project Manager: ____ 
    Date: ____
