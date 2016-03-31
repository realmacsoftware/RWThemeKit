#RapidWeaver Theme SDK v7.0

This README describes solely the changes to the RWThemeKit SDK for RapidWeaver v7.

**ALL DETAILS IN THIS DOCUMENT ARE SUBJECT TO CHANGE PRIOR TO RAPIDWEAVER 7’S RELEASE**

## SDK Deprecations

Starting in RapidWeaver 6, the `%toolbar%` key was deprecated. Instead, developers should move to use `%navigation%`. `%navigation%` displays the same data as `%toolbar%` would previously, with extra keys available for sub-navigation.

Additionally, the RWThemeAuthor key was deprecated in RapidWeaver 6, and you should use RWAddonAuthor for your Developer Name.

These deprecated keys, while supported in RapidWeaver 7, are provided solely to ensure legacy support and future major upgrades to RapidWeaver (e.g. version 8) may remove support for these keys.

## Identify your theme as responsive (New PLIST Key)

If your theme is responsive, add a TRUE boolean to the `Info.plist` for the `RWThemeIsResponsive` key - an example of the key can be found [here](https://github.com/realmacsoftware/RWThemeKit/commit/7f29d16392f05d5cfee929feab21f3f76d66b832). This PLIST key doesn’t currently have any effect, but we recommend all responsive themes use this key so that any future responsive theme filters show your theme.

## Banner Images (New Feature, New PLIST Keys)

RapidWeaver 7 supports the use of the new `%banner_image%` and `%banner_path%` keys. To enable the use of a banner image in your theme, you must set the `RWThemeSupportsBannerImages` boolean to YES in your theme’s Info.plist. **The Theme.PLIST file will not be used when determining whether to enable the Banner Image feature**. With the PLIST key in your theme, and the `%banner_path%` key in either your index.html or stylesheets, you’ll get a path to the image that can be used as you wish.

If you add `%banner_path%` either to your theme HTML or CSS, the following will be inserted:

```html
<img src="%banner_path%" />
```

becomes

```html
<img src="rw_common/images/banner.png" />
```

and...

```css
#banner {
    background-image: url('%banner_path%');
}
```

becomes

```css
#banner {
    background-image: url('../../images/banner.png');
}
```

If the user does not provide a banner image, you should provide a path to your own using the key `RWThemeBannerFallbackImage` in `Info.plist`. This is relative to your other theme files.

You can suggest a height and width for the banner which will be displayed in the RW settings screen using the following keys:

- `RWThemeBannerImageRecommendedWidth`
- `RWThemeBannerImageRecommendedHeight`

**All banner configuration keys must be within a `RWBannerOptions` dictionary**:

```plist
<key>RWBannerOptions</key>
<dict>
	<key>RWThemeBannerFallbackImage</key>
	<string>images/banners/banner_1.jpg</string>
	<key>RWThemeBannerImageRecommendedWidth</key>
	<integer>500</integer>
	<key>RWThemeBannerImageRecommendedHeight</key>
	<integer>150</integer>
</dict>
```

You can also use the %banner_image% macro to request an image element:

```html
<img src="%banner_path%" id="rw-banner-image" height="" width=""/>
```

It’s important to note that height and width attributes will be those of the asset added by the user - not the recommended height-width integers you enter into the Theme‘s `Info.plist`.

The `alt` attribute can also be placed with the `%banner_alternate_text%` token.

## How to Target RapidWeaver 7 With Your Themes

If you’re building a theme that targets RapidWeaver 7 only, you should add a new key to your Theme’s `Info.plist` (not `Theme.plist`) which describes the target SDK version: `RWThemeSDKVersion`. RapidWeaver 6 supports any version between 1 and 6, and RapidWeaver 6.3.4 rejects themes that use any other SDK version.

RapidWeaver 7 supports `RWThemeSDKVersion` versions 1 through 7. If you wish to target RapidWeaver 7 **only** in your theme, you should ensure you use the `.rapidweavertheme` extension for your theme, and set the `RWThemeSDKVersion` version as `7` (RapidWeaver 5 and earlier will not open this theme format, while any RapidWeaver 6.x release from 6.3.4 onwards will prevent the theme’s installation).

## Migrating Existing Themes to RapidWeaver 7

RapidWeaver 7 will copy over the Addons folder from RapidWeaver 6 automatically on launch. No changes are made to your themes, and the contents of the Addons folder is kept as per RapidWeaver 6.
