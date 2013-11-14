# Backward Compatibility Policy

| Version | Date | Notes |
| --- | --- | --- |
| 1.0.0 | 2013 | Scrape from [developer.joomla.org](http://developer.joomla.org) |

Backward compatibility for any software platform is a high priority. &nbsp;Clean, maintainable code is also a high priority for any software platform. &nbsp;Sadly, in practice, these two ideals are often at odds. &nbsp;Providing backward compatibility support makes software more complex and less maintainable. &nbsp;The Joomla project's policy for addressing these conflicting ideals is as follows:

### Backward compatibility support is important.

During development, alpha testing, and beta testing of new releases, backward-incompatible changes will be considered issues to be resolved. Every effort will be made to make sure that each release of Joomla is backward compatible with the previous minor release.

### Backward compatibility support will be limited.

When a documented API method is removed or changed, the previously documented method will be retained and deprecated. &nbsp;Deprecated methods will have added code to generate deprecation notices when they are used. &nbsp;The deprecation notices will state specifically when the backward-compatibility support for the method will expire. &nbsp;This expiration will be expressed as a release number which could be as early as the next minor release. &nbsp;In this way old API methods will not have to be maintained longer than necessary, but plenty of warning will be given before their removal.

When data changes are involved, we will provide data conversion tools that will be available before the GA milestone.

It is often very hard to determine if any applications are relying on or extending a subtle feature. &nbsp;Because of this it is difficult to assess whether or not backward-compatibility support needs to be provided for that feature and judgement calls will be made. &nbsp;In these cases if the judgement is wrong it will need to be caught during testing and reported.

### Backward compatibility support is the responsibility of everyone.

It is very important to catch backward compatibility problems during development of new releases. In particular, it is important to test new Joomla releases before they are released in final form. If a backward-compatibility problem is found before the final release, it will be considered an issue and will generally be fixed (by adding backward compatibility support where it is reasonable to do so) if at all possible before the final release.

After the final release, we may elect not to fix outstanding or new backward-compatibility problems. Consumers of Joomla have a right to backward compatibility, but they also have a responsibility to test Joomla against their applications during the beta release cycle (or sooner) to make sure their applications work.

## Commentary

### Developer API

The developer API is the code that a developer uses to write extensions for &nbsp;the Joomla CMS and applications on the Joomla Platform. Where reasonable, new minor releases will be backward compatabie with at least the previous minor release. &nbsp;For example, API not marked as deprecated in version 1.5 will be backward compatible with version 1.6. &nbsp;Unavoidable exceptions can arise (hopefully infrequently). &nbsp;For example, the permission codes in 1.6 are not backward compatible with 1.5 but the goal is for such circumstances to be rare. &nbsp;Contributors will make their best effort to document[&nbsp;potential backward compatibility issues](http://docs.joomla.org/Potential_backward_compatibility_issues_in_Joomla_1.7_and_Joomla_Platform_11.1).

Compatibility between major versions, for example 1.x and 2.x, is desirable but not mandatory nor expected.

### Data Model

Changes to the data model are inevitable in every release. When data model changes occur, they will be documented and an SQL patch will be provided. Where complex transformations are required then code based solutions (for example, upgrade code in the installation or a separate component) will be provided.

### User Interface and Site Behaviour

Changes in the UI between minor releases are to be expected. However, proposed changes should attempt to improve the usage of Joomla, not just change for change's sake. Judgment needs to be used to ensure the "jump" to learn enhancements balances with the net benefit that such enhancements bring. &nbsp;In other words, if a big change is made, make it worthwhile to the end user.

### Site Migration

Our goal is to provide a mechanism for SQL upgrades to automatically happen and not subject the end-user to running SQL upgrade queries manually.

### Core Output

Core output should not be subjected to dramatic change without significant warning. For example, massive changes will have occurred in the core output of Joomla 1.6 compared with Joomla 1.5 and this has been communicated constantly throughout the development of this release.

### Extension Migration

While Joomla core extensions are obviously handled by the Joomla project, third-party migration is the responsibility of the author concerned. &nbsp;Many tools are available since Joomla 1.6 which the developer can take advantage of to assist with this process. &nbsp;We encourage the normal process is that a user will upgrade their site, then install upgrades for all the extensions which will make appropriate adjustments to extension specific code and data.

## Frequently Asked Questions

#### I have a site running on version x.y. How difficult will it be for me to migrate to the next Joomla version?

For maintenance releases (for example, from 1.6.3 to 1.6.4), the upgrade should be very easy, fully automatic, and 100% backward compatible.&nbsp;

For minor releases (for example, from 1.6 to 1.7), there will be normally be some conversion required. An automatic data conversion will be provided for the Joomla! core features. Third-party extensions may or may not require a data conversion, depending on whether the core changes required changes to the specific extension.

Major releases (for example, from 1.9 to 2.0) are not conceptually different from minor releases. However, they are expected to have a greater number of significant changes. Accordingly, they will be more likely to require data conversions for both the core database and for third-party extensions. It is likely that extensions will need to be modified in order to work with a new major release. This means that you will need to make sure all of the extensions in your site have versions that are compatible with the new major release.

#### I have an extension that runs with version x.y. How difficult will it be for me to release a version of that extension for the next Joomla version?

For maintenance releases, there should be no changes required. For dot releases, it will depend on how the specific changes in the dot release interact with your extension. It is expected that most dot releases will not require changes to most extensions.

#### I have an application that uses the framework for Joomla version x.y. How difficult will it be for me to release a new version of that application that uses the next Joomla version?

As mentioned in the Developer API section above, the API will change over time. Developers will get warning when an API is deprecated. When this happens, it will be the application developer's responsibility to change their code to use the supported API before the next release, when the deprecated API will be removed.

When changes are made to the API, functionality will be preserved and documentation will be provided to show how to use the new API to cover the same functionality as the deprecated API.

#### I have a template that works with Joomla version x.y. How difficult will it be for me to release a version of that template that works with the next Joomla version?

As discussed above under Core Output, we will try to keep the output stable over time and to provide warning when something is going to change. This means that templates should not require changes just because a new version of Joomla! is released.

#### I am in a large organization that wants to use Joomla! for an enterprise site. How can I be sure that the product will be stable and that version upgrades will not cause problems?

In a large site, you will be doing some combination of the activities discussed above: namely, site administration, using third-party extensions (or internally developed extensions), using the framework, and using or building templates. Because large, complex sites take longer to test and deploy, frequent version upgrades can be a disadvantage.

For this reason, we will designate some releases to receive long-term security upgrades. For example, let us assume that version 1.6 will be a long-term security release. This will mean that version 1.6 will continue to receive all relevant security fixes for an extended period of time. So large enterprise sites that want to run the same Joomla! version for an extended period of time should build their sites using one of these special versions. In this way, the frequency of upgrades can be reduced.
