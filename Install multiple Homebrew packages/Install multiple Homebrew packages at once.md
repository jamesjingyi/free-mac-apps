# Install multiple Homebrew packages at once

Before starting, ensure Homebrew is installed correctly by typing `brew`. If it doesn't work, follow their instructions [here](https://brew.sh) (ensure you do the final instructions after running the command!)

1. Open TextEdit, and create a new document

2. Go to `Format` → `Make Plain Text`

![Menu bar selection of Format, Make Plain Text](https://i.imgur.com/d4AhNqi.png)

3. Add in the syntax after `brew install` in the Formulae, each on a new line (e.g. `brew install --cask utm` becomes `--cask utm` and `brew install macfuse` becomes `macfuse`) — An example file can be found [here](https://github.com/jamesjingyi/free-mac-apps/blob/b59b68026b1604ad9f99f0fcebe7f274d81963c6/Install%20multiple%20Homebrew%20packages/packages.txt)


![An example of what a file might look like once formulae has been added](https://i.imgur.com/hPQUzSx.png)

4. Save this as `packages.txt` somewhere (I put it in my Downloads folder)

5. Open Terminal and type `brew install $(cat`, then to avoid having to find the file, drag in your `packages.txt` file. Close this command with a `)` (I used the Downloads folder so my final command looked like this: `brew install $(cat /Users/jamesjingyi/Downloads/packages.txt)`)

6. Let Homebrew do its magic!

# Install multiple Mac App Store packages at once

Before starting, this requires the `mas` package to be installed via Homebrew (`brew install mas`) and you have to be logged in to the Mac App Store. You can do this by opening the App Store (the `mas signin` command no longer works).

> Reinstalling a Mac? Find your Mac App Store Apps by using the System Information app (you can search for it as an app or go to `` > `About This Mac` > `More Info...` > `System Report...` > `System Information`), then go to `Software` > `Applications` and use the `Obtained from` header to sort by `App Store`.

My current setup is using `mas install` to get my previously purchased/installed apps. I do this recursively through my `mas-apps.txt` file using the command:

`grep -v '^\s*#' apps.txt | awk '{print $1}' | xargs -n 1 mas install`

Breakdown:

1. `grep -v '^\s*#' apps.txt` - Removes any lines starting with # (so I can comment them out), or empty lines

2. `awk '{print $1}'` - Extracts only the first field (the app ID), ignoring everything after it

3. `xargs -n 1 mas install` - Passes the cleaned app IDs one by one to `mas install`

## `mas-apps.txt` setup:

I have set up this file with two columns, the `app-id` and it's name. The name is only there to help me identify whether I still want it. This is why the above command is a bit more complex.

## Adjusting to `purchase` rather than `install`

You could adjust this to 'purchase' (which doesn't actually buy things, only gets free things - see the [mas documentation](https://github.com/mas-cli/mas)):

`grep -v '^\s*#' apps.txt | awk '{print $1}' | xargs -n 1 mas purchase`

Note: You also need to be logged in to use this command