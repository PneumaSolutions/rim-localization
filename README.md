# RIM Localization

This repository is the hub for the localization of [Remote Incident Manager](https://getrim.app/) from Pneuma Solutions.

## Message files

RIM uses gettext-format message files, specifically, a `.pot` file for the source template and a `.po` file for each target language. The `locale` directory of this repository uses the usual structure for a gettext `locale` directory; the message file for each language is called `rim.po`. We recommend that translators use [poedit](https://poedit.net/) to edit the `.po` files.

RIM is initially being translated to the following languages: French, German, Italian, Spanish, and Swedish. We have seeded the repository with machine translations for these languages. We understand that machine translations aren't ideal, but we believe they're useful as a starting point.

Some messages include variables, also known as parameters. These are indicated using the following syntax:

`%{controller_name}`

The above text indicates that a variable called `controller_name` should be substituted wherever that construct appears in the message. Note that the variable names **must not be translated**.

## Testing localizations

At this early stage in the localization of RIM, you'll need to use one of the following test builds:

* [Windows](https://download.pneumasolutions.com/rim/rim-l10n-test-setup.exe)
* [macOS](https://download.pneumasolutions.com/rim/rim-l10n-test.pkg)

We will soon include localization support in normal release builds of RIM, once we're confident that the localization infrastructure doesn't cause any regressions for current English-language users.

To test RIM localization, at least one environment variable must be set in the environment where the main RIM process is run. The `RIM_LOCALIZATION_ROOT` variable must be set to the absolute path of your checkout of this repository.

In addition, if you want to test a language other than your operating system's default language, you must set the `RIM_LANG` environment variable to the two-letter, lowercase language code for that language, e.g. `es` for Spanish or `sv` for Swedish.

Note that in a normal installation, RIM normally runs in the background. This means that you'll need to kill the main "Remote Incident Manager" process before starting an instance of RIM with the necessary environment variable(s) set.

### Windows

To run RIM with the necessary environment variable(s) set, you can either:
#### Use the command line
Open a command prompt, set the variable(s), and then launch RIM from there. We'll use Spanish as an example:  
`
cd "C:\Program Files\Remote Incident Manager"

$env:RIM_LOCALIZATION_ROOT = "%homepath%"\documents\github\rim-localization"

$env:RIM_LANG = "es"

`
At that point, running "Remote Incident Manager.exe" from your command prompt would start RIM with the Spanish translation running.

#### Via the Start Menu

Open the Start menu, search for "environment variables", and then set the variable(s) in the control panel that comes up in the search results.

### macOS

As far as we know, on macOS, the only option is to open Terminal, set the variable(s), and directly run the "Remote Incident Manager" executable (under the application's Contents/MacOS directory) from the Terminal. If you know of an easier way, please submit a pull request.
