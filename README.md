# RIM Localization

This repository is the hub for the localization of [Remote Incident Manager](https://getrim.app/) from Pneuma Solutions.

## Message files

RIM uses gettext-format message files, specifically, a `.pot` file for the source template and a `.po` file for each target language. The `locale` directory of this repository uses the usual structure for a gettext `locale` directory; the message file for each language is called `rim.po`. We recommend that translators use [poedit](https://poedit.net/) to edit the `.po` files.

### RIM for iOS

RIM for iOS says a number of things the desktop app has never had to, so it has a second message file per language, `rim-ios.po`, with `rim-ios.pot` as its template. Anything the two apps say identically stays in `rim.po` and is shared; only the strings with no desktop equivalent live here. Keeping them apart means regenerating `rim.pot` from the desktop sources can never drop them.

Both files are translated the same way and there is nothing extra to install. A message left untranslated in `rim-ios.po` falls back to English on its own, one string at a time, so partial progress is genuinely useful.

RIM is initially being translated to the following languages: French, German, Italian, Spanish, and Swedish. We have seeded the repository with machine translations for these languages. We understand that machine translations aren't ideal, but we believe they're useful as a starting point.
### A Note about Variables
Some messages include variables, also known as parameters. These are indicated using the following syntax:

`%{controller_name}`

The above text indicates that a variable called `controller_name` should be substituted wherever that construct appears in the message. Note that the variable names **must not be translated**.

Messages in `rim-ios.po` use Apple's spelling for the same idea, because that is what the app itself is written in:

- `%@` is a piece of text, such as a machine name.
- `%lld` and `%u` are numbers.
- `%1$@` and `%2$@` are numbered, and appear when a message takes more than one variable.

Where a message is numbered, **keep the numbers on the right variables** if your language puts them in a different order — `%2$@ … %1$@` is how you say "these two have swapped places". A message with only one variable needs no number.

If you would rather write these as `%{name}`, that works too; the iOS import accepts either. What it cannot do is guess a reordering of unnamed variables, so please use the numbered form when the order changes.

## Testing localizations

The localization infrastructure and initial machine translations are now available in the current version of RIM. You can set the UI language using the "Language" button in the "Provide Help" or "Receive Help" window in the RIM app.

To test your own changes to RIM message files, an environment variable must be set in the environment where the main RIM process is run. Specifically, the `RIM_LOCALIZATION_ROOT` variable must be set to the absolute path of your checkout of this repository.

Note that in a normal installation, RIM normally runs in the background. This means that you'll need to kill the main "Remote Incident Manager" process before starting an instance of RIM with the environment variable set.

If you want to test a message file for a language that isn't yet included in release builds of RIM, you'll also need to set the `RIM_LANG` environment variable to the short code for that language. For example, if you were testing a new message file for Russian, you would set `RIM_LANG` to `ru`.

### Windows

To run RIM with the environment variable set, you can either:
#### Use the command line
Open a command prompt, set the variable(S), and then launch RIM from there. As an example, we'll assume that you left the repository's path at Github's default choice:  

```
cd "C:\Program Files\Remote Incident Manager"
$env:RIM_LOCALIZATION_ROOT = "%homepath%"\documents\github\rim-localization"
```

At that point, running "Remote Incident Manager.exe" from your command prompt would start RIM with your current working copy of the message files.

#### Via the Control Panel

Open the Start menu, search for "environment variables", and then set the variable in the control panel that comes up in the search results.

### macOS

As far as we know, on macOS, the only option is to open Terminal, set the variable, and directly run the "Remote Incident Manager" executable (under the application's Contents/MacOS directory) from the Terminal. If you know of an easier way, please submit a pull request.
## Creating a New Language
IN order to create a new language, you'll want to do the following:
1. Open Poedit.
1. Select "New from POT/PO file…" off the file menu.
1. Locate and select the rim.pot file.
1. Select the target language from the list, then click "ok."
<!-- end -->
At this point, you now have a blank language file labeled with the language code of the language you specified. When saving this:
1. Go to the "Locale" directory.
1. Create a new folder with the language code of your new language, I.E. ru.
1. Once inside that folder, create a new folder called "LCMessages". This is where you will save your .po file.
<!-- end -->