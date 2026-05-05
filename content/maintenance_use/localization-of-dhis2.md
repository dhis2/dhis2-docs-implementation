# Localization of DHIS 2

## DHIS 2 localization concepts { #localization-intro } 

Localization involves the adaptation of an application to a specific
location. When implementing DHIS 2 in a given country, adequate resources
should be allocated to translate and localize the application if required.
Translation of the user interface elements, messages, layout, date and
time formats, currency and other aspects must be considered. In addition
to translation of the user interface itself, metadata content which is
contained in the database must also be considered to be translated.

Interface translations are compiled into the system itself, such that new translations
can only be accessed by taking a newer version of DHIS 2.
Database translations, on the other hand, are specific to your implementation
and can be added to your existing DHIS 2 instance.

These two aspects are managed independently and the processes and tools are outlined
below.


## User Interface localization

### Overview

DHIS 2 supports internationalization (i18n) of the user interface through
the use of Java property strings and PO files. Java property files are used
when messages originate from the back-end Java server, while PO files
are used for front-end apps written in JavaScript.
The DHIS 2 Android apps use a specific XML format.

> **Note**
> 
> The translator need not worry about the different resource file formats; 
> the translation platform hides the details, and only displays the strings
> that require translation.  
> For example, the figure below shows the source and target strings when
> translating a resource to French.  
>
> ![](resources/images/translation_ui.jpg)

There should always be an English string for all messages in DHIS 2.
When the user selects a given language, and a translation is present in that
language, then the translation will be shown. However, if the string in the
desired language is missing then fallback rules will be applied. In cases when
two given translations, such as Portuguese and Brazilian Portuguese share
common messages, it is not required to perform a full translation in the
variant language. Only messages which are different should be translated.  
Fallback rules are then applied in the following manner (assuming the user has
chooses Brazilian Portuguese as their language:

1.  Display the message in Brazilian Portuguese if it exists.

2.  If it does not exist in the variant language, then use the Portuguese
    message, if it exists.

3.  If there is no message in either the base language or the variant language,
    choose the ultimate fallback language, English.


>  **Important**
>
>   There are a number of source strings such as "dd MMM yyyy 'to '" which are used
>   for date/time formatting in various parts of DHIS 2. Part of the value
>   should not be translated because it is actually a special formatting
>   field used by either Java or JavaScript to interpolate or format a string.
>   In this example the part of the value which **can** be translated would be
>   "to", for instance to "a" in Spanish. The special string which should **not** 
>   be translated is "dd MMM yyyy". If these date format template
>   strings are translated, it may result in errors in the application!     

>  **Important**
>  
>   Some special variables (e.g. {0} ) use curly brackets. This
>   denotes a variable which will be replaced by a number or other
>   value by the application. You must place this variable notation in
>   the correct position and be sure not to modify it.

### Translation Platform { #translation-server } 

DHIS2 is now using [transifex](https://www.transifex.com) as our main platform for
managing translations. You can access the DHIS2 resources at
[translate.dhis2.org](https://translate.dhis2.org), or directly at
[https://explore.transifex.com/hisp-uio/].

### How do I contribute to translations? 

#### Register as a translator

The first step is to  get access to the project. There are two ways to do this:

1. Navigate to the platform and create an account with transifex, then
	- request access to our organisation "HISP UiO" as a member of the "DHIS 2 Core Apps" translation team.  
	Transifex
have some useful instructions here:
[Getting Started as a Translator](https://docs.transifex.com/getting-started-1/translators)

1. Email the DHIS 2 team at translate@dhis2.org to request access.   
Please provide:
	- the name, email address and translation language of the user(s) you would like us to give access to, and
	- a little bit of information about why you are interested in contributing to the DHIS 2 translations

#### Edit translations

Once you have access as a translator, you can start translating through the transifex Web Editor.

Transifex have a useful guide here:
[Translating Online with the Web Editor](https://docs.transifex.com/translation/translating-with-the-web-editor)

As far as possible, the projects represent DHIS 2 apps one-to-one. For example, the **APP: Data Visualizer** project contains the translation strings for the Data Visualizer app.

Our transifex projects for DHIS2 User Interface all start with one of the following:

- **APP:** indicates that the project contains strings for a specific app
- **APP-COMPONENT:** indicates that the project is a component library used by the apps
- **ANDROID:** indicates that the project is an Andriod app

In addition, **APP: Server-Side Resources** contains some strings that are used by several apps; namely:
- "Data Entry"
- "Maintenance"
- "Pivot Tables"
- "Reports"

Within the projects we have resources, which represent localization files in the source code. In order to support multiple DHIS2 versions, with the same localization files, the _version_ is associated with each instance of the file. So, for **APP: Data Visualizer** the list of resources looks like this in the Web Editor:

![](resources/images/transifex_data_vis.jpg)

i.e. there is only one source resource for the app (`en.pot`), but we have added the versions from 2.31 (v31) up to the latest development (master). The version is shown in the "Category" field, and is also visible as a prefix to the resource name, e.g. `v31--en-pot`.

> **Note**
>
> In general, we request translators focus on the "**master**" resource; it usually contains all strings from previous versions, and when translations are added the platform will fill in matching translations on the previous versions too. See the [localization](https://dhis2.org/localization/#section-2)
section of our website.
 
> **Tip** { .tip }
>
> For a specific language and DHIS2 version, you can get an overview of the tranlation coverage, as well as direct links to all relevant resources on transifex, from the [localization](https://dhis2.org/localization/#section-2) section of our website.

### When will new translations be available in the system?

We have a nightly service that pulls new translations from the transifex platform and opens a pull request on the source code.

The service loops over all projects and supported languages and does the following:

1. Pulls localization files from transifex (**where translations are more than 20% complete**)
2. Raises a pull request on the source code if changes are found for the language

The pull requests are reviewed and merged into the code base as part of the normal development process.

> **Info**
>
> The translations added to transifex will, in general, be in the next available stable release for all supported DHIS 2 versions
>
> _If you need to ensure that your translations are in the next stable release, contact us (translate@dhis2.org) expalining your needs, and we'll let you know what we can do._ 

> **Tip**
>
> The translations you add in transifex should be visible in all development demo versions on our play server (https://play.dhis2.org) within a few days, in most cases.

### Custom translations using the datastore  { #custom_translations_using_the_datastore }

Starting in core version 43.0, there is an option to add custom translations or text overrides for core apps using the datastore. This can be used to translate strings that haven't been translated yet by other means (Transifex), or to override the text in apps in other ways, for example to use domain-specific language.

>  **Important**
>
>  This is an experimental feature and may be subject to change.

Configuring custom translations requires either knowledge of Transifex or some simple API usage in the browser.

Using the feature takes three steps:
1. Enable custom translations from the System Settings app, under the Appearance section
2. Configure the controller in the datastore
3. Configure the app and locale text overrides

#### Step 1. Enable custom translations in the System Settings app

1. Open the Settings app
2. Navigate to the Appearance section
3. Check the checkbox labeled "Enable custom translations" at the bottom of the page

![Enable custom translations in System Settings](./resources/images/ct-settings.png)

#### Step 2. Configure the controller in the Datastore

The controller acts as an allow-list for the specified apps to load custom translations for the specified locales. This is a mechanism for saving network requests in apps and not loading unwanted overrides.

1. Open the Datastore Management app
2. Click New namespace to create a new namespace and key (if not already created) with these exact names: Namespace = `custom-translations`. Key = `controller`

![Create the custom-translations namespace](./resources/images/ct-controller-create.png)

3. Viewing the `custom-translations` namespace, click the Sharing button (three connected dots) on the `controller` key and edit the sharing settings so the public can only view the key, and only you and other trusted app administrators can edit the key. Click Save.

> **Important**
>
> Configuring these sharing settings is important because the datastore is publicly editable by default, and these translations should only be editable by privileged users.

![Change the controller sharing settings](./resources/images/ct-controller-sharing.png)

4. In the code editor window to the right, edit the content to be a dictionary of app identifiers as keys and arrays of locale identifiers as values, i.e. `{ "<app-identifier>": ["<locale1>", "<locale2>"] }`. See the screenshot below for an example.
    1. You can find an app’s identifier in a few ways:
        1. You can navigate to that app in the browser and inspect the URL bar. Some examples are `capture`, `aggregate-data-entry`, and `data-visualizer`. Here are some formats you might find:
            1. `<baseUrl>[/api]/apps/data-visualizer` => `data-visualizer`
            2. `<baseUrl>/dhis-web-capture/` => `capture`
        2. For advanced users, the app identifier used for custom translations is an app’s `key` value from the `/api/apps` response.
    2. You can find a locale’s identifier in a few ways:
        1. In Transifex, the code in parentheses when choosing a language to translate. For example, "Portuguese (Brazil) (pt_BR)" shows the locale identifier is `pt_BR`.
        2. Using the API, you can visit the URL `<dhis2BaseUrl>/api/locales/ui` in the browser, find the locale you want to translate for, then use the `locale` property as the locale identifier.
5. Click Save.

![Configure the controller](./resources/images/ct-controller-config.png)

#### Step 3. Add text overrides for the app and locale

1. In the Datastore Management app, viewing the `custom-translations` namespace, click the New key button at the top.
2. Name the key according to the convention `<app-identifier>__<locale-identifier>`, for example `capture__pt_BR`. **NB:** There are two underscores between the app and locale identifiers.
3. Edit the sharing settings for the new key in the same way as for the `controller` key.
4. In the code editor window to the right, add translations in the format `{ "<text identifier>": "Override text" }`. See below for more information on how to find the right text identifiers to use.
5. Click Save.

![Configure the translation strings](./resources/images/ct-datastore-tl-strings.png)

#### How to find text identifiers for overrides

There are a few options for finding the identifiers (source string/`msgid`) for strings of text in the app:

* In Transifex, text identifiers can be found there in each app, for example "Choose a program and organisation unit to see existing data and create new records."
* In GitHub, identifiers can be found as the `msgid` property in the `/i18n/en.pot` file for each app. Here is the [file](https://github.com/dhis2/capture-app/blob/master/i18n/en.pot) for the Capture app, for example.
* For app developers, these JSON-formatted key-value pairs can be found in the `/src/locales` directory when building an app using the App Platform.
* Sometimes, identifiers can be guessed from the text in the app.

Here are some more details to keep in mind:
* Make sure "interpolation values" like `{{ count }}` or `{{ category }}` are copied exactly in the override string
* Plurals need multiple entries to handle "one" and "many" cases. Observe how plurals are accomplished in the screenshot above, for example for `{{ count }} event` and `{{ count }} event_plural`

#### Validate the changes in the app

Now, these three conditions should be met:
1. Custom translations have been enabled in the Settings app
2. The `custom-translations` namespace and `controller` key in the datastore have been set up with an app and locale allow-list
3. Text overrides for the app and locale have been added to a datastore key for the app and locale

At this stage, the affected apps should now show the new string overrides in the selected locales when the apps are loaded (notice how education-themed strings from the datastore screenshot above are visible in the Capture app below).

![Custom text in the Capture app](./resources/images/ct-capture-inspected.png)

#### How to remove custom translations

To remove an override for one string, remove that line from the `<app>__<locale>` datastore key in the `custom-translations` namespace for the app and locale of interest.

To remove all the custom translations for an app and locale, remove that locale from the app's list in the `controller` key in the `custom-translations` datastore namespace. You can either keep the `<app>__<locale>` key to use again later, or remove the key to clean up.

To remove all custom translations for all apps and locales, remove all the contents of the `controller` key (but don't delete it -- it can be useful later) and uncheck the "Enable custom translations" option in the Appearance section of the Settings app. You can either keep or remove the `<app>__<locale>` keys in the `custom-translations` datastore namespace.

#### App requirements for custom translations from the datastore

Apps using App Platform [v12.11.0](https://github.com/dhis2/app-platform/releases/tag/v12.11.0) can use custom translations via the datastore.

Strings from libraries that an app uses, like the UI library, must also meet the same App Platform requirement to be translatable.


### How do I add a new language?

Please contact us via email translate@dhis2.org, or on the [Community of Practice](https://community.dhis2.org/c/translation) and we'll add that language to the projects on transifex.

Once resources for that language are more than 20% translated, they will start to be pulled into the system. They will then
become visible in the development demo versions, and be available in future releases.

> **Note**
>
> DHIS 2 manages metadata (database) locales independently from the UI. _See the following section._ 


## Metadata/Database translations { #metadata-database-translations } 

In addition to translation of the user interface, DHIS 2 also supports
the localization of the metadata content in the database. It is possible
to translate individual objects through the **Maintenance app**, but in
order to better support a standard translation workflow, a specialized
app has been developed for this purpose.

New metadata locales can be added in **Maintenance app > Locales**.

### DHIS 2 Translations app { #translations-app } 

The DHIS 2 **Translation app** can 
be used to translate all metadata (data elements, categories,
organization units, etc) into any locale which is present in the
database.

To get started, simply choose the **Translations app** from the top level
menu.

![](resources/images/translations_app.png)

1.  Choose the type of object you wish to translate from the **Object**
    drop-down menu, such as "Data elements".

2.  Be sure you have set the **Target Locale** to the correct language.

3.  Choose the specific object you wish to translate, and translate each
    of the properties (Name, Short name, Description, etc). These
    properties vary from object to object.

4.  Press "Save" when you are done translating the specific object to
    save your changes.


> **Note**
>
> You can search for a specific term using the search feature in the
upper right hand corner of the app.
