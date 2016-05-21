# Wiener Git Linien Ubahnplan

Dieses Repo ist eine repräsentation des Wiener Ubahn Netzes mit Stand 2016.
!(http://media.vienna.at/bilder/specials/u-bahn/u-bahn-plan-wien-viennaAT.png)
Jeder commit repräsentiert dabei eine Station. Die einzelnen Linien lassen sich durch den Graphen verfolgen.

## Probleme
Problematisch war die Station Karlsplatz, da wenn U1 beim Stefansplatz steht, U2 beim Museumsquartier und U4 beim Stadtpark der Stand der U1 immer in entweder U2 oder U4 enthalten ist. Git macht in diesem Fall einen merge commit mit nur Museumsquartier und Stadtpark als parent commit. Diesen einen commit habe ich dann per hand erstellt:

```
tree 4b825dc642cb6eb9a060e54bf8d69288fbee4904
parent e4cfa967de04447511864b135b88123d4eada4fe
parent 7295bff107b03115bd8b3f58fef51794f54bd385
parent b43dcbea51b3503572adbca56ea4083a0821bd19
author Lukas Peleska <git@luaks.net> 1458927946 +0100
committer Lukas Peleska <git@luaks.net> 1458927946 +0100

U1,U2,U4 - Karlsplatz

```
```
$ git log --graph --oneline --decorate --date=relative --all
* 94a0b1e (HEAD -> master, origin/master) Initial Commit
* 49970f5 (tag: Hütteldorf, U4) U4 - Hütteldorf
* dd1bcc4 (tag: Ober_St._Veit) U4 - Ober St. Veit
* d565c0b (tag: Unter_St._Veit) U4 - Unter St. Veit
* 9c24ab3 (tag: Braunschweiggasse) U4 - Braunschweiggasse
* 21cd2dc (tag: Hietzing) U4 - Hietzing
* 47941fc (tag: Schönbrunn) U4 - Schönbrunn
* 51d34e6 (tag: Meidling_Hauptstrasse) U4 - Meidling Haupstrasse
| * f1a4874 (tag: Ottakring, U3) U3 - Ottakring
| * ace1880 (tag: Kendlerstrasse) U3 - Kendlerstrasse
| * 4ace8c6 (tag: Hütteldorferstrasse) U3 - Hütteldorferstrasse
| * d97e436 (tag: Johnstrasse) U3 - Johnstrasse
| * 5814833 (tag: Schweglerstrasse) U3 - Schweglerstrasse
| | * 71835d1 (tag: Siebenhirten, U6) U6 - Siebenhirten
| | * 383e507 (tag: Perfektastrasse) U6 - Perfektastrasse
| | * dcfc1dc (tag: Erlaaer_Strasse) U6 - Erlaaer Strasse
| | * 2813d68 (tag: Alterlaa) U6 - Alterlaa
| | * 7c5f092 (tag: Am_Schöpfwerk) U6 - Am Schöpfwerk
| | * f9866da (tag: Tscherttegasse) U6 - Tscherttegasse
| | * a26ac32 (tag: Philadelphiabrücke_(Bhf._Meidling), tag: Niederhoferstrasse) U6 - Niederhoferstrasse
| |/  
|/|   
* |   6b656b7 (tag: Längenfeldgasse) U4,U6 - Längenfeldgasse
|\ \  
| * | 6518ea8 (tag: Margaretengürtel) U4 - Margaretengürtel
| * | 0b51fc3 (tag: Pilgramgasse) U4 - Pilgramgasse
| * | ca90019 (tag: Kettenbrückengasse) U4 - Kettenbrückengasse
* | | c297aca (tag: Gumpendorferstrasse) U6 - Gumpendorferstrasse
| |/  
|/|   
* |   d935738 (tag: Westbahnhof) U3,U6 - Westbahnhof
|\ \  
| * | f3e6e55 (tag: Zieglergasse) U3 - Zieglergasse
| * | 00b2774 (tag: Neubaugasse) U3 - Neubaugasse
* | | 5867fc0 (tag: Burggasse_Stadthalle) U6 - Burggasse Stadthalle
* | | 453221d (tag: Thaliastrasse) U6 - Thaliastrasse
* | | 3ba8863 (tag: Josefstädter_Strasse) U6 - Josefstädter Strasse
* | | 1dc770b (tag: Alser_Strasse) U6 - Alser Strasse
* | | e5b6614 (tag: Michelbeuern-AKH) U6 - Michelbeuern-AKH
* | | 335923f (tag: Währinger_Strasse_Volksoper) U6 - Währinger Strasse - Volksoper
* | | 31a400c (tag: Nußdorfer_Strasse) U6 - Nußdorfer Strasse
| | | * 3190aae (tag: Reumannplatz, U1) U1 - Reumannplatz
| | | * e5f8706 (tag: Keplerplatz) U1 - Keplerplatz
| | | * e2baca4 (tag: Südtiroler_Platz_Hauptbahnhof) U1 - Südtiroler Platz, Hauptbahnhof
| | | * 6af56f2 (tag: Quartier_Belvedere) U1 - Quartier Belvedere
| | | * 86552b2 (tag: Taubstummengasse) U1 - Taubstummengasse
| | |/  
| | *-.   f05ca00 (tag: Karlsplatz, U2) U1,U2,U4 - Karlsplatz
| | |\ \  
| | | * | 7295bff (tag: Stadtpark) U4 - Stadtpark
| | * | | e4cfa96 (tag: Museumsquartier) U2 - Museumsquartier
| |/ / /  
| * | |   ce41a16 (tag: Volkstheater) U2,U3 - Volkstheater
| |\ \ \  
| | * | | 3853527 (tag: Herrengasse) U3 - Herrengasse
| | | |/  
| | |/|   
| | * |   b43dcbe (tag: Stephansplatz) U1,U3 - Stephansplatz
| | |\ \  
| | | * | 2bba7e6 (tag: Stubentor) U3 - Stubentor
| | | |/  
| | | *   d22a4f2 (tag: Landstraße) U3,U4 - Landstraße
| | | |\  
| | | |/  
| | |/|   
| | * |   180dd27 (tag: Schwedenplatz) U1,U4 - Schwedenplatz
| | |\ \  
| | | * | cb748b9 (tag: Nestroyplatz) U1 - Nestroyplatz
| | | | * faa5995 (tag: Rochusgasse) U3 - Rochusgasse
| | | | * d8f3f2c (tag: Kardinal-Nagl-Platz) U3 - Kardinal-Nagl-Platz
| | | | * e9d0239 (tag: Schlachthausgasse) U3 - Schlachthausgasse
| | | | * 907443c (tag: Erdberg) U3 - Erdberg
| | | | * dff4fd5 (tag: Gasometer) U3 - Gasometer
| | | | * f14b541 (tag: Zipperstraße) U3 - Zippererstraße
| | | | * ed75ab6 (tag: Enkplatz) U3 - Enkplatz
| | | | * 2704d93 (tag: Simmering) U3 - Simmering
| * | | 0b04db2 (tag: Rathaus) U2 - Rathaus
| * | | 968ad9b (tag: Schottentor) U2 - Schottentor
| |/ /  
| * |   f54e33d (tag: Schottenring) U2,U4 - Schottenring
| |\ \  
| | * | a94a834 (tag: Taborstraße) U2 - Taborstraße
| | |/  
| | *   003514a (tag: Praterstern) U1,U2 - Praterstern
| | |\  
| | | * 394af55 (tag: Vorgartenstraße) U1 - Vorgartenstraße
| | | * 0486d0e (tag: Donauinsel) U1 - Donauinsel
| | | * 2c79529 (tag: Kaisermühlen) U1 - Kaisermühlen
| | | * e5490f5 (tag: Alte_Bonau) U1 - Alte Donau
| | | * db93e5c (tag: Kagran) U1 - Kagran
| | | * bfe0024 (tag: Kagraner_Platz) U1 - Kagraner Platz
| | | * 3d91bc6 (tag: Rennbahnweg) U1 - Rennbahnweg
| | | * 7cdbf1e (tag: Aderklaaer_Straße) U1 - Aderklaaer Straße
| | | * 1028684 (tag: Großfeldsiedlung) U1 - Großfeldsiedlung
| | | * e36bb35 (tag: Leopoldau) U1 - Leopoldau
| | * 04ff6d7 (tag: Messe-Prater) U2 - Messe-Prater
| | * 605688d (tag: Krieau) U2 - Krieau
| | * c7cb25f (tag: Stadion) U2 - Stadion
| | * 88c8854 (tag: Donaumarina) U2 - Donaumarina
| | * 6132a96 (tag: Donaustadtbrücke) U2 - Donaustadtbrücke
| | * 762fbab (tag: Stadlau) U2 - Stadlau
| | * e6a17c8 (tag: Hardeggasse) U2 - Hardeggasse
| | * 1c54432 (tag: Aspernstraße) U2 - Aspernstraße
| | * 11cd546 (tag: Hausfeldstraße) U2 - Hausfeldstraße
| | * 5439a5e (tag: Aspern_Nord) U2 - Aspern Nord
| | * f9effca (tag: Seestadt) U2 - Seestadt
| * ad087f2 (tag: Roßauer_Lände) U4 - Roßauer Lände
| * b987e41 (tag: Friedensbrücke) U4 - Friedensbrücke
|/  
*   9fdaf23 (tag: Spitellau) U4,U6 - Spittelau
|\  
| * 59c4113 (tag: Heiligenstadt) U4 - Heiligenstadt
* 98384f2 (tag: Jägerstraße) U6 - Jägerstraße
* 75ce7ad (tag: Dresdner_Straße) U6 - Dresdner Straße
* 245e0f9 (tag: Handelskai) U6 - Handelskai
* 2a77f6a (tag: Neue_Donau) U6 - Neue Donau
* d46a14c (tag: Floridsdorf) U6 - Floridsdorf
```
