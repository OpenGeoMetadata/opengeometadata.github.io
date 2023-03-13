# opengeometadata.github.io


## About

This site contains documentation about OpenGeoMetadata schemas and repositories.



### Written in: [Markdown language](https://daringfireball.net/projects/markdown/)

[Markdown](https://daringfireball.net/projects/markdown/) is a lightweight and easy-to-use language for text documents.
Most text editors support it and translates easily to other formats, such as HTML or PDF or EPUB.

### Generated with: [MkDocs framework ](https://www.mkdocs.org)

[MkDocs](https://www.mkdocs.org) is a static site generator platform that allows users to create and maintain documentation websites. It takes Markdown files and uses the [Python-Markdown library](https://python-markdown.github.io) to convert the documents to HTML.

### Styled with: [Material for MkDocs theme](https://squidfunk.github.io/mkdocs-material/)

[Material](https://squidfunk.github.io/mkdocs-material/) is the most actively developed theme available for MkDocs (as of 2023) and features flexible navigation and many plugins to extend what we can do with Markdown. It is called "Material" because it is based on Google's Material Design guidelines, a web accessibility and screen responsiveness.


### Published with: [GitHub Pages](https://pages.github.com)

[GitHub Pages](https://pages.github.com) is a free static site hosting service offered by GitHub. It is often used to host documentation sites, personal portfolios, and project websites.


## Updating the OpenGeoMetadata website

### Workflow overview

1. Make changes on a branch
2. Merge changes to the **Main** branch
3. Use a local command line to publish to the **GitHub Pages** branch.

This workflow may vary from how you collaborated on other GitHub Pages sites, because we don't do Pull Requests to the branch that is actually being published (gh-pages). It is always published from a command line interfaces using `mkdocs gh-deploy`

### GitHub Repository organization:

#### Main Branch

* **readme.md**: the file you are reading right now
* **mkdocs.yml**: the configuration file that identifies the theme, the extensions and the navigation
* **docs** folder
	*  	/images : JPGs, PNGs, and other image files
	*   /javascripts : extensions using javascipt (currently this is where the tableSort function lives)
	*   /ogm-aardvark: a subfolder with markdown files for each element in the Aardvark schema
	*   /stylesheets/extra.css : a CSS file that can define colors, fonts, and other customizations for the site
	*   /tables : CSV files for any information to be included in tables
* Markdown documents: The content for the site. These can all live in the same directory and are organized in the public navigation menu in the nav section of **mkdocs.yml**.



MkDocs offers two commands to run in Terminal/Command Line for simplifying the process of editing and publishing GitHub pages:

* `mkdocs serve`: this will start a local server so you can preview the site as you build it. 

* `mkdocs gh-deploy`: this will convert all of the Markdown documents to HTML and publish them to a branch called **gh-pages**.






### Workflow steps

Part 1.
1. Update your local instance of the OpenGeoMetadata repository
2. Make a new branch and switch to it
3. Edit the Markdown files
4. Preview the site locally using `mkdocs serve`
5. Commit your changes
6. Publish your branch
7. Open a Pull Request to the main branch

Part 2.
1. Accept Pull Request and merge changes to the main branch
2. Update your local instance of the OpenGeoMetadata repository
3. Stay or switch to the MAIN branch
4. Preview the site locally using `mkdocs serve`
5. Publish to GitHub with `mkdocs gh-deploy`




















------

All questions about this repository and contributing to it or other elements of the OpenGeoMetadata project can be directed to geoblacklight-working-group@googlegroups.com.
