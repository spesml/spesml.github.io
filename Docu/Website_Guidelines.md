---
nav_exclude: true
---
# Richtlinien zur Erstellung und Verwaltung der SpesML-Webseiteninhalte
Diese Richtlinien und Anleitungen sollen dazu dienen, den SpesML Projektmitgliedern einen schnellen Start in die Veröffentlichung und Verwaltung der [SpesML Webseite](https://spesml.github.io) - mithilfe von Guthub Pages und Jekyll - zu bieten und als Hilfestellung zu agieren. Diese Richtlinien geben eine Einleitung in den Static Site Generator *Jekyll* und in die Veröffentlichung von Webinhalten als *Markdown*-Dateien. 

---
### Inhaltsverzeichnis
1. [Jekyll - ein Static Site Generator](https://github.com/spesml/spesml.github.io/blob/gh-pages/Docu/Website_Guidelines.md#1-jekyll---ein-static-site-generator)
2. [Github Repository](https://github.com/spesml/spesml.github.io/blob/gh-pages/Docu/Website_Guidelines.md#2-github-repository)
3. [Jekyll-Konfigurationen bei der SpesML-Webseite](https://github.com/spesml/spesml.github.io/blob/gh-pages/Docu/Website_Guidelines.md#3-jekyll-konfigurationen-bei-der-spesml-webseite)
---

## 1. Jekyll - ein Static Site Generator
Jekyll ist eine open source Software, die als Static Site Generator (SSG) zur automatisierten Erstellung einer statischen Webseite dient und wurde 2008 von Tom Preston-Werner veröffentlicht. Da es sich um einen SSG handelt, verwendet Jekyll keine Datenbanken, um dynamische Webseiten zu generieren. Einstellungen und Konfigurationen werden Jekyll als *YAML*-, *JSON*-, *CSV*- und/oder *TSV*-Dateien übergeben.  
  
Jekyll ist das Engine, das hinter Github Pages steht, wodurch über Jekyll generierte Webseiten über den Hostingservice von Github veröffentlicht werden können. Jekyll kann auch lokal installiert und verwendet werden. Eine Nutzung von Jekyll in Kombination mit einem Webframework (z.B. Bootstrap oder Semantic UI) ist ebenfalls möglich und die generierten Webseiten können mit cloudbasierter CMS-Software verknüpft werden, die eine Editierung von Webcontent ohne Programmierkenntnisse ermöglicht.  
  
Weitere Informationen zu Jekyll gibt es im zugehörigen [Github Repository](https://github.com/jekyll/jekyll) und auf der [Jekyll-Webseite](https://jekyllrb.com/).

## 2. Github Repository
Die Webseite wird über das bereits vorhandene [Github Repository](https://github.com/spesml/spesml.github.io) verwaltet, gewartet und veröffentlicht. Die genutzte Branch ist "gh-pages". Alle in dieser Branch hochgeladenen und veränderten Inhalte werden von Github Pages automatisch erkannt, verarbeitet und gemäß der abgelegten Jekyll-Konfiguration (siehe *_config.yml*) veröffentlicht. Dies bedarf keiner manuellen Veröffentlichung und keiner Kenntnisse in der Programmierung von CI/CD-Pipelines in Github.

### Struktur des Repository
In diesem Abschnitt wird die Struktur des genutzten Repository vorgestellt. Ein Repository besteht standardmäßig aus einem Hauptverzeichnis (Root Directory), in dem Dateien abgelegt und weitere Ordner angelegt werden können. Jede Branch verfügt über ein eigenes Hauptverzeichnis und entsprechende - wenn angelegt - Unterordner. Um die fehlerfreie und korrekte Übernahme der zu veröffentlichenden Inhalte zu gewährleisten, müssen diese in der bereits angelegte Branch "gh-pages" abgelegt werden.
  
![Struktur des Repository](/Docu/GitStruktur.png)  
  
Die Ordnerstruktur im Hauptverzeichnis richtet sich nach der Navigationsstruktur der Webseite. Für jede Hauptseite wurde ein eigener Unterordner angelegt. Da Github Pages das ganze Hauptverzeichnis der Branch überprüft, können die Unterordner in beliebig viele weitere Unterordner aufgeschlüsselt werden.  
  
Damit Github Pages die Jekyll-Konfigurationen und die Indexseite verarbeiten kann, müssen die Konfigurationsdateien, die Gemfiles sowie die Markdown-Datei der Indexseite im Hauptverzeichnis abgelegt werden und dürfen nicht in einen Unterordner verschoben oder umbenannt werden (siehe folgendes Bild).  
  
![Dateien im Hauptverzeichnis](/Docu/Dateien.png)  
  
### Actions
Im Reiter "Actions" werden alle aktuellen und vergangenen Workflows aufgezeigt. Workflow sind Anweisungsabfolgen, die von Github abgearbeitet werden, um beispielsweise über Github Pages eine Seite zu veröffentlichen. In diesem Reiter kann der Fortschritt der einzelnen Workflows verfolgt werden und Fehler untersucht werden.  
  
![Workflows in Github](/Docu/Workflows.png)  
  
Beim Auftreten eines Fehlers kann es unter Umständen zum Abbruch eines Workflows kommen. Der Fehler kann durch die Detailansicht des betroffenen Workflows ausgewertet und untersucht werden.  
  
![Workflowfehler](/Docu/Fehler.png)  
  
## 3. Jekyll-Konfigurationen bei der SpesML-Webseite
Die SpesML-Webseite wird mithilfe von Jekyll generiert und über Github Pages veröffentlicht. Um eine korrekte Darstellung der Webseite zu gewährleisten, müssen Jekyll bestimmte Informationen zur Konfiguration der Webseite mitgeteilt werden. Hierfür wird die im Hauptverzeichnis abgelegte YAML-Datei *_config.yml* verwendet. Diese Datei beinhaltet alle Konfigurationsinformationen, die für die Generierung der Webseite benötigt werden. Hierzu gehören unter anderem der titel der Webseite, das Logo der Webseite, das verwendete Layout (bzw. Theme) oder auch einstellen zu Suchfunktionen. Die folgenden Abschnitte geben einen Überblick über das verwendete Layout/theme und über die genutzten Konfigurationen.

### *Just the Docs*-Theme
Die spesML-Webseite baut auf dem open source Jekyll-Theme "Just the Docs" von *pmarsceill* auf und ist im Github Repository [just-the-docs/just-the-docs](https://github.com/just-the-docs/just-the-docs) erhältlich. Das Theme ist ein Layout, das sich unter anderem zur Dokumentation von Projekterfolgen eignet und viele Features bietet.  
  
Damit Jekyll und Github Pages die Webseite mit diesem Layout veröffentlichen kann, ist es notwendig das Layout in der Konfigurationsdatei festzulegen. Da das Theme selbst in Github abgelegt ist, ist der einfachste Weg zur Einbindung des Layouts die Nutzung als *remote-theme*. Hierfür wird in der Datei *_config.yml* folgende Codezeile eingetragen
  
```yaml
remote_theme: just-the-docs/just-the-docs
```  
  
Mit diesem Vorgehen können alle im Github abgelegten Themes unkompliziert eingebunden werden.  
  
Das Layout kann auch lokal verwendet werden. Hierfür muss das Theme in die Jekyll-Gemfile intergriert werden. Die entsprechende Codezeile lautet:

```ruby
gem "just-the-docs"
```  
  
Zusätzlich muss in *_config.yml* das Theme definiert werden:

```yaml
theme: just-the-docs
```  
  
Über ```$ bundle``` oder ```$ gem install just-the-docs``` kann das Layout schließlich lokal installiert und genutzt werden.  
  
Um eine korrekte Darstellung der Webseite und des Layouts zu gewährleisten, wird empfohlen die aktuellen Konfigurationseinstellungen unter *_config.yml* beizubehalten. Weiterführende Informationen zur Nutzung und Konfiguration des Themes gibt es auf [Github](https://github.com/just-the-docs/just-the-docs) und auf https://pdmosses.github.io/just-the-docs/. 

### Konfigurationsdatei *_config.yml*
