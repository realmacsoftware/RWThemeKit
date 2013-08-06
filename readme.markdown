#RapidWeaver Theme SDK v6.0
*Updated on Tuesday 6th August 2013*
*This is preliminary information, and subject to change prior to the launch of RapidWeaver 6*

This README describes solely the changes to the RWThemeKit SDK for RapidWeaver v6. For full reference, please refer to `documentation.markdown` in this repository.

##Deprecations

Starting in RapidWeaver 6, the `%toolbar%` key is considered deprecated. Instead, developers should move to use `%navigation%`. `%navigation%` functions exactly as `%toolbar%` does.

##New Additions
RapidWeaver 6 introduces the ability for themes to offer split navigation.

`%top_navigation%` returns an unordered list of just the top-level of the page hierarchy.
`%subnavigation%` returns an unordered list of the remaining sub-navigation of the hierarchy, and respects the `RWAlwaysDisplayFullNavigation` key.