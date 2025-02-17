# thunderbird-patches
Betterbird is a fork of Mozilla Thunderbird. Here are the patches that provide all the goodness.

## Building Betterbird
These instruction assume that you know how to build Thunderbird. The following instructions are specific to Betterbird.

1. Pull `mozilla-esr91` and `comm-esr91`.  
(The `comm-esr91` repo goes into the `mozilla-esr91/comm/` subdirectory.)
1. Put `91/series-M-C` into `mozilla-esr91/.hg/patches`; rename `series-M-C` to `series`.
1. Put `91/series` into `mozilla-esr91/comm/.hg/patches`.
1. Put all patches from `91/branding`, `91/bugs`, `91/features`, `91/misc` into `mozilla-esr91/comm/.hg/patches`,
then move the ones ending in `*-m-c.patch` into `mozilla-esr91/.hg/patches`.
1. Copy `.mozconfig` into the `mozilla-esr91` directory.
1. Apply the patches using `hg qpush -a`.
1. Build normally using `mach build`.
1. Build an installer using `mach package`.
 
Voilà. :heavy_check_mark:

Note that our builds sometimes include patches taken from [bugzilla.mozilla.org](https://bugzilla.mozilla.org/) when we quick-track fixes.
We don't store those patches here. Those patches will have a comment in the series file pointing to the original changeset.

To import: `hg qimport <changeset URL> -n <patch name>.patch`.  
If you miss them, you will notice it on the `hg qpush`.

Linux users please note that [08-branding-m-c.patch](91/branding/08-branding-m-c.patch) patches a Windows installer script making use of Windows PowerShell.
However, that part of the build system should not be triggered for Linux builds.

Linux users also can use [Ansible-betterbird](https://github.com/4ch1m/ansible-betterbird) for an automated "one click" build, well, "one command" build.

Visit [www.betterbird.eu](https://www.betterbird.eu/) for details.
