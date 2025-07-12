## About

This package exports a **Tailwind CSS 4 configuration** file that can be used to make the CSS output more email client-friendly. The output will still contain modern CSS syntax, so it needs lowering with a tool like Lightning CSS.

## Usage

First, install the package:

```sh
npm install @maizzle/tailwindcss
```

Then, import it in your project's CSS file:

```css
@import '@maizzle/tailwindcss';
```

You may also import individual configurations:

```css
@import '@maizzle/tailwindcss/mso';
@import '@maizzle/tailwindcss/clients';
@import '@maizzle/tailwindcss/theme/colors';
@import '@maizzle/tailwindcss/theme/text';
@import '@maizzle/tailwindcss/theme/shadows';
@import '@maizzle/tailwindcss/theme/filters';
@import '@maizzle/tailwindcss/theme/spacing';
@import '@maizzle/tailwindcss/theme/borders';
```

Note: for Tailwind CSS Intellisense to work, make sure you import this package in an actual .css file in your project.

## Namespaces

The following namespaces are customized by this package:

- `--breakpoint-*` - breakpoints are reset and only include `xs` and `sm`
- `--spacing` - spacing utilities use a `px` scale instead of `rem`
- `--color-*` - oklch colors have been replaced with their HEX equivalents
- `--text-*` - font sizes use a `px` spacing scale instead of `rem`
- `--font-*` - font families are set to use custom font stacks that are more compatible with email clients
- `--shadow-*` - custom shadow utilties
- `--blur-*` - custom filter utilities
- borders - custom border radius utilities
- `--animate-*` - this namespace is disabled

## Variants

The package registers a few custom variants:

### Breakpoint variants

- `sm` - max-width: 600px
- `xs` - max-width: 430px

### Hover variant

The `hover:` variant has been overridden to use a `:hover` pseudo-class instead of a `@media` query, just like in Tailwind CSS v3.

## Email targeting variants

The config includes variants for targeting specific email clients. These can be used to apply styles conditionally based on the client.

- Airmail - `airmail:`
- Apple Mail
    - `apple-mail-10:` to target Apple Mail 10
    - `apple-mail:` to target Apple Mail 12 and later
- Comcast - `comcast:`
- Edison (iOS, Android) - `edison:`
- Freenet - `freenet:`
- Gmail (web, Android, iPad)
    - `gmail:` to target Gmail web
    - `gmail-android:` to target Gmail Android
    - `gmail-ipad:` to target Gmail on the iPad
- iOS Mail
    - `ios-10:` to target iOS 10
    - `ios-13:` to target iOS 13
    - `ios-15:` to target iOS 15 and later
- Notion - `notion:`
- Open-Xchange - `ox:`
- Outlook
    - `outlook-mac:` to target Outlook on Mac
    - `outlook-android:` to target Outlook on Android
    - `ogsc:` and `ogsb:` to target Outlook webmail and iOS dark modes
- Spark - `spark:`
- Superhuman - `superhuman:`
- Thunderbird - `thunderbird:`
- Yahoo! Mail - `yahoo:`

## MSO utilities

The configuration includes an extensive set of MSO (Microsoft Office) utilities that can be used to style emails in specific versions of Outlook (2007-2021), which use the Word rendering engine. 

These utilities are prefixed with `mso-` and can be used in your HTML like so:

```html
<div class="mso-hide-all">
  This will be hidden in Outlook 2007-2021.
</div>
```
