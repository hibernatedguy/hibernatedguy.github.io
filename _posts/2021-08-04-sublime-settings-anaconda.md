---
layout: post
title: Sublime setup for python/django development
description: Setup sublime for python/django development.
summary: Setup sublime for python/django development.
tags: python
minute: 2
---
I assume that you know about sublime-package installation by using ```ctrl+shift+p``` 


**[1]**. Install Anaconda package for better linting and use the below setttings to disable few startup warnings and change pep8 max-line error.

Edit ```Preferences > Package Settings >  Anaconda > Settings - User ```
<br/>
```.md
{
    "swallow_startup_errors": true,

    /*
        If 'outline' (default), anaconda will outline error lines.
        If 'fill', anaconda will fill the lines.
        If 'solid_underline', a solid underline below regions.
        If 'stippled_underline', a stippled underline below regions.
        If 'squiggly_underline', a squiggly underline below regions.
        If 'none', anaconda will not draw anything on error lines.
    */
    "anaconda_linter_mark_style": "squiggly_underline",
    "pep8_max_line_length": 79,
    "python_interpreter": "/your-python-path/usr/local/bin/python",
} 
```
  ->> [Official Anaconda Installation Guide ](http://handlebarsjs.com/)

**[2]**. Install FiraCode : one of my favorite font after monaco font.


```.md
sudo apt install fonts-firacode
```
 -> [FiraCode github repo ](https://github.com/tonsky/FiraCode)


**[3]**. Install djaneiro, gitgutter and html-css-js-prettify.

Hit ```ctrl+shift+p``` and type package name listed below and hit ```Enter```.

```.txt
djaneiro : Syntax highlighting and django snippets
gitgutter : git history
html-css-js-prettify : formatting our HTML, CSS and JS code
```
 ->> [click here for more packages ](https://micropyramid.medium.com/ten-sublime-plugins-useful-for-your-daily-python-django-development-448f9407499b)



**[4]**. Install GithubDark theme and change your sublime's user-settings.
Edit ``` Preferences > Settings```

  ->> [Install Github Dark Theme ](https://github.com/mauroreisvieira/github-sublime-theme/)

```.md
{
    "rulers": [80, 100, 120],
    "font_face": "Fira Code",
    "font_options": ["antialias"],
    "theme_font_options": [ "gray_antialias"],
    "ignored_packages":
    [
        "Vintage",
    ],
    "theme": "SoDaReloaded Dark.sublime-theme",
    "color_scheme": "Packages/GitHub Theme/schemes/GitHub Dark.sublime-color-scheme",
    "font_size": 9,
    "show_full_path": true,
    "detect_indentation": true,
    "tab_size": 4,
    "translate_tabs_to_spaces": true,
    "draw_white_space": "all",
 }
```