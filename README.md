# RIM Localization

This repository is the hub for the localization of [Remote Incident Manager](https://getrim.app/) from Pneuma Solutions.

## Message files

RIM uses gettext-format message files, specifically, a `.pot` file for the source template and a `.po` file for each target language. The `locale` directory of this repository uses the usual structure for a gettext `locale` directory; the message file for each language is called `rim.po`. We recommend that translators use [poedit](https://poedit.net/) to edit the `.po` files.

RIM is initially being translated to the following languages: French, German, Italian, Spanish, and Swedish. We have seeded the repository with machine translations for these languages. We understand that machine translations aren't ideal, but we believe they're useful as a starting point.

Some messages include variables, also known as parameters. These are indicated using the following syntax:

`%{controller_name}`

The above text indicates that a variable called `controller_name` should be substituted wherever that construct appears in the message. Note that the variable names **must not be translated**.

## Testing localizations

The localization infrastructure and initial machine translations are now available in the current version of RIM. You can set the UI language using the "Language (BETA)" button in the "Provide Help" or "Receive Help" window in the RIM app.

To test your own changes to RIM message files, an environment variable must be set in the environment where the main RIM process is run. Specifically, the `RIM_LOCALIZATION_ROOT` variable must be set to the absolute path of your checkout of this repository.

Note that in a normal installation, RIM normally runs in the background. This means that you'll need to kill the main "Remote Incident Manager" process before starting an instance of RIM with the environment variable set.

If you want to test a message file for a language that isn't yet included in release builds of RIM, you'll also need to set the `RIM_LANG` environment variable to the short code for that language. For example, if you were testing a new message file for Russian, you would set `RIM_LANG` to `ru`.

### Windows

To run RIM with the environment variable set, you can either:
#### Using the command line
Open a command prompt, set the variable, and then launch RIM from there. As an example, we'll assume that you left the repository's path at Github's default choice:  

```
cd "C:\Program Files\Remote Incident Manager"
$env:RIM_LOCALIZATION_ROOT = "%homepath%"\documents\github\rim-localization"
```

At that point, running "Remote Incident Manager.exe" from your command prompt would start RIM with your current working copy of the message files.

#### Via the Control Panel

Open the Start menu, search for "environment variables", and then set the variable in the control panel that comes up in the search results.

### macOS

As far as we know, on macOS, the only option is to open Terminal, set the variable, and directly run the "Remote Incident Manager" executable (under the application's Contents/MacOS directory) from the Terminal. If you know of an easier way, please submit a pull request.
