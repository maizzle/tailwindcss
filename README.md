## About

This package exports a **Tailwind CSS 4 configuration** file that can be used to make the CSS output more email client-friendly. The output will still contain modern CSS syntax, so it needs lowering with a tool like [Lightning CSS](https://lightningcss.dev/transpilation.html).

## Installation

```sh
npm install @maizzle/tailwindcss
```

## Usage

Import it in your project's CSS file:

```css
@import '@maizzle/tailwindcss';
```

You may also import configurations individually:

```css
/* Base resets */
@import "@maizzle/tailwindcss/reset";

/* Custom breakpoints */
@import "@maizzle/tailwindcss/screens";

/* mso-* utilities */
@import '@maizzle/tailwindcss/mso';

/* Email client targeting utilities */
@import '@maizzle/tailwindcss/clients';

/* Theme customizations */
@import '@maizzle/tailwindcss/text';
@import '@maizzle/tailwindcss/colors';
@import '@maizzle/tailwindcss/shadows';
@import '@maizzle/tailwindcss/filters';
@import '@maizzle/tailwindcss/spacing';
@import '@maizzle/tailwindcss/borders';
```

## Namespaces

The following namespaces are customized by this package:

- `--breakpoint-*` - breakpoints are reset and only include `xs` and `sm`
- `--spacing` - spacing utilities use a `px` scale instead of `rem`
- `--color-*` - `oklch` colors have been replaced with their HEX equivalents
- `--text-*` - font sizes use a `px` spacing scale instead of `rem`
- `--font-*` - uses custom font stacks that are more compatible with email clients
- `--shadow-*` - custom shadow utilities
- `--blur-*` - custom filter utilities
- borders - custom border radius utilities
- `--animate-*` - this namespace is disabled

## Variants

The package registers a few custom variants.

### Breakpoints

The `screens` configuration has been overridden to include only two breakpoints:

- `sm` - max-width: 600px
- `xs` - max-width: 430px

### hover:

The `hover:` variant has been customized to use a `:hover` pseudo-class instead of `@media`.

Nested media queries, which Tailwind CSS 4 uses by default for these, have [poor support in email clients](https://www.caniemail.com/features/css-at-media/) and cannot be grouped to reduce the size of the HTML.

### Email client targeting

The config includes variants that help style elements in specific email clients.

| Provider      | Email Client                       | Variant            |
|---------------|------------------------------------|--------------------|
| **Apple**     | Apple Mail 10                      | `apple-mail-10:`   |
|               | Apple Mail 12+                     | `apple-mail:`      |
|               | iOS 10                             | `ios-10:`          |
|               | iOS 13                             | `ios-13:`          |
|               | iOS 15+                            | `ios-15:`          |
| **Google**    | Gmail (web)                        | `gmail:`           |
|               | Gmail (Android)                    | `gmail-android:`   |
|               | Gmail (iPad)                       | `gmail-ipad:`      |
| **Microsoft** | Outlook (Mac)                      | `outlook-mac:`     |
|               | Outlook (Android)                  | `outlook-android:` |
|               | Outlook (webmail & iOS dark modes) | `ogsc:`, `ogsb:`   |
| **Webmail**   | Comcast                            | `comcast:`         |
|               | Freenet                            | `freenet:`         |
|               | Yahoo! Mail                        | `yahoo:`           |
| **Other**     | Airmail                            | `airmail:`         |
|               | Edison (iOS, Android)              | `edison:`          |
|               | Notion                             | `notion:`          |
|               | Open-Xchange                       | `ox:`              |
|               | Spark                              | `spark:`           |
|               | Superhuman                         | `superhuman:`      |
|               | Thunderbird                        | `thunderbird:`     |



## MSO utilities

The configuration includes an extensive set of MSO (Microsoft Office) utilities that can be used to style emails in specific versions of Outlook (2007-2024), which use the Word rendering engine. 

These utilities are prefixed with `mso-` and can be used in your HTML like so:

```html
<div class="mso-hide-all">
  Hide this from Outlooks that use Word to render HTML.
</div>
```
