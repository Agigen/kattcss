# kattcss

## Short about kattcss
kattcss is a fork and extension of [inuitcss](https://github.com/inuitcss), a superb framework with a great ideology, that we at Agigen have used quite a lot throughout the years.

The primary goal with kattcss was essentially to make it easier and more hassle-free to use inuitcss in a whole lot of different projects, by primarily reducing the setup time. We've also made some minor changes, most of which have to do with consistency when it comes to class names, but we've also gone away from inuitcss' way to use multiple repositories to use one, single repository.

*You can read more about the differences from inuitcss in [the license file](/LICENSE)*

**In the future** we want to build kattcss into something more of our own, and less of a bundle of different inuit modules, but we'll probably not stray too much from the architecture of inuitcss 5/itcss. We aim to keep kattcss as somewhat a living organism, that's extended and updated on a regular basis. kattcss, as well as this readme, is very much a work in progress, and we won't promise it won't break your heart.

## Setting up a kattcss project

```scss
// Essential functions and settings
@import 'kattcss/collections/collections.core';

// Essential responsive functions and settings
@import 'kattcss/collections/collections.responsive';

// Settings and functions for a objects and trumps concerning
// layout and skin
@import 'kattcss/collections/collections.layout-skin';

// Import all generic files from kattcss
@import 'kattcss/collections/collections.generic';

@import 'kattcss/base/base.page';

@import 'kattcss/objects/objects.layout';

// Import your components
@import 'components.page-head';
@import 'components.page-foot';

// Import kattcss and inuitcss trumps
@import 'kattcss/trumps/trumps.widths';
@import 'kattcss/trumps/trumps.show-hide';
```

## Import order

*Borrowed from inuitcss' readme*

Because inuitcss is broken apart into lots of small, composable modules, it is
important that you as the developer piece things together in the correct order.
That order is:

* **Settings:** Global variables, site-wide settings, config switches, etc.
* **Tools:** Site-wide mixins and functions.
* **Generic:** Low-specificity, far-reaching rulesets (e.g. resets).
* **Base:** Unclassed HTML elements (e.g. `a {}`, `blockquote {}`, `address {}`).
* **Objects:** Objects, abstractions, and design patterns (e.g. `.media {}`).
* **Components:** Discrete, complete chunks of UI (e.g. `.carousel {}`). This is
  the one layer that inuitcss doesn’t get involved with.
* **Trumps:** High-specificity, very explicit selectors. Overrides and helper
  classes (e.g. `.hidden {}`).

The order of partials within each layer is fairly open; it is the sections
themselves that are important to get in the correct order.

**N.B.** All partials—including your own—follow the `<section>.<file>` naming
convention, e.g. `_objects.box.scss`, `_components.carousel.scss`.

---

**Collections** is a new concept introduced in kattcss: collections are modules that simply import other modules. They provide a great way to get started without having to dig deep into the framework for finding out what you might need for your project. All of the collection modules included in kattcss only import settings and tools, except the generic collection that imports all generic files, so most of the time you won't have to worry about including a collection and getting a lot of junk you might not need in your CSS.


## Toggling modules

In inuitcss, the only way for a developer to completely disable a module is to not import it. In kattcss, you can import all modules provided, and if you'd later on feel the need to disable them, you can simply disable them by the module variables:

```scss
$katt-enable-module-trumps-show-hide: false;
$katt-enable-module-objects-buttons: false;
```

## Variable index, settings

Variables in inuitcss are set up in each module; for example, for finding the variables for trumps.spacing, you need to navigate through your bower components to find the folder for trumps.spacing, and within there find the variables your searching for. In kattcss, we decided to keep all variables in settings files stored in the settings folder, to make it easier to find these.

Also included is an index of all variables that are used in kattcss:

 	kattcss/_vars.scss
 	
This file is never to be included (even though it is safe for you to do so since the variables are tightly shut in an impossible if statement).
 
 
# Module documentation

## trumps.spacing

trumps.spacing contains helper classes for margins and paddings. By default, the margin and padding values (`$katt-margin` and `$katt-padding`) are based upon the `$katt-base-spacing-unit`.

The helpers are named `m` for margins, and `p` for paddings, with their classes prefixed with the utility prefix `u-`. They all come with a set of suffixes for the placement of the margin and padding helpers: `t` for top, `r` for right, `b` for bottom, `l` for left, `h` for horizontal, and `v` for vertical.

These suffixes can in turn be suffixed with how large the margin or padding should be: `/4` for tiny margins and paddings, `/2` for small, `0` for no margin or padding, `2` for large, and `4` for huge spacing.

The margin helpers can also be prefixed with `n` for negative margins.

The classes will in the end look like this (*these are only a few examples, not a complete list*):

* `.u-m` 		- `margin: $katt-margin`
* `.u-mt` 	- `margin-top: $katt-margin`
* `.u-mr` 	- `margin-right: $katt-margin`
* `.u-mb` 	- `margin-bottom: $katt-margin`
* `.u-ml` 	- `margin-left: $katt-margin`
* `.u-mh` 	- `margin-left: $katt-margin; margin-right: $katt-margin;`
* `.u-mv` 	- `margin-top: $katt-margin; $margin-top: $katt-margin;`
* `.u-m/4` 	- `margin: $katt-margin / 4`
* `.u-mt/4` 	- `margin-top: $katt-margin / 4`
* `.u-mh/4` 	- `margin-left: $katt-margin / 4; margin-right: $katt-margin / 4`
* `.u-mr/2`	- `margin-right: $katt-margin / 2`
* `.u-mv/2`	- `margin-top: $katt-margin / 2; margin-bottom: $katt-margin / 2`
* `.u-m0`		- `margin: 0`
* `.u-mb0` 	- `margin-bottom: 0`
* `.u-mt2`	- `margin-top: $katt-margin * 2`
* `.u-mh2` 	- `margin-left: $katt-margin * 2; margin-right: $katt-margin * 2`
* `.u-m4`		- `margin: $katt-margin * 4`
* `.u-ml4`	- `margin-left: $katt-margin * 4`
* `.u-nm/4`	- `margin: -$katt-margin / 4`
* `.u-nml		- `margin-left: -$katt-margin`
* `.u-nmh4`	- `margin-left: -$katt-margin * 4; margin-right: -$katt-margin * 4`
* `.u-p`		- `padding: $katt-padding`
* `.u-pt`		- `padding-top: $katt-padding`
* `.u-pl/4` 	- `padding-left: $katt-padding / 4`
* `.u-pt/2`	- `padding-top: $katt-padding / 2`
* `.u-pb0`	- `padding-bottom: 0`
* `.u-pl2` 	- `padding-left: $katt-padding * 2`
* `.u-ph4`	- `padding-left: $katt-padding * 4; padding-right: $katt-padding * 4`

All of these can also be suffixed with responsive aliases, to only use the helpers in specific breakpoints, such as:

* `.u-m/4-portable`
* `.u-pt4-lap-and-up`
* `.u-mt2-palm`
* `.u-pl/2-desk`
* `.u-p0-portable`

The variables to enable these features of kattcss can be found in `settings.spacing`, or in `vars`