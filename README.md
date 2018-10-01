# BAS Style Kit Oracle Apex Theme

[Oracle Apex theme](https://apex.oracle.com/) for the [BAS Style Kit](https://style-kit.web.bas.ac.uk).

## Overview

This project documents a theme and content that incorporates elements of the BAS Style Kit into Apex applications. This
integration demonstrates how the Style Kit can be used in a third party platform to make applications that are 
consistent, but not uniform, with first party applications that implement the Style Kit directly.

**Note:** This theme is not based on the Style Kit, for example the Apex grid system is used rather than the Style 
Kit's. This to ensure compatibility with Apex's functionality and to guard against having to reimplement Apex features.

The theme is a customised version of the [Apex Universal Theme](https://apex.oracle.com/pls/apex/f?p=42:100::::::) and
includes:

* a colour scheme based on the Style Kit's colours
* custom css to use the Style Kit's fonts and to style some Apex elements that have equivalents in the Style Kit the 
  same way, such as a main navigation header

Extra content and configuration options can be used to implement the Style Kit's:

* [default favicon](https://style-kit-testing.web.bas.ac.uk/core/favicon/)
* [navbar brand text](https://style-kit-testing.web.bas.ac.uk/components/navbar/#brand-text)
* [navigation launcher](https://style-kit-testing.web.bas.ac.uk/components/navbar/#navigation-launcher)
* [default footer](https://style-kit-testing.web.bas.ac.uk/components/footer/#default-footer)

## Installation

Currently this theme needs to be installed into each Workspace that it is needed. This consists of an application that
represents/contains the theme, from which other applications can copy, and subscribe to, the theme.

**Note:** In the future it is hoped the theme can be defined as part of the Apex theme repository, where it can be used
in any workspace.

1. in a workspace create a new (desktop) application named `BAS Style Kit (Apex)` using the *Universal Theme (42)* 
   (any theme style can be used)
2. go to the created application's *Shared Components* -> *User Interface* -> *Themes* page
3. choose the *Import Theme* action
4. choose *From Export* as the import method, choose the `bsk-apex.sql` file in this project as the *Import file*
5. go back to the created application's *Shared Components* -> *User Interface* -> *Themes* page
6. choose the *Switch Theme* action
7. choose *BAS Style Kit (Apex)* as the theme to switch to
8. agree to all of the other default options, including mapping templates (as these are the same)
9. go back to the created application's *Shared Components* -> *User Interface* -> *Themes* page
10. delete the *Universal Theme* theme as it is no longer needed

This should result in the application using a *BAS Style Kit (Apex)* theme.

## Usage

To apply the *BAS Style Kit (Apex)* theme to an application:

1. if necessary, create the application (using the *Universal Theme (42)* and any theme style)
1. go the application's *Shared Components* -> *User Interface* -> *Themes* page
2. choose the *Copy Theme* option
3. choose the *BAS Style Kit (Apex)* application, and *BAS Style Kit (Apex)* theme (use any theme ID e.g. `1100`),
   ensure the *Subscribe Theme* option is enabled
4. go back to the application's *Shared Components* -> *User Interface* -> *Themes* page
5. choose the *Switch Theme* action
6. choose *BAS Style Kit (Apex)* as the theme to switch to
7. agree to all of the other default options, including mapping templates (as these are the same)
8. go back to the created application's *Shared Components* -> *User Interface* -> *Themes* page
9. delete the *Universal Theme* theme as it is no longer needed

**Note:** If you are applying this theme to an existing application, you will need to ensure it is compatible with the
(Apex) Universal theme. For example, if applications using list based navigation will be converted to tab based 
navigation, which cannot be reversed. You may want to copy the application to test using this theme first.

### Favicon

To apply the default Style Kit [Favicon](https://style-kit-testing.web.bas.ac.uk/core/favicon/): 

1. go the application's *Shared Components* -> *User Interface* -> *User Interface Attributes* page
2. set the *Favicon HTML* field to the required markup for the 
   [default favicon](https://style-kit-testing.web.bas.ac.uk/core/favicon/#usage)

### Logo text

The apply the Style Kit's [navbar brand text](https://style-kit-testing.web.bas.ac.uk/components/navbar/#brand-text) styles to the Apex application logo:

1. go the application's *Shared Components* -> *User Interface* -> *User Interface Attributes* page
2. set *Logo Type* to *Text* and *Logo* to the name of the application

**Note:** Image logos can be used but are limited to the height of the navigation header. This is too narrow to use with
the BAS logo.

### Navigation launcher

To apply the Style Kit's [navigation launcher](https://style-kit-testing.web.bas.ac.uk/components/navbar/#navigation-launcher):

1. go the application's *Shared Components* -> *Navigation* -> *Lists* -> *Desktop Navigation Bar* page
2. choose the *Create Entry* action and add items as per below

| List Item | Parent List Item | List Entry Label                   | Target Type | URL Target               |
| --------- | ---------------- | ---------------------------------- | ----------- | ------------------------ |
| 1         | *None*           | `Part of British Antarctic Survey` | *No Target* | *N/A*                    |
| 2         | 1                | `BAS Home`                         | *URL*       | `https://www.bas.ac.uk`  |
| 3         | 1                | `Discover BAS Data`                | *URL*       | `https://data.bas.ac.uk` |

**Note:** If you don't see the *Desktop Navigation Bar* navigation list (which might happen if migrating an existing application), look for a navigation 
menu that contains the logout link, as this is the menu shown in the same location.

### Footer

To apply the Style Kit's [default footer](https://style-kit-testing.web.bas.ac.uk/components/footer/#default-footer),
a number of regions are added to the *global page* (page 0).

To create a global page (if one is does not already exist):

1. go to the application
2. choose the *Create Page* action
3. choose the *Global Page* option

To create the required regions:

1. go to the application
2. edit the *global page*
3. add *Static Content* regions to the *FOOTER* page area as per below:

| Region | Region Name          | Start New Row | Column      | Column Span | Template                | CSS Classes | Content |
| ------ | -------------------- | ------------- | ----------- | ----------- | ----------------------- | ----------- | ------- |
| 1      | `Is something wrong` | *Yes*         | `1`         | `6`         | *Blank with Attributes* | *None*      | [1]     | 
| 2      | `Back to top`        | *No*          | *Automatic* | *Automatic* | *Blank with Attributes* | `u-textEnd` | [2]     |
| 3      | `Divider`            | *Yes*         | *Automatic* | *Automatic* | *Blank with Attributes* | *None*      | [3]     |
| 4      | `Governance`         | *Yes*         | `1`         | `9`         | *Blank with Attributes* | *None*      | [4]     |
| 5      | `Legal`              | *No*          | *Automatic* | *Automatic* | *Blank with Attributes* | `u-textEnd` | [5]     |

[1]

```html
<a href="#">Is something wrong with this page?</a>
```

**Note:** Update the `href` property of this link to a page or email address where the user can report feedback.

[2]

```html
<a href="#top">Back to top</a>
```

[3]

```html
<div role="separator" class="margin-bottom-lg bsk-apex-margin-top-xl bsk-apex-footer-divider"></div>
```

[4]

```html
<div>The <a href="https://www.bas.ac.uk">British Antarctic Survey</a> (BAS) is part of <a href="https://www.ukri.org">UK Research and Innovation</a> (UKRI)</div>

<div>All content is available under the <a href="http://www.nationalarchives.gov.uk/doc/open-government-licence" rel="license">Open Government Licence v3.0</a>, except where otherwise stated</div>
```

[5]

```html
<ul class="margin-top-none margin-bottom-none margin-right-none bsk-apex-list-inline">
  <li><a href="#">Cookies</a></li>
  <li><a href="#">Copyright</a></li>
  <li><a href="#">Privacy</a></li>
</ul>
© (Year) British Antarctic Survey
```

**Note:** Substitute `(Year)` for the current year (e.g. `2018`).

**Note:** The footer's colours are inverted in this project to fit with Apex's page design better. The content is the 
same, with the exception of the OGL logo (the link is still used).

## Developing

This project is developed within the 
[BAS Style Kit (Apex) Master](http://bsdbase.nerc-bas.ac.uk:8080/ords/f?p=4000:1:9421523650299::NO:RP:FB_FLOW_ID,F4000_P1_FLOW,P0_FLOWPAGE,RECENT_PAGES:136,136,136) 
Apex application (number `136`) in the *AEDC* workspace of the *BAS Cambridge* Oracle Apex instance.

**Note:** Contact the maintainer of this project to request access to this application.

This application contains a theme and theme style incorporating relevant elements of the Style Kit. This application 
a basic page to help develop and test this theme and style.

An export of the `BAS Style Kit (Apex)` theme (and theme style) is exported as a theme export from this application as 
`bsk-apex.sql`, kept within this project.

CSS styles used to customise elements of the Universal Theme, or to implement specific parts of the Style Kit, are
maintained in `bsk-apex.css` within this project. This CSS file is hosted on the 
[BAS CDN](https://gitlab.data.bas.ac.uk/WSF/cdn) (currently managed manually) and referenced within the theme style as 
a *File URL*.

## Issue tracking

This project uses [issue tracking](https://gitlab.data.bas.ac.uk/web-apps/bsk/bas-style-kit-apex-theme/issues) to 
manage development of new features/improvements and reporting bugs.

**Note:** Read & write access to this issue tracker is restricted. Contact the project maintainer to request access.

## Feedback

The maintainer of this project is the BAS Web & Applications Team, they can be contacted through the 
[BAS Service Desk](mailto:servicedesk@bas.ac.uk).

## License

© UK Research and Innovation (UKRI), 2018, British Antarctic Survey.

You may use and re-use this software and associated documentation files free of charge in any format or medium, under 
the terms of the Open Government Licence v3.0.

You may obtain a copy of the Open Government Licence at http://www.nationalarchives.gov.uk/doc/open-government-licence/
