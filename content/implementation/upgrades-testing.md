# Testing upgrades

While the DHIS2 software development team execute significant levels of functional, non-functional, and regression testing prior to releases, the scale of the platform and its configurability mean that it is not all scenarios can be explored for every release. It is vital that implementations validate the system against their own critical scenarios, in a test environment with their own data, prior to upgrading their production instance.

Testing should be as exhaustive as possible within the available time and budget. Typically this means some level of prioritisation. For the sake of efficiency, the main focus areas should be:

* **Implementation-specific customisations**: tools and functionalities that might not be tested by anyone else. This can include custom apps and integrations, as well as highly-configured programs.
* **Known challenges**: Core scenarios that vary significantly with different scales of metadata and data in real environments. Straightforward examples are things like analytics generation or searching for enrollments.
* **Critical workflows**: activities that would have serious operational impact for the target implementation in the event of failure. This includes not just consideration of the scenarios, but also the various user roles who need to perform those scenarios.


## Application testing checklist

In order to help identify priority scenarios and critical workflows, a template checklist for upgrades is available [here](https://docs.google.com/spreadsheets/d/1-UznbOoEVo3YJyYbYveSrJ5GKFtP4FUR-ZKJdyse3X8).

This template lists core functionalities of the platform, and is meant to serve as a guide for items that you might want to test as part of your upgrade procedures. You will need to alter this template with any items that are specific to your implementation, for example by adding any type of custom modifications, apps, scripts or other tools you may have made to support your implementation; or any specific activities for your own implementation(s) that are not within the checklist template.

An important part of developing this checklist for your own implementation(s) is to focus on the features that you are currently using. This may include a detailed testing of apps that, while not supported in the most recent version, are still being used until you have had space to implement an upgrade plan or to include a training component for some the latest features that will be replacing previous ones.

The idea behind this checklist is to support you, during your own testing phase, to perform all of the manual testing within DHIS2 ***prior*** to deploying your version upgrade to your production instance.

### Checks with specific users  

Once scenarios are identified, an important consideration is to test them using cloned users that have the exact same user roles and sharing as those deployed in the field.  

For instance, if you want to test the Capture app, along with a specific program; while you can do this with a user that has administrative privileges, you ***must*** ensure that you also do this for data entry users that are entering data into the identified program. For example, if you have a malaria tracker program, along with specific data entry users for that program, you could test the Capture app by cloning one of these data entry users, accessing Capture as that user and following through with the various checks within the Capture app according to your checklist template.

Instructions on how to clone a user within the users app can be found [here](#clone_user)

A broad categorization for testing using specific, cloned users that you should consider includes:

* **Data Entry users** that are using either the Data Entry, Capture app or both. You want to focus on:
    * If they can enter data correctly into these applications without any unnecessary hindrances
    * Checking all of the functions related to data entry that you have outlined in your checklist work as expected
    * Making sure they can only do what they are supposed to (ie. they should not be able to delete a tracked entity instance in capture, if that is not a permission assigned to their user role)
* **Users that focus on "viewing" data** for a particular program or set of programs
    * These users typically have access to the data itself. This may or may not be combined with a data entry role.
    * Check if they have access to the analysis apps they are supposed to, and that the functions within those apps work correctly based on your checklist while using this user
    * Check that they only can access they data they are supposed to
* **Admin users that can add or edit your configuration**
    * These users can have a wide range of permissions depending on your user role set up.
    * Check at least one of each admin user type you have in your system; based on the privileges they have work through your checklist to ensure all functions are working correctly when logged in as these user types.

For the user types above, you may also have variations by program. As an example, a single user may be able to view one or many programs; and different users may have varying degrees of access within these programs. Ideally, you would want to check each of these program users to ensure sharing, user roles and any current and updated features as a result of upgrade is working as expected.

#### Establishing a group of tester

While it will generally always be necessary for the DHIS2 core team to perform tests using cloned users, a useful complement can be to recruit a small group of end users who can support the testing. These users should have different roles in the system, and can support the testing process by performing their typical tasks in a test environment.

## Testing apps under continuous release

Updating individual apps independently might be considered a low-risk subset of upgrades in general. The apps are relatively easy to revert if one runs into issues, but should nevertheless be tested in a separate environment prior to updating; to make sure that any user interface changes are known, and that the key scenarios used by the implementation are still supported.

## Other testing
In addition to testing the user-facing functionality *within* DHIS2 its important as far as possible to verify that scheduled jobs run, integrations continue working, and that there are no performance degradation.

### Scheduled jobs

Testing scheduled jobs involves verifying that background processes run successfully in the upgraded version. This includes testing things like:
Testing scheudled

* resource table updates
* predictors
* analytics generation
* data exchange jobs

This is not always straightforward, in particular for anaytics generation (may require more server resources than what is available in a test enviroment) and data exchange (may require another test environment to push data to). Simplifying the testing may be necessary (though not recommended) in certain cases, for example running analytics for a single year only.

### Integrations

Integrations are often developed locally, and are therefore particularly important to test. This requires that a test environment is also available for whatever other systems that DHIS2 is sharing data or metadata with.

### Performance

Testing performance is also an important, in particular validating that there is no degradation in performance of critical operations. Unfortunately, this can be difficult to measure accurately.

For example, the test environment is generally different from the production environment, both in terms of infrastructure and in the lack of active users. If the infrastructure is shared and/or virtualized, the actual resources available might vary over time, so results are hard to compare. It's recommended that any comparisons between versions are done in the same enviroment, not between one version in a production environment and another version running in a test environment. It would then be better to also measure the current version in the test environment, and then upgrade, retest and compare.

While doing thorough performance tests is complex and generally require dedicated skills and tools, there are some basic things that can be checked relatively easily:

* percived performance during testing of apps/functionality
* compare analytics runtime across versions
* comparing the response time for commmon API requests:
    * creating a new event
    * creating a new enrollment
    * searching for a tracked entity
    * importing a file with aggregate data
    * analytics requests

Basic measurements can be done in the browser console, but it is recommended to also monitor response times using [Glowroot](https://glowroot.org/) or similar tools.

## Beta testing [draft]

Beta testing refers to testing software prior to it's release. Depending on your upgrade calendar, it may be possible to take advantage of the beta testing phase to "get ahead of the curve" and begin testing earlier in your upgrade cycle. In addition, you may be able to provide valuable feedback to the DHIS2 development team, that will help them to fix issues before they are released.

During the beta testing period, the DHIS2 development team publish release candidates for the upcoming release. These can be installed, like the real release, in a test environment, and subjected to the same critical workflows you would target for any upgrade. Issues that are found can be reported to the DHIS2 development team via forms or email shared as part of the test campaign.

Note that issues reported during beta testing should fall into the following categories.

1. Regressions: these are issues that are working in the previous version of DHIS2, but are broken in the release candidate. i.e. they would usually prevent your implementation from being able to upgrade and use the system as before.

2. Blocking issues in new features: these are issues that would prevent your implementation from being able to use the new feature; which may prevent you from upgrading if that is one of the main things you are upgrading for.

It is important **NOT** to use the beta testing programme to report issues that are already present in earlier releases of DHIS2, or have previously been reported in the issue management system (Jira).
