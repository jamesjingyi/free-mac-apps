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
