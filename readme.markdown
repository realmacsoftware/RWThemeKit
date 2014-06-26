#RapidWeaver Theme SDK v6.0
*This is preliminary information, and subject to change prior to the launch of RapidWeaver 6*

This README describes solely the changes to the RWThemeKit SDK for RapidWeaver v6. For full reference, please refer to the [documentation](documentation.markdown) contained in this repository.

##Deprecations

Starting in RapidWeaver 6, the `%toolbar%` key is considered deprecated. Instead, developers should move to use `%navigation%`. `%navigation%` displays the same data as `%toolbar%` would previously.

The RWThemeAuthor key is deprecated, and you should use RWAddonAuthor for your Developer Name.

##New Additions
RapidWeaver 6 introduces the ability for themes to offer split navigation.

`%top_navigation%` returns an unordered list of just the top-level of the page hierarchy.
`%sub_navigation%` returns an unordered list of the remaining sub-navigation of the hierarchy, and respects the `RWAlwaysDisplayFullNavigation` key.

The `RWToolbarItem` Theme PLIST keys now offer a new “Parent” variation that allows you to specify the markup for the navigation menu when the page has subpages (i.e. is a parent page). For examples, check [this commit](https://github.com/realmacsoftware/RWThemeKit/commit/07ba4e71597fc82bdc1abfd8085820e4ca1a3f4d).

##Targeting RapidWeaver 6
As the new %navigation% tags are only available in RapidWeaver 6, to ensure that themes are only installed in versions of RapidWeaver that support this feature, RapidWeaver supports the .rapidweavertheme file extension *in addition to the legacy .rwtheme extension*.

We strongly encourage themes to use the latest RapidWeaver Theme SDK conventions and features, and whilst RapidWeaver 6.x will support .rwtheme files this file format should be considered deprecated and may be removed in the longer term.