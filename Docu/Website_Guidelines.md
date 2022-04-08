---
nav_exclude: true
---
# Richtlinien zur Erstellung und Verwaltung der SpesML-Webseiteninhalte
Diese Richtlinien und Anleitungen sollen dazu dienen, den SpesML Projektmitgliedern einen schnellen Start in die Veröffentlichung und Verwaltung der [SpesML Webseite](https://spesml.github.io) - mithilfe von Guthub Pages und Jekyll - zu bieten und als Hilfestellung zu agieren. Diese Richtlinien geben eine Einleitung in den Static Site Generator *Jekyll* und in die Veröffentlichung von Webinhalten als *Markdown*-Dateien. 

---
### Inhaltsverzeichnis
1. [Jekyll - ein Static Site Generator](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#1-jekyll-ein-static-site-generator)
2. [Github Repository](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#2-github-repository)
    1. [Struktur des Repository](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#21-struktur-des-repository)  
    2. [Actions](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#22-actions)
3. [Jekyll-Konfigurationen bei der SpesML-Webseite](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#3-jekyll-konfigurationen-bei-der-spesml-webseite)  
    1. [*Just the Docs*-Theme](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#31-just-the-docs-theme)
    2. [Konfigurationsdatei *_config.yml*](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#32-konfigurationsdatei-_configyml)
    3. [Gemfile](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#33-gemfile)
4. [Veröffentlichen mit Markdown-Dateien](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#4-ver%C3%B6ffentlichen-mit-markdown-dateien)  
    1. [Erstellung von Markdown-Dateien](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#41-erstellung-von-markdown-dateien)  
    2. [Front Matter für Markdown](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#42-front-matter-f%C3%BCr-markdown)
5. [Kontakt](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#5-kontakt)
---

## 1. Jekyll - ein Static Site Generator
Jekyll ist eine open source Software, die als Static Site Generator (SSG) zur automatisierten Erstellung einer statischen Webseite dient und wurde 2008 von Tom Preston-Werner veröffentlicht. Da es sich um einen SSG handelt, verwendet Jekyll keine Datenbanken, um dynamische Webseiten zu generieren. Einstellungen und Konfigurationen werden Jekyll als *YAML*-, *JSON*-, *CSV*- und/oder *TSV*-Dateien übergeben.  
  
Jekyll ist das Engine, das hinter Github Pages steht, wodurch über Jekyll generierte Webseiten über den Hostingservice von Github veröffentlicht werden können. Jekyll kann auch lokal installiert und verwendet werden. Eine Nutzung von Jekyll in Kombination mit einem Webframework (z.B. Bootstrap oder Semantic UI) ist ebenfalls möglich und die generierten Webseiten können mit cloudbasierter CMS-Software verknüpft werden, die eine Editierung von Webcontent ohne Programmierkenntnisse ermöglicht.  
  
Weitere Informationen zu Jekyll gibt es im zugehörigen [Github Repository](https://github.com/jekyll/jekyll) und auf der [Jekyll-Webseite](https://jekyllrb.com/).

## 2. Github Repository
Die Webseite wird über das bereits vorhandene [Github Repository](https://github.com/spesml/spesml.github.io) verwaltet, gewartet und veröffentlicht. Die genutzte Branch ist "gh-pages". Alle in dieser Branch hochgeladenen und veränderten Inhalte werden von Github Pages automatisch erkannt, verarbeitet und gemäß der abgelegten Jekyll-Konfiguration (siehe *_config.yml*) veröffentlicht. Dies bedarf keiner manuellen Veröffentlichung und keiner Kenntnisse in der Programmierung von CI/CD-Pipelines in Github.

### 2.1. Struktur des Repository
In diesem Abschnitt wird die Struktur des genutzten Repository vorgestellt. Ein Repository besteht standardmäßig aus einem Hauptverzeichnis (Root Directory), in dem Dateien abgelegt und weitere Ordner angelegt werden können. Jede Branch verfügt über ein eigenes Hauptverzeichnis und entsprechende - wenn angelegt - Unterordner. Um die fehlerfreie und korrekte Übernahme der zu veröffentlichenden Inhalte zu gewährleisten, müssen diese in der bereits angelegte Branch "gh-pages" abgelegt werden.
  
![Struktur des Repository](/Dokumentation%20zur%20Webseite/pics/GitStruktur.png)  
  
Die Ordnerstruktur im Hauptverzeichnis richtet sich nach der Navigationsstruktur der Webseite. Für jede Hauptseite wurde ein eigener Unterordner angelegt. Da Github Pages das ganze Hauptverzeichnis der Branch überprüft, können die Unterordner in beliebig viele weitere Unterordner aufgeschlüsselt werden.  
  
Damit Github Pages die Jekyll-Konfigurationen und die Indexseite verarbeiten kann, müssen die Konfigurationsdateien, die Gemfiles sowie die Markdown-Datei der Indexseite im Hauptverzeichnis abgelegt werden und dürfen nicht in einen Unterordner verschoben oder umbenannt werden (siehe folgendes Bild).  
  
![Dateien im Hauptverzeichnis](/Dokumentation%20zur%20Webseite/pics/Dateien.png)  
  
### 2.2. Actions
Im Reiter "Actions" werden alle aktuellen und vergangenen Workflows aufgezeigt. Workflow sind Anweisungsabfolgen, die von Github abgearbeitet werden, um beispielsweise über Github Pages eine Seite zu veröffentlichen. In diesem Reiter kann der Fortschritt der einzelnen Workflows verfolgt werden und Fehler untersucht werden.  
  
![Workflows in Github](/Dokumentation%20zur%20Webseite/pics/Workflows.png)  
  
Beim Auftreten eines Fehlers kann es unter Umständen zum Abbruch eines Workflows kommen. Der Fehler kann durch die Detailansicht des betroffenen Workflows ausgewertet und untersucht werden.  
  
![Workflowfehler](/Dokumentation%20zur%20Webseite/pics/Fehler.png)  
  
## 3. Jekyll-Konfigurationen bei der SpesML-Webseite
Die SpesML-Webseite wird mithilfe von Jekyll generiert und über Github Pages veröffentlicht. Um eine korrekte Darstellung der Webseite zu gewährleisten, müssen Jekyll bestimmte Informationen zur Konfiguration der Webseite mitgeteilt werden. Hierfür wird die im Hauptverzeichnis abgelegte YAML-Datei *_config.yml* verwendet. Diese Datei beinhaltet alle Konfigurationsinformationen, die für die Generierung der Webseite benötigt werden. Hierzu gehören unter anderem der titel der Webseite, das Logo der Webseite, das verwendete Layout (bzw. Theme) oder auch einstellen zu Suchfunktionen. Die folgenden Abschnitte geben einen Überblick über das verwendete Layout/theme und über die genutzten Konfigurationen.

### 3.1. *Just the Docs*-Theme
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

### 3.2. Konfigurationsdatei *_config.yml*
Die Datei *_config.yml* ist die Hauptkonfigurationsdatei für die Jekyll-Webseite und beinhaltet alle wichtigen Einstellungen, die zur korrekten Darstellung der Webseite benötigt werden. Üblicherweise wird diese Datei nur selten bearbeitet und bleibt bei einmaliger Konfiguration meist unverändert. Wichtige Änderungen können das Hinzufügen von bestimmten Plugins oder Funktionen sein, oder auch eine Änderung des Titels.  
  
#### Site Settings
Die wichtigsten Parameter sind die *Site Settings*. Hier werden Eigenschaften wie Titel, Beschreibung, URL, Pfad, Logo, Favicon oder auch die Auxiliary Links der Webseite definiert. Zur Definition werden bereits im Layout definierte Variablen eingesetzt. Der Webseitentitel, die Mailadresse udn die Bescheibung der Webseite werden wie folgt definiert:  
  
```yaml
title: SpesML
email: your-email@example.com
description: >- # this means to ignore newlines until "baseurl:"
  The aim of the SpesML project is to make this well-founded approach applicable to the industrially widespread Systems Modeling Language (SysML) and to adapt a commercial SysML tool to the SPES methodology.
```  
  
Änderungen an der Konfigurationsdatei werden ebenfalls automatisch übernommen und verarbeitet und sollte daher genau geprüft werden, um einen kurzfristigen Ausfall der Webseite zu verhindern.  
  
Im nächsten Abschnitt der *_config.yml* sind Einstellungen und Definitionen zu den URLs der Webseite zu finden.  
  
```yaml
baseurl: "/" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
```  
  
Die Variable *baseurl* definiert den Pfad/Subpfad der Webseite. Hier kann auch auf Unterordner des Github Repository verwiesen werden, allerdings ist es ratsam den Pfad "/" zu nutzen, um das Hauptverzeichnis - in dem die Konfigurationsdatei liegen sollte - als Pfad zu verlinken. Die Variable *url* kann zur Definition und Verlinkung einer eigenen Domain genutzt werden. Im Falle eines Deployments über Github Pages ist hier kein Eintrag notwendig.  

In den Site Settings können weitere optionale Einstellungen eingepflegt werden. So können über die folgenden YAML-Variablen das Logo der Webseite, welches anstelle des Titels angezeigt wird, festgelegt werden. Weitere Features aus dem *Just the Docs*-Theme ist die Verwendung eines Favicon oder die Nutzung von Auxiliary Links in einer horizontalen Navigationsbar. Diese werden wie folgt definiert:   
  
```yaml
logo: "bilder/logo_spesml.png"
favicon: "/favicon.ico"
aux_links:
  "Imprint":
    - "https://spesml.github.io/imprint.html/"
  "Privacy":
    - "https://spesml.github.io/privacy.html/"
```

#### Build Settings & Plugins
Die *Build Settings* legen fest, welche Parser für die Konvertierung von Markdown genutzt werden, welches Layout verwendet wird und welche Plugins zur Generierung der Webseite genutzt werden sollen. Die Plugins werden dann von Github ausgewertet und entsprechend verwendet. Für eine lokale Nutzung müssen die Plugins außerdem noch in der *Gemfile* eingefügt werden (siehe ...).  
  
Jekyll nutzt den Github Flavored Markdown (GFM) Prozessor von Kramdown. Um die Nutzung von Kramdown als Markdown-Prozessor nochmals zu spezifizieren, kann in *_config.yml* folgende Zeile in den Build Settings eingefügt werden:  
  
```yaml  
# Build settings
markdown: kramdown
```  
  
Das Theme wird Über die *remote-theme* Variable definiert.  
  
```yaml
remote_theme: pmarsceill/just-the-docs
```  
  
Diese Art von Layout-Definition eignet sich jedoch nur zur Verwendung von in Github Repositories abgelegten Themes (siehe Abschnitt [3.1 *Just the Docs*-Theme](https://git.rwth-aachen.de/spesmlgroup/spesml/-/blob/master/Dokumentation%20zur%20Webseite/Website_Guidelines.md#31-just-the-docs-theme)).  
  
Zu verwendende Plugins werden ebenfalls in der Konfigurationsdatei definiert, wobei das Plugin *jekyll-feed* eine Voraussetzung zur Nutzung des *Just the Docs*-Theme ist.  
  
```yaml
plugins:
  - jekyll-feed
  - jekyll-seo-tag
  - jekyll-pdf-embed
  - jekyll-include-cache
```  
  
Bestimmte Einstellungen zu genutzten Plugins können einfach in die Konfigurations datei eingetragen werden. Als Beispiel kann die Suchfunktion des genutzten Themes genannt werden. Diese ist bereits im Layout implementiert und muss nicht zusätzlich als Plugin hinzugefügt werden, allerdings können die dazugehörigen Einstellungen in der Konfigurationsdatei der Webseite bearbeitet und angepasst werden:  
  
```yaml
# Enable or disable the site search
# Supports true (default) or false
search_enabled: true
search:
  # Split pages into sections that can be searched individually
  # Supports 1 - 6, default: 2
  heading_level: 2
  # Maximum amount of previews per search result
  # Default: 3
  previews: 2
  # Maximum amount of words to display before a matched word in the preview
  # Default: 5
  preview_words_before: 3
  # Maximum amount of words to display after a matched word in the preview
  # Default: 10
  preview_words_after: 3
  # Set the search token separator
  # Default: /[\s\-/]+/
  # Example: enable support for hyphenated search words
  tokenizer_separator: /[\s/]+/
  # Display the relative url in search results
  # Supports true (default) or false
  rel_url: true
  # Enable or disable the search button that appears in the bottom right corner of every page
  # Supports true or false (default)
  button: false
```  
  
#### Excludes
Am Ende der Konfigurationsdatei befindet sich typischerweise ein *Exclude*-Abschnitt. Die in diesem Abschnitt angegebenen Dateipfade werden von Jekyll ignoriert, werden nicht verarbeitet und nicht veröffentlicht. Hierdurch können beispielsweise Dateien eines bestimmten Formats vollständig aus der Verarbeitung ausgeschlossen werden, um so die Artifaktgröße oder die Speichergröße des Inhaltes zu verringern.  
  
```yaml
# Exclude from processing.
# The following items will not be processed, by default.
# Any item listed under the `exclude:` key here will be automatically added to
# the internal "default list".
#
# Excluded items can be processed by explicitly listing the directories or
# their entries' file path in the `include:` list.
#
# exclude:
#   - .sass-cache/
#   - .jekyll-cache/
#   - gemfiles/
#   - Gemfile
#   - Gemfile.lock
#   - node_modules/
#   - vendor/bundle/
#   - vendor/cache/
#   - vendor/gems/
#   - vendor/ruby/
```  
  
### 3.3. Gemfile
*Gemfile* ist eine Datei, die dazu dient die Rubygems - Installationspackages der Ruby-Programmiersprache in Form von "Edelsteinen" - für die jeweiligen Plugins und Themes an Jekyll weiterzugeben. In dieser Datei wird auch angegeben, ob der Jekyll-Prozessor oder der Github-Prozessor verwendet wird.  
  
```ruby
source "https://rubygems.org"
# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
#gem "jekyll", "~> 4.2.2"
# This is the default theme for new Jekyll sites. You may change this to anything you like.
gem "minimal-mistakes-jekyll"
gem "just-the-docs"

# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
gem "github-pages","~>225", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins
# If you have any plugins, put them here!
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.15.1"
  gem "jekyll-pdf-embed"
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gem to `v0.6.x` on JRuby builds since newer versions of the gem
# do not have a Java counterpart.
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

gem "webrick", "~> 1.7"

# From https://github.com/MihajloNesic/jekyll-pdf-embed
source "https://rubygems.pkg.github.com/mihajlonesic" do
  gem "jekyll-pdf-embed", "1.1.2.1", group: :jekyll_plugins
end
```
  
Zur Verwendung von Github Pages muss überprüft werden, dass `gem "github-pages","~>225", group: :jekyll_plugins` enthalten ist.  
  
Plugins, Themes und weitere Bausteine werden über `gem "name_des_bausteins"` eingefügt. Weitere Informationen zu *gems*, *Ruby* und zur *Gemfile* sind auf https://bundler.io/gemfile.html erhältlich.

## 4. Veröffentlichen mit Markdown-Dateien
Die Veröffentlichung von Webseiteninhalten mit Jekyll und Github Pages lässt sich am einfachsten durch die Ablage von Inhalten in einer Markdown-Datei implementieren. Jekyll liest die Markdown-Dateien aus und verarbeitet diese zu einer html-Datei. Dies bietet den Vorteil, unabhängig von Programmierkenntnissen, den gewünschten Inhalt zu publizieren. Dieser Abschnitt soll eine Einleitung zum Verfassen von Webinhalten mit Markdown bieten.  
  
### 4.1. Erstellung von Markdown-Dateien
Markdown-Dateien können ohne Umwege direkt im Github Repository angelegt werden. Die Dateien können sowohl im Hauptverzeichnis, als auch in Unterordnern, abgelegt werden - mit Ausnahme der Datei *index.md*, die im Hauptverzeichnis liegen muss und die erste Seite der Webseite bildet. Markdown-Dateien in Github endet üblicherweise mit *.md* und können jeden gewünschten Namen annnehmen. Es wird empfohlen Leerzeichen in Dateinamen durch Binde- und Unterstriche zu ersetzen, um Kompatibilität zu gewährleisten.  
  
![Markdown-Datei erstellen](/Dokumentation%20zur%20Webseite/pics/markdown_erstellen.png)  
  
Der Inhalt der Datei kann schließlich in das dafür vorgesehene Eingabefeld eingetragen werden und über *Commit changes* in das jeweilige Verzeichnis hochgeladen werden.  
  
Ein weiteres Feature von Markdown ist die Unterstützung von HTML-Code innerhalb der Datei. Hierdurch können die Inhalte über HTML angepasst und dargestellt werden. Durch HTML-Code lassen sich auch Videos, Bilder, Links oder PDF-Dateien in die Markdown-Datei einbetten und darstellen. Um eine PDF-Datei in Markdown einzubetten und somit auf der Webseite zu veröffentlichen kann folgender HTML-Code verwendet werden:  
  
```html
<html>
  <head>
    <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width">
  </head>
  <body>
    <object data="https://spesml.github.io/Unterordner/dateiname.pdf" type="application/pdf" style="min-height:100vh;width:100%"></object>
  </body>
</html>
```  
  
Der Link *data="..."* hängt vom Speicherpfad des jeweiligen PDF-Dokuments im Github ab. Hier müssen *Unterordner* und *dateiname.pdf* durch den jeweiligen Ordner- oder Dateiname ersetzt werden.
  
### 4.2. Front Matter für Markdown
Damit Jekyll die Markdown-Dateien korrekt verarbeiten kann, benötigt die Software eine *Front Matter* in der Markdown-Datei, die Informationen über das Seitenlayout, den Titel der Seiten oder der Navigationsreihenfolge beinhaltet. In diesem Abschnitt werden die mindestens benötigten Front Matter Variable vorgestellt und einige zusätzliche, wichtige Variablen zur besseren Gestaltung der Webseite.  
  
#### Notwendige Front Matter Variablen
Damit der Inhalt einer Seite von Jekyll verarbeitet und über Github Pages veröffentlicht werden kann, benötigt Jekyll mindestens die Definition eines Layouttyps für die entsprechende Seite. Je nach Theme gibt es unterschiedliche Layouttypen. Bei dem für die SpesML-Webseite verwendeten Layout ist bereits ein Standardtyp festgelegt, der über `layout: default`definiert werden kann.  
  
Eine Front Matter wird in einer Markdown-Datei durch die Eingabe von `---` geöffnet und mit einer erneuten Eingabe von `---` geschlossen. Jekyll und Github Pages verarbeiten die Informationen in dieser Front Matter schließlich ähnlich zu einem Header in einer HTML-Datei.  
  
```yaml
---
layout: default
title: Home
---
```  

Mit `title: Titel` kann der Seitentitel übergeben werden und so die unterschiedlichen Inhalte von Jekyll differenziert werden. Ohne weitere Angabe von Variablen werden die Seiten mit dieser vorgestellten Front Matter ungeordnet in die Navigationsstruktur eingegliedert. Um eine geordnete Navigationsstruktur zu erhalten, müssen weitere Front Matter Variablen eingesetzt werden.

#### Weitere Variablen
Mithilfe von weiteren Variablen im Front Matter können die Einstellungen der Seiten und Layouts weiter verfeinert werden. Weitere oft verwendete Variable sind u.a.:  
  
```yaml
nav_order: 1-xxx # Numerische Reihenfolge in der Navigationsstruktur
has_children: true/false # Gibt an ob aktuelle Seite untergeordnete Seite besitzt
has_toc: true/false # Blendet ein Inhaltsverzeichnis ein oder aus
permalink: /plugin/overview.html # Setzt einen Permalink für die aktuelle Seite
parent: Titel der übergeordneten Seite # Wird bei untergeordneten Seiten benötigt
grand_parent: Titel der über-übergeordneten Seite # Wird bei untergeordneten Seiten benötigt
```  
  
### 5. Kontakt
Sollte noch Fragen aufkommen oder ein Anliegen noch in die Dokumentation mit aufgenommen werden, wenden Sie sich bitte an folgende Projektmitglieder:  
  
**Alexander Knerr**  
Qualicen GmbH  
E-Mail: [alexander.knerr@qualicen.de](mailto:alexander.knerr@qualicen.de)  
(noch bis 22.04.2022)  
  
**Michael Jastram**  
Qualicen GmbH  
E-Mail: [michael.jastram@qualicen.de](mailto:michael.jastram@qualicen.de)  
  
**Maximilian Junker**  
Qualicen GmbH  
E-Mail: [maximilian.junker@qualicen.de](mailto:maximilian.junker@qualicen.de)  
  
**Henning Femmer**  
Qualicen GmbH  
E-Mail: [henning.femmer@qualicen.de](mailto:henning.femmer@qualicen.de)
