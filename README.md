# GitHub Homepage

My simplistic academic homepage. 

Template from: [@yaoyao-liu](https://github.com/yaoyao-liu) under [![LICENSE](https://img.shields.io/github/license/yaoyao-liu/minimal-light?style=flat-square&logo=creative-commons&color=EF9421)](https://github.com/yaoyao-liu/minimal-light/blob/main/LICENSE), known as [The Minimal Light Theme](https://github.com/yaoyao-liu/minimal-light). Itself derived from [minimal-light](https://github.com/Xiao-Chenguang/minimal-light), which is based on [minimal](https://github.com/orderedlist/minimal).


## Scope

- Simplicity
- [Jekyll](https://jekyllrb.com/docs/) site generator, automatically deployed by GitHub Pages
- Mobile friendly
- Markdown content editing
- Dark mode

## Repository Structure

```
.
├── _data                    
|   └── publications.yml                      # the YAML file for publications, holds the content
├── _includes                    
|   ├── publications.md                       # the Markdown file for publications, holds the logic to print content
|   └── awards.md                             # the Markdown file for awards
├── _layouts                  
|   └── homepage.html                         #  the html template for the homepage 
├── _sass
|   ├── minimal-light.scss                    #  this file will be compiled into a CSS file to control the style of the page              
|   └── minimal-light-no-dark-mode.scss       #  this file is similar to minimal-light.scss with the dark mode disabled
├── assets                                    #  css styles, images, and other files
├── _config.yml                               #  the Jekyll configuration file, including some options of the page  
├── .gitignore                                #  specifies intentionally untracked files
├── Gemfile                                   #  a RubyGems related file
├── index.md                                  #  the content of the index page, using Markdown
├── LICENSE                                   #  the license file
└── README.md                                 #  this readme file 
```

## License

This work is licensed under a [Creative Commons Zero v1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/deed.en) License.

## Acknowledgements

This project uses source code from the following repositories:

* [yaoyao-liu/minimal-light](https://github.com/yaoyao-liu/minimal-light)

* [pages-themes/minimal](https://github.com/pages-themes/minimal)

* [orderedlist/minimal](https://github.com/orderedlist/minimal)

* [al-folio](https://github.com/alshedivat/al-folio)
