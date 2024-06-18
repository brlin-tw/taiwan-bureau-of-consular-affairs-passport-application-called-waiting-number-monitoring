# (IN DEVELOPMENT) Taiwan Bureau of Consular Affairs passport application called waiting number monitoring

Fetch and present the current called applicant number of the specified [Bureau of Consular Affairs](https://www.boca.gov.tw/mp-2.html) waiting queue for the convenience of handling the timing for the applicant to wait at the spot.

![Desktop notification screenshot example](doc-assets/main-view-en.png "Desktop notification screenshot example")

<https://gitlab.com/brlin/taiwan-bureau-of-consular-affairs-passport-application-called-waiting-number-monitoring>  
[![The GitLab CI pipeline status badge of the project's `main` branch](https://gitlab.com/brlin/taiwan-bureau-of-consular-affairs-passport-application-called-waiting-number-monitoring/badges/main/pipeline.svg?ignore_skipped=true "Click here to check out the comprehensive status of the GitLab CI pipelines")](https://gitlab.com/brlin/taiwan-bureau-of-consular-affairs-passport-application-called-waiting-number-monitoring/-/pipelines) [![GitHub Actions workflow status badge](https://github.com/brlin-tw/taiwan-bureau-of-consular-affairs-passport-application-called-waiting-number-monitoring/actions/workflows/check-potential-problems.yml/badge.svg "GitHub Actions workflow status")](https://github.com/brlin-tw/taiwan-bureau-of-consular-affairs-passport-application-called-waiting-number-monitoring/actions/workflows/check-potential-problems.yml) [![pre-commit enabled badge](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white "This project uses pre-commit to check potential problems")](https://pre-commit.com/) [![REUSE Specification compliance badge](https://api.reuse.software/badge/gitlab.com/brlin/taiwan-bureau-of-consular-affairs-passport-application-called-waiting-number-monitoring "This project complies to the REUSE specification to decrease software licensing costs")](https://api.reuse.software/info/gitlab.com/brlin/taiwan-bureau-of-consular-affairs-passport-application-called-waiting-number-monitoring)

English | [台灣中文](README.zh_TW.md)

## Notice

Before using this application please note that:

* This solution only fetches the called number information, applicants should adhere to the agency's regulations to avoid losing the qualification of being serviced.
* Please properly set this utility's polling behavior settings to avoid overloading the agency's IT system.
* This is NOT an official Bureau of Consular Affairs product, the author CAN NOT and WILL NOT provide compensation of any damages relating to the usage of this application.

## Prerequisites

This application requires the following software to be available in order to work:

* A desktop environment that has a running [Desktop Notifications Specification](https://specifications.freedesktop.org/notification-spec/notification-spec-latest.html) notification server implementation(either implemented internally or an external one)
* [libnotify](https://gitlab.gnome.org/GNOME/libnotify)  
  For the `notify-send` command.
* [curl](https://curl.se/)  
  For sending HTTP requests to the hospital's consultation room called patient number website.
* [orf/html-query: jq, but for HTML](https://github.com/orf/html-query)  
  For parsing the hospital's consultation room called patient number webpage and convert the result into JSON data.
* [jqlang/jq: Command-line JSON processor](https://github.com/jqlang/jq)  
  For parsing the JSON data from html-query into simple string.
* [gettext](https://www.gnu.org/software/gettext/)  
  For the software internationalization(I18N) support.
* [Coreutils - GNU core utilities](https://www.gnu.org/software/coreutils/)  
  For the `realpath` and the `sleep` command.
* [Bash](https://www.gnu.org/software/bash/)  
  For running the monitoring program.

## Environment variables to change the monitoring utility's behavior

The following environment variables can adjust the monitoring program's behavior according to the user's need:

### CHECK_INTERVAL_BASE

The base interval for the monitoring polling(unit: seconds).

Default value: `15`

### CHECK_INTERVAL_VARIANCE_MAX

The max variance value to assigning the polling interval some  randomness(unit: seconds).

The actual interval of each polling will be `CHECK_INTERVAL_BASE` + (random number % `CHECK_INTERVAL_VARIANCE_MAX` + 1) seconds.

Default value: `10`

### CHECK_URL

[The Bureau of Consular Affairs passport application called waiting number page](https://www.boca.gov.tw/sp-wain-board-1.html) to monitor.

Default value: (None)  
Example value: `https://www.boca.gov.tw/sp-wain-board-1.html`

### CHECK_TIMEOUT

The timeout time of the HTTP request used for monitoring(unit: seconds).

Corresponding to the `--max-time` command-line option of the curl software.

Defualt value: `30`

## References

* [外交部領事事務局全球資訊網-申辦護照現場等待人數](https://www.boca.gov.tw/sp-wain-board-1.html)  
  The passport application called waiting number page of the Taiwan Bureau of Consular Affairs.
* curl(1) manpage  
  Explains how to use the curl HTTP client utility
* xgettext(1) manpage  
  Explains how to use the `xgettext` command to extract translatable strings from the source code file.
* msginit(1) manpage  
  Explains how to use the `msginit` command to create a new PO message catalog file from the POT template file.
* msgfmt(1) manpage  
  Explains how to use the `msgfmt` command to compile message catalog files into the binary format.
* notify-send(1) manpage  
  Explains how to use the `notify-send` command to send desktop notifications.
* [Basic Design - Desktop Notifications Specification](https://specifications.freedesktop.org/notification-spec/notification-spec-latest.html#basic-design)  
  Explains the basics of the Desktop Notifications in Linux desktop environments.
* [Files - Fields - Machine-readable debian/copyright file](https://www.debian.org/doc/packaging-manuals/copyright-format/1.0/#files-field)  
  Explains how to specify the file matching patterns in the Files fields of the REUSE DEP5 file.

## Licensing

Unless otherwise noted(individual file's header/[REUSE DEP5](.reuse/dep5)), this product is licensed under [the 4.0 International version of the Creative Commons Attribution-ShareAlike license](https://creativecommons.org/licenses/by-sa/4.0/), or any of its more recent versions of your preference.

This work complies to the [REUSE Specification](https://reuse.software/spec/), refer the [REUSE - Make licensing easy for everyone](https://reuse.software/) website for info regarding the licensing of this product.
