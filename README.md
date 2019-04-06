# rEFInd theme Regular Dark

A simplistic clean and minimal theme for rEFInd

NOTE: this is a fork to create a dark mode/theme.
However, the operating system logo icons have not been updated to constrast with a dark background.
Windows and Ubuntu look fine, and many others should be fine too.

![Screenshot](https://i.imgur.com/0AEk8BF.png)

<p align="center">(press F10 to take a screenshot at the boot screen, which gets saved to <code>/boot/efi</code>)</p>

### Installation [Quick]:

Just paste this command in your terminal:
```
bash <(curl -s https://raw.githubusercontent.com/1j01/refind-theme-regular/master/Install.sh)
```

### Installation [Manual]:

1. Clone git repository to your `$HOME` directory.
   ```
   git clone https://github.com/1j01/refind-theme-regular.git
   ```

2. Locate refind directory under EFI partition. For most Linux based system is commonly `/boot/efi/EFI/refind/`. Copy theme (repo) directory to it.

   **Important:** Delete older installed versions of this theme before you proceed any further.

   ```
   sudo rm -rf /boot/efi/EFI/refind/{regular-theme,refind-theme-regular}
   ```
   ```
   sudo cp -r refind-theme-regular /boot/efi/EFI/refind/
   ```
3. Remove unused directories.
   ```
   sudo rm -rf /boot/efi/EFI/refind/refind-theme-regular/{src,.git}
   ```

4. To adjust icon size and font size edit `theme.conf`.
   ```
   sudo nano /boot/efi/EFI/refind/refind-theme-regular/theme.conf
   ```

5. To enable the theme add `include refind-theme-regular/theme.conf` at the end of `refind.conf`.
   ```
   sudo nano /boot/efi/EFI/refind/refind.conf
   ```

### Contribute new icons:

0. Fork this repository on github and then git clone your fork of this repository in your Linux system

1. The icons must be in svg format to allow easy generation of icons at any scale, canvas size must have width and height 128 px for OS icons, or 48 px for tool icons. The actual icon in the svg file should roughly fit in a square with a side of 96 px or 20 px (for OS and tool icons, respectively). Inkscape is a good program to create and work with svg files.

2. Copy/save the svg file to `/src/svg/big` or `/src/svg/small` (depending on what is more appropriate) and rename them to be consistent with others.

3. Install inkskape and optipng in your linux system as they will be needed to process the icons by the next step.

4. `cd` into the `./src` directory and run the script `./render_bitmaps.sh` that will process the svg files and generate the png files at various sizes.

5. Copy the png icons you generated from their `/src/bitmap` subfolder into the appropriate `/icons` subfolders for their size by running `./copy-bitmap.sh`

6. Commit your changes, upload to your fork and then open a PR.


### TODO

- Use `git remote add boot /boot/efi/EFI/refind/refind-theme-regular` to manage installed copy in development (and maybe for the quick install as well) (then you can just `git push boot master` to it)
- Use a `themes` dir inside `refind`
- Make dark theme live alongside light, installable from the same repo (or in separate repos but sharing tooling?)
- Add an option for stretching all icons by some ratio to counteract a misproportioned boot screen (when your native monitor resolution is unavailable)
- Make it clear from the directory structure what files are generated (at least via READMEs but maybe by naming the folder "built" or "derived" or "generated")

### More information

[The official rEFInd website](http://www.rodsbooks.com/refind/)

