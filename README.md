# Saab Kockums

### Studentproject 2017
Hantering av tredjepartskomponenter

* [Komma igång](#komma-igång)
  * [Installation av mallapplikation](#installation-av-mallapplikation)
  * [Start av back- och frontend](#start-av-back--och-frontend)
* [Mappstruktur](#mappstruktur)
* [Rekommenderad Programvara](#rekommenderad-programvara)
  * [Visual Studio Code](#visual-studio-code)
  * [DB Browser for SQLite](#db-browser-for-sqlite)
  * [Postman](#postman)
  * [Vue.js Devtools](#vuejs-devtools)
* [Dokumentation](#dokumentation)
* [Felsökning](#felsökning)
  * [Fel vid installation av mallapplikation](#fel-vid-installation-av-mallapplikation)
  * [Fel vid start av back- och frontend](#fel-vid-start-av-back--och-frontend)

## Komma igång
Börja med att [ladda ned](https://nodejs.org/en/download/) och installera **Node.js** version `6.11.2`

**OBS!** Notera att valet av version är viktigt.

### Installation av mallapplikation
Öppna `Node.js command prompt` från startmenyn och navigera till roten för detta repository.

För att hämta och installera alla beroenden kör

```bash
$ npm install
```

### Start av back- och frontend
För att starta både back- och frontend samtidigt med automatisk uppdatering kör

```bash
$ npm run watch
```

Det öppnas ytterliggare en promt där backend-servern körs samtidigt som prompten vilken utförde kommandot kör frontend-servern. Det öppnas också ett webbläsarfönster med den genererade webbapplikationen.

Samtliga ändringar som sker i koden under tiden dessa fönster körs kommer att `automatiskt uppdatera applikationen` efter att ändrad fil sparas.

## Mappstruktur
Mallapplikationen följer följande mappstruktur

```
.
├─ backend
|   ├─ routes                       ←   end points för backend
|   |   ├─ components.js
|   |   ├─ products.js
|   |   └─ projects.js
|   |
|   ├─ db-setup.sql.js              ←   setup-script för databas
|   ├─ server.js
|   └─ sqlite.db                    ←   den faktiska databasfilen
~
                                    ←   filer för bygge av applikationen
~
├─ src
|   ├─ assets
|   ├─ components                   ←   komponenter som återanvänds i vyer
|   |   ├─ layout
|   |   |   ├─ Content.vue
|   |   |   ├─ Navbar.vue
|   |   |   ├─ Sidebar.vue
|   |   |   └─ SidebarItem.vue
|   |   |   
|   |   ├─ ComponentList.vue
|   |   ├─ ProductsList.vue
|   |   └─ ProjectsList.vue
|   |
|   ├─ router                       ←   end points för frontend
|   |   └─ index.js
|   |
|   ├─ views                        ←   vyer i applikationen
|   |   ├─ Component.vue
|   |   ├─ ComponentHome.vue
|   |   └─ Ovweview.vue
|   | 
|   ├─ App.vue                      ←   rotvyn för applikationen
|   └─ main.js
| 
├─ index.html
└─ package.json
```

## Rekommenderad programvara
Nedan listas programvara som inte är nödvändig för utförandet av projektet, men rekommenderas starkt.

Rekommenderad Programvara | Version | Download
------------------------- | ------- | :------:
Visual Studio Code        | v1.14.2 | [Länk](https://code.visualstudio.com/)
DB Browser for SQLite     | v6.11.2 | [Länk](https://github.com/sqlitebrowser/sqlitebrowser/tags)
Postman                   | v0.2.23 | [Länk](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop)
Vue.js Devtools           | v3.1.6  | [Länk](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
Vetur                     | v0.9.3  | ↓

### Visual Studio Code
Är en editor med pluginstöd för `Vue.js` som används som frontend-ramverk. 

**TIPS** - för att installera `Vetur` som är ett plugin för utveckling av `Vue.js` tryck

```bash
[ctrl] + [shift] + x
```

skriv in `Vetur` och installera. En omstart av editorn kan också krävas.

### DB Browser for SQLite
Är en databashanterare för SQLite-databaser. Möjliggör direkt manipulering av tabeller och exekvering av setup-script. Allt som behövs är att ladda in databasfilen för projektet som kan hittas i `./backend/sqlite.db`.

### Postman
Är en applikation för enklare API-utveckling. Möjliggör snabba och enkla tester av HTTP CRUD-operationer på egenutvecklade API:er.

### Vue.js Devtools
Är ett Chrome-plugin för att enklare utveckling med `Vue.js`. Änvänds i webbläsaren genom att trycka `F12` och navigera till `Vue`-tabben.

## Dokumentation
Vidare dokumentation som kan behövas.

Dokumentation             |  Download
------------------------- | :------:
Vue.js                    | [Länk](https://vuejs.org/v2/guide/)
SQLite3 tutorial          | [Länk](https://dbwebb.se/kunskap/sqlite-och-nodejs)
SQLite3 SQL-syntax        | [Länk](https://www.sqlite.org/lang.html)
SQLite3 för Node.js       | [Länk](https://github.com/mapbox/node-sqlite3/wiki)
Bulma CSS-framwork        | [Länk](http://bulma.io/documentation/overview/start/)

## Felsökning
Följande problem kan uppstå

### Fel vid installation av mallapplikation
Kontrollera att rätt version av `Node.js` och `npm` är installerade. Öppna `Node.js command prompt` och kör

```
$ node --version             ←   ska skriva ut v6.11.2
```

```
$ npm --version              ←   ska skriva ut 3.10.10
```

Skulle båda applikationerna ha rätt version, kontrollera att installationsförsöket görs i rotmappen av projektet.

### Fel vid start av back- och frontend
För `*nix` system kommer startkommandot inte fungera. Starta istället `två separata terminalfönster` och kör

```
$ npm run front
```

```
$ npm run back
```

> Det går även att köra ovanstående kommandon om `$ npm run watch` inte fungerar för ett Windows-system.

Skulle inget av dessa alternativ fungera, för någon typ av system, kör istället

```
$ node build/dev-server.js
```

```
$ node backend/server.js
```

Det kommer dock inte finnas möjlighet att få automatisk uppdatering vid ändring av kod. Det senare kommandot måste köras på nytt varje gång en uppdatering sker för backend.
