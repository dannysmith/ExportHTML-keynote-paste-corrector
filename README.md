
# Sublime Text 3 ExportHTML Keynote Paste Corrector

When building Keynote or PowerPoint presentations, I've often wanted an easy way to copy and paste from Sublime Text 3 into the slides, maintaining just the font and sytax highlighting. Thanks to the [ExportHTML](https://github.com/facelessuser/ExportHtml) ST3 plugin and a bookmarklet, I now have it.

![Animation of export process](http://f.cl.ly/items/2z2w2L341t1u0g2H1N1v/mbVrhkJhw7.gif)

If you just want the bookmarklet, you can get it here: http://dannysmith.github.io/ExportHTML-keynote-paste-corrector/


## Browser Support

|         | Keynote | PowerPoint |
|---------|---------|------------|
| Safari  |    ✓   |      ✓     |︎
| Chrome  |    ✘   |      ✓     |︎
| Firefox |    ✘   |      ✓     |︎



## Installation & Setup

1. [Install Isaac Muses ExportHTML plugin for Sublime Text](http://facelessuser.github.io/ExportHtml/installation/).
2. [Visit this page](http://dannysmith.github.io/ExportHTML-keynote-paste-corrector/) and drag the bookmarklet to your bookmarks bar.
3. Setting up your theme
4. Set up your ExportHTML settings.



### Setting up `tmTheme` files

Sublime Text uses `.tmtheme` files. You can configure ExportHTML to use more than one theme when exporting, and then select your preferred one at the point you export it. I use the [Extended Railscasts](https://github.com/jevzee/sublime-railscasts-extended) theme by @jevzee, with a few minor changes. You can [edit and create theme files online](http://tmtheme-editor.herokuapp.com).

For the plugin and bookmarklet to work properly, you need to create a second version of your themes without background colours. I prefix those without background colours with `-nobackground`. Here's a diff of the original theme and the one with backgrounds removed:

![Diff of original theme and nobackground theme](http://f.cl.ly/items/2N2U2U3Y3c3G393g291a/Screen%20Shot%202016-03-02%20at%2002.22.42.png)

Once you've got your backgroundless theme sorted, you should save is somewhere in Sublime text's packages directory. The code below assumes it's in `/Packages/User`:

```
Packages/User/railscasts-extended-dannysmith-nobackground.tmTheme
```

### Your ExportHTML Settings

Open your ExportHTML User Settings file (*Sublime Text > Preferences > Package Settings*). There are a variety of [configuration options](http://facelessuser.github.io/ExportHtml/usage) available, but dince we're using ExportHTML just to copy/paste into keynote, we want the simplest settings possible.

Turn off numbers, browser print, gutters and header.

```json
{
  "html_panel": [
    {
      "Sparta Theme without Backgrounds": {
        "numbers": false,
        "browser_print": false,
        "color_scheme": "Packages/User/railscasts-extended-dannysmith-nobackground.tmTheme",
        "style_gutter": false,
        "no_header": true
      }
    }
  ]
}
```

You could also set up a key binding:

```json
  {
    "keys": ["ctrl+alt+super+n"],
    "command": "export_html",
    "args": {
          "numbers": false,
          "browser_print": false,
          "color_scheme": "Packages/User/railscasts-extended-dannysmith-nobackground.tmTheme",
          "style_gutter": false,
          "no_header": true
    }
  }
```


## Usage

1. Open the Sublime Text Command Palette and use the fuzzy search to find "Export to HTML: Show Export Menu".

![Screenshot](http://f.cl.ly/items/1N3C303c3A2D2N0Z2B1g/st_palette_exporthtml.png)

2.  Hit enter. You should see the export theme's you set up in the ExportHTML settings. Choose the right one and hit enter again.
3. This should open Safari showing your code.
4. Click the bookmarklet.
5. Select and copy the code from your browser (⌘ + A then ⌘ + C).
6. Paste into Keynote (⌘ + V) or "Paste Special" into PowerPoint for mac (^ + ⌘ + V then ⏎).

## Thanks
Obviously, thanks to Isaac Muse (@facelessuser) for making the ExportHTML plugin, which has saved me heaps of time.
