# VoiceOver Tester

This script simulates various VoiceOver actions on a webpage and prints a log of the information passed to the screen reader. You can run this tester on Firefox Nightly, Nightly Debug, or Safari. This tester supports live web pages as well as sample web files (html, xhtml, etc).

## How do I use it?

Download the AppleScript file from this directory. Using terminal, navigate to your downloads (or wherever you've placed the script). To test, run the following:

`osascript VoiceOver_Tester.scpt [browser] [input] [file path or site flag] [site]`

### browser

Pass the single letter corresponding to the browser you'd like to run your tester on:
- `f` = Firefox Nightly
- `d` = Nightly Debug
- `s` = Safari

### input

Pass the (relative) path to the text file containing your VoiceOver actions. These will be translated into key presses as the script runs. The currently supported actions are:
- next (VO + right)
- prev (VO + left)
- in (VO + shift + down)
- out (VO + shift + up)
- activate (VO + space)
- web (VO + CMD + f)

"Web" is a little hack-y, but it attempts to skip the browser UI and navigate directly to web content. It's a good idea to place this at the start of your input file if you're testing a website and not the browser chrome.

### Files vs. Sites

Because launching files differs from launching live websites in AppleScript, the script requires that you indicate what kind of path you're passing as an argument. If you'd like to pass a live website, your third argument should be `-s` and your fourth argument should be the website URL (ex. https://google.com). If you'd like to pass a local file (ex. sample.html), the relative path to your local file should be the third argument, and your fourth argument should be empty.

## Reading Logs

Each run should add lines to the `output.txt` log file in this directory. The top of each run should be headed by the browser it was run on (ex. `==== Safari`).

## Troubleshooting

You may need to give AppleScript / Terminal permission to synthesize key presses. You should be prompted to do this on the first run, if necessary. You can change these settings in System Preferences > Accessibility > Keyboard.
