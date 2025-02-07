---

layout: post-release
title: 'New release: 1.5.0'
author: foosel
date: 2020-11-30 15:55:00 +0100
card: /assets/img/blog/2020-11/2020-11-30-octoprint-1.5.0-card.png
featuredimage: /assets/img/blog/2020-11/2020-11-30-octoprint-1.5.0-card.png
poster: /assets/img/blog/2020-11/2020-11-30-octoprint-1.5.0-poster.png
images:
- url: /assets/img/blog/2020-11/2020-11-10-screenshot-swu.png
  title: Release channels for third party plugins and individual notice configuration.
- url: /assets/img/blog/2020-11/2020-11-10-screenshot-systeminfo.png
  title: New system information screen gives access to help in support and bug reports.
- url: /assets/img/blog/2020-11/2020-11-10-screenshot-recovery.png
  title: Recovery dialog gives access to system commands, backups and system info, as well as basic printer control (if connected).
- url: /assets/img/blog/2020-11/2020-11-10-screenshot-timelapse-player.png
  title: Timelapse player for mp4 timelapses, thanks to @jneilliii.
excerpt: "After almost 4 months of development and a three week long RC phase, I'm proud to present you OctoPrint 1.5.0!"

release: "1.5.0"

headsups:
- title: Access Control is now mandatory and no longer can be disabled
  content: >
    If you so far had Access Control disabled, upon upgrading to 1.5.0, OctoPrint will prompt
    you to create a user name and password for the (first) admin user. This step was sadly
    necessary as too many people still will happily expose their completely unsecured
    OctoPrint instance on the public internet, causing additional support overhead from both
    attacked users and security researchers. See
    [this guide](https://community.octoprint.org/t/how-to-set-up-octoprint-to-autologin-a-single-user-when-connecting-from-the-internal-network/26235)
    for a way to have OctoPrint log you in automatically when connecting from an internal IP.

pluginincompatibilities:
- name: OctoPrint-GcodeLeveling
  page: https://plugins.octoprint.org/plugins/gcodeleveling/
  link: https://github.com/Willmac16/OctoPrint-GcodeLeveling/issues/5
  linktitle: Willmac16/OctoPrint-GcodeLeveling#5
- name: Octolapse < 0.4.1rc1
  page: https://plugins.octoprint.org/plugins/octolapse/
  rcavailable: https://github.com/FormerLurker/Octolapse/releases/tag/v0.4.1rc1
- name: OctoPrint-PrettyGCode
  page: https://plugins.octoprint.org/plugins/prettygcode/
  link: https://github.com/Kragrathea/OctoPrint-PrettyGCode/issues/75
  linktitle: Kragrathea/OctoPrint-PrettyGCode#75
- name: OctoPrint-WebcamTab
  page: https://plugins.octoprint.org/plugins/webcamtab/
  link: https://github.com/malnvenshorn/OctoPrint-WebcamTab/issues/13
  linktitle: malnvenshorn/OctoPrint-WebcamTab#13

contributors:
- chudsaviet
- coldtobi
- cp2004
- frenck
- j7126
- jneilliii
- ManuelMcLure
- mjrider
- OllisGit
- shaver
- Sophist-UK
- urish

testers:
- AndKe
- b-morgan
- benlye
- BillyBlaze
- ChrisHeerschap
- cp2004
- CRCinAU
- Crowlord
- Guilouz
- jneilliii
- JohnOCFII
- kmanley57
- Lantoit
- ManuelMcLure
- mild-lemon
- oliof
- Pavulon87
- Prutsium
- radfordwill
- schnello
- varazir
- zeroflow

stats:
  instancegraph: /assets/img/blog/2020-11/2020-11-30-rc-instances.png
  printtimegraph: /assets/img/blog/2020-11/2020-11-30-rc-prints.png
  piecharts: /assets/img/blog/2020-11/2020-11-30-rc-piecharts.png
  totalinstances: 1334
  totalprinttime: 29391
  rcs:
  - tag: 1.5.0rc1
    date: 2020-11-10
    instances: 894
    printtime: 10980
  - tag: 1.5.0rc2
    date: 2020-11-17
    instances: 263
    printtime: 1575
  - tag: 1.5.0rc3
    date: 2020-11-18
    instances: 830
    printtime: 16800

---

It might still a bit early to hand out Christmas presents 🎄, but this year deserves
some special treatment, doesn't it? And thus - after over four months of development and
almost another month of RC testing - I hereby present you the next stable release
of OctoPrint, version 1.5.0 🥳

**"Wait, 1.5.0 already?"** you might say, "You just released 1.4.0 earlier this year!" That's
correct - OctoPrint's versioning has slightly changed and now fully adheres to the ideas
behind semantic versioning, as-in, the so called PATCH number (the 0 in 1.5.0) will now
only increase for releases containing bugfixes only. Instead, for the usual maintenance
releases that contain improvements, fixes and the one or other new feature, the MINOR
number (the 5 in 1.5.0) will increase from now on. Finally, backwards incompatible changes will
increase the MAJOR number (the 1 in 1.5.0) - in OctoPrint's specific case that will mean
dropping Python 2 support in the not so distant future.

So, from 1.4.2 to 1.5.0 this makes a MINOR number increase and thus you can expect more
than just bug fixes in this one :) And like every single release (and release candidate) of OctoPrint ever since early 2016 this
release was made possible only through your continued **[support of my work](/support-octoprint/)** 💕

The [full changelog](https://github.com/OctoPrint/OctoPrint/releases/tag/1.5.0) contains
a long list of new features, improvements and bug fixes, but here are
some of the highlights:

  * **Access Control is now mandatory and no longer can be disabled**. If you so far had it
    disabled, upon upgrading to 1.5.0, OctoPrint will prompt you to create a username and
    password for the (first) admin user. This step was sadly necessary as too many people
    still will happily expose their completely unsecured OctoPrint instance on the public
    internet, causing additional support overhead from both attacked users and security
    researchers. **See
    [this guide](https://community.octoprint.org/t/how-to-set-up-octoprint-to-autologin-a-single-user-when-connecting-from-the-internal-network/26235)
    for a way to have OctoPrint log you in automatically when connecting from an internal IP.**
  * A new **recovery page** is available under `/recovery/` that gives access to configured
    system commands, backups, basic printer controls and the new system information
    (see below), even if the main UI is no longer functional. This will hopefully help
    in case of a third party plugin or a misconfiguration messing with the core UI so much
    it is no longer usable. <a href="#image-2">Take a look at this screenshot!</a>
  * A new **system information screen** is available from footer, settings dialog and recovery
    page. It provides information on the system OctoPrint is running on that's invaluable
    for support and issue analysis and will soon be asked for in support requests and
    bug reports. A one-click copy-paste link is provided. <a href="#image-1">Take a look at this screenshot!</a>
  * OctoPrint will now **detect when there are too many resend requests** being generated by
    the printer (default: more than 10% of transmitted lines getting a resend request as
    response) and display a prominent warning to help identify communication issues causing
    print failures. This detection will only get armed after 100 lines have been sent to
    the printer, to rule out issues during initial connection handshaking.
  * The bundled Software Update plugin now supports **release channels for third party plugins**,
    individually disabling notifications per update check and also update information overlays
    served from plugins.octoprint.org that will make future maintainer changes of plugins
    less cumbersome for all involved. Plugin developers probably want to take a look at
    [the docs](https://docs.octoprint.org/en/maintenance/bundledplugins/softwareupdate.html#version-checks)
    to learn how to make use of release channels. <a href="#image-0">Take a look at this screenshot!</a>
  * A new event `plugin_backup_backup_created` will be triggered on backup creation.
    **Allows third party plugins to perform certain actions on backup creation**, e.g. saving
    them to a cloud provider like GDrive as displayed by the
    [Google Drive Backup plugin](https://github.com/jneilliii/OctoPrint-GoogleDriveBackup).
  * **A terminal filter configuration for the busy protocol** now comes preconfigured. If you
    have modified your stock terminal filters, you'll have to add this manually, using
    name "Suppress processing responses" and regex `Recv: (echo:\s*)?busy:\s*processing`.
  * **Support has been added for reading the long filename from `M20` if included** or adding it from a plugin
    (e.g. one that utilizes a storm of `M33` to fetch all long names, [proof of concept here](https://gist.github.com/foosel/cadc38123687a46816a1d3e1d160d48a)). Please note:
    That's the only way `M33` will ever be supported in OctoPrint, as it is utterly the
    wrong way to go about fetching long names for a *list of files of unknown size*, so
    stop asking about it now please ;)
  * The whole code base now uses [black](https://black.readthedocs.io/en/stable/),
    [prettier](https://prettier.io/), [isort](https://pycqa.github.io/isort/),
    [pre-commit](https://pre-commit.com/) and a bunch of
    [custom pre-commit hooks](https://github.com/OctoPrint/codemods) to ensure **consistent
    formatting and enforcement thereof**. For anyone doing development, a file containing
    revs to ignore by `git blame` is included so this should hopefully not nuke the
    usefulness of that as long as a current git version is used, set it up via
    `git config blame.ignoreRevsFile .git-blame-ignore-revs`.
  * **New plugin timings logging feature.** If enabled (via Settings > Server > Debug options)
    this will write two new files to the logging dir, `plugintimings.log` and
    `plugintimings.csv`, which contain timing information for each and every hook or
    implementation call on plugins registered with OctoPrint. This should be helpful to
    debug any kind of performance issues caused by third party plugins. It should also be
    a valuable tool to debug performance issues with bundled plugins.
  * The timelapse list now has a nifty little **web player built in for MP4 timelapses**,
    courtesy of @jneilliii. MP4 is now also the default format for new timelapses.
    <a href="#image-4">Take a look at this screenshot!</a>
  * **Several dependencies have been upgraded**, most prominently Font Awesome, which is now
    bundled in version 5. A compatibility layer should ensure that plugins still
    relying on 4.x icon and class names will continue to work as expected.
  * **A big number of bug fixes**, among which is a fix for cancelling/pausing taking too long,
    a fix in the plugin manager to remove timeout issues when installing huge plugins,
    a fix for `M876` not force sending while printing, a fix for installation of `tar.gz`
    plugins and plugin installation under Windows, several performance improvements and
    much much more.
