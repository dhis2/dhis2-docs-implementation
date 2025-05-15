
# DHIS2 Upgrade Guide (non-technical)

Using a supported version of DHIS2 is important to ensure the system remains secure.  Major version of DHIS2 are released on an annual basis (typically in April-May). At any point in time, the last 3 major versions are supported, meaning they receive security patches and bug fixes. This means that a major version upgrade should be planned *at least* every 3 years to ensure a supported version is used. We recommend planning for a major upgrade every year or every 2 years, as this ensures quicker access to the improvements included in each release and means that each upgrade process introduce fewer changes. In addition to the major version upgrades, minor updates and fixes should be applied on a regular basis.

As a system serving as a key component of the government information systems in many countries upgrades must be well planned and executed to avoid interruptions. This section discusses the key elements to consider related to DHIS2 upgrades from a management and implementation perspective, in terms of planning, budgeting, testing, training etc. A guide covering the concrete steps that system administrators need to take to perform the actual software upgrade on the server is covered in [this guide](#techincal-upgrade-guide).

## Why upgrade?

Upgrading DHIS2 requires time and resources from the DHIS2 core team and others involved in testing, and it does involve some risk. However, there is also risk involved in using an outdated software. Keeping DHIS2 updated means:

* Receiving the latest security patches and updates
* Benefiting from bug fixes and performance improvements
* Accessing new features
* Meeting required dependencies

Having a proper plan and procedure for upgrades in place reduces the associated risks, and creates visibility in when resources are needed for the upgrade process. Relying on an unsupported version of DHIS2 is strongly discouraged, and especially when any individual-level/sensitive data is captured.

## DHIS2 versions

DHIS2 core versioning follows this structure:

* Major Upgrade: 
  * Released once a year.
  * Involve significant changes between versions (e.g., 2.38 to 2.39, or v41 to v42).
  * Including database schema changes and new features.
* Minor Upgrade: 
  * Released periodically for maintained versions. You can see the estimated release date for upcoming patches [here](https://dhis2.org/downloads/#next_patch).
  * Include bug fixes and incremental improvements with minimal risk. 
* Hot-fix: 
  * Released only when necessary.
  * Address critical issues and can be safely applied to systems running the preceding patch update. 

> **Note**
>
>Starting with v40, the 2. prefix of the major version has been replaced with v (version). The version format follows: `<major>.<patch>.<hotfix>`. This corresponds to traditional semantic versioning `<major>.<minor>.<patch>`.

### Apps on continuous release

The versions above refer to the core DHIS2 software. DHIS2 comes with a set of *bundled* applications, i.e. applications that come with the software without having to be manually installed from, e.g. the App Hub. An increasing number of these are also released and updated independently through a *continuous release* mechanism. This includes key apps like "Dashboard", "Capture", "Data Entry”, and "Data Visualizer" that are widely used by end users. Each release of the DHIS2 core software comes with the latest version of these bundled applications that were available at the time the core software was released.

Continuously released applications can also be updated manually in the App Management application *independently* of the core DHIS2 upgrades. In this case, the manually updated application will take precedence over the bundled application. If an application is manually updated and later the core software is updated, the manually installed application version will be used *even if this is older than the bundled version*. If the manually installed version is removed, the system will always fall back to whatever bundled version was included with the current core version.

Continuously released applications give both the DHIS2 developers and DHIS2 implementers more flexibility, since changes and fixes to apps can quickly be released, and implementers can install these updates to individual apps through the DHIS2 user interface itself. At the same time, from a DHIS2 upgrade and management perspective, the continuous release of apps is also a complicating factor. Updates to apps must be tested and can in some cases introduce changes in functionality or the user interface that should be communicated to users.

> **Note**
>
> The continuous release process is similar to what many people are used to from their Android or iPhone devices. The Android OS and iOS typically receive major upgrades on a yearly basis, whilst there may be updates available to apps in the Play Store/App Store at any point in time.
> However, unlike the case for smartphone apps, the DHIS2 apps can be upgraded or *downgraded* to any version that is compatible with the current core version. This means that implementers can have full control over the roll-out of new apps; and are not forced to move to the versions bundled with a core upgrade.
