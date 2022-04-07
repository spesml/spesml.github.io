---
nav_exclude: true
---
# Richtlinien zur Erstellung und Verwaltung der SpesML Webseiteninhalte
Diese Richtlinien und Anleitungen sollen dazu dienen, den SpesML Projektmitgliedern einen einfachen und schnellen Start in die Veröffentlichung und Verwaltung der SpesML Webseite - mithilfe von Guthub Pages und Jekyll - zu bieten und als Hilfestellung zu agieren. Diese Richtlinien geben eine Einleitung in den Static Site Generator(SSG) *Jekyll* und in die Veröffentlichung von Webinhalten als Markdown-Dateien. 

---
### Inhaltsverzeichnis
1. [Jekyll - ein Static Site Generator]()
---

## 1. Jekyll - ein Static Site Generator
Jekyll ist ein open source Software, die als Static Site Generator(SSG) zur automatisierten Erstellung einer statischen Webseite dient. 

## Das Github Repository
Die Webseite wird über das bereits vorhandene [Github Repository](https://github.com/spesml/spesml.github.io) verwaltet, gewartet und veröffentlicht.
The website is deployed using an already opened Github Repository and Github Pages. In order to guarantee an error-free deployment of the website, this chapter gives a brief introduction to the used Github repository and its folder structure.  
  
The Github repository that is used for the website files is available through https://github.com/spesml/spesml.github.io and via the branch "gh-pages" (set as default branch). All changes and uploads pushed to this branch are automatically detected and rendered by Github Pages. The deployment on the website usually takes up to 2 minutes.

### Structure of the repository
The repository is organised in a root directory (the repository itself) and a folder structure. The default branch for deployment is "gh-pages" and should be used for deployment of any file.  
  
![Choice of branch](/Docu/pics/branch_choice.png)  
  
All files already organised in the root directory need to remain in this directory and shall be updated diectly via Github. These files contain the website configurations and all plugins needed for the correct deployment of the website. A precise description of those files is given in ...
The root files are showed in the following picture.  
  
 
