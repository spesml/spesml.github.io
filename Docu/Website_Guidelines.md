---
nav_exclude: true
---
# Richtlinien zur Erstellung und Verwaltung der SpesML Webseiteninhalte
Diese Richtlinien und Anleitungen sollen dazu dienen, den SpesML Projektmitgliedern einen einfachen und schnellen Start in die Veröffentlichung und Verwaltung der [SpesML Webseite](https://spesml.github.io) - mithilfe von Guthub Pages und Jekyll - zu bieten und als Hilfestellung zu agieren. Diese Richtlinien geben eine Einleitung in den Static Site Generator *Jekyll* und in die Veröffentlichung von Webinhalten als *Markdown*-Dateien. 

---
### Inhaltsverzeichnis
1. [Jekyll - ein Static Site Generator](https://github.com/spesml/spesml.github.io/blob/gh-pages/Docu/Website_Guidelines.md#1-jekyll---ein-static-site-generator)  
---

## 1. Jekyll - ein Static Site Generator
Jekyll ist eine open source Software, die als Static Site Generator (SSG) zur automatisierten Erstellung einer statischen Webseite dient und wurde 2008 von Tom Preston-Werner veröffentlicht. Da es sich um einen SSG handelt, verwendet Jekyll keine Datenbanken, um dynamische Webseiten zu generieren. Einstellungen und Konfigurationen werden Jekyll als *YAML*-, *JSON*-, *CSV*- und/oder *TSV*-Dateien übergeben.  
  
Jekyll ist das Engine, das hinter Github Pages steht, wodurch über Jekyll generierte Webseiten über den Hostingservice von Github veröffentlicht werden können. Jekyll kann auch lokal installiert und verwendet werden. Eine Nutzung von Jekyll in Kombination mit einem Webframework (z.B. Bootstrap oder Semantic UI) ist ebenfalls möglich und die generierten Webseiten können mit cloudbasierter CMS-Software verknüpft werden, die eine Editierung von Webcontent ohne Programmierkenntnisse ermöglicht.  
  
Weitere Informationen zu Jekyll gibt es im zugehörigen [Github Repository](https://github.com/jekyll/jekyll) und auf der [Jekyll-Webseite](https://jekyllrb.com/).

## 2. Github Repository
Die Webseite wird über das bereits vorhandene [Github Repository](https://github.com/spesml/spesml.github.io) verwaltet, gewartet und veröffentlicht. Die genutzte Branch ist "gh-pages". Alle in dieser Branch hochgeladenen und veränderten Inhalte werden von Github Pages automatisch erkannt, verarbeitet und gemäß der abgelegten Jekyll-Konfiguration (siehe *_config.yml*) veröffentlicht. Dies bedarf keiner manuellen Veröffentlichung und keiner Kenntnisse in der Programmierung von CI/CD-Pipelines in Github.

### Struktur des Repository
In diesem Abschnitt wird die Struktur des genutzten Repositorys vorgestellt. Ein Repository besteht standardmäßig aus einem Hauptverzeichnis (Root Directory), in dem Dateien abgelegt und weitere Ordner angelegt werden können. Jede Branch verfügt über ein eigenes Hauptverzeichnis und entsprechende - wenn angelegt - Unterordner. Um die fehlerfreie und korrekte Übernahme der zu veröffentlichenden Inhalte zu gewährleisten, müssen diese in die bereits vorgestellte Branch "gh-pages" abgelegt werden.
  
![Choice of branch](/Docu/pics/branch_choice.png)  
  
 
  
 
