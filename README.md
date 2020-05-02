Data from the Robert-Koch-Institut on COVID-19 in Germany
================
Last update: 2020-05-02

This repository contains data on reported COVID-19 cases in Germany and
its federal states that is published daily by the Robert-Koch-Institut
(RKI).

``` r
library(tidyverse)
corona_rki <- read_csv("data/corona_deu_rki.csv")
corona_rki %>% 
  arrange(desc(Datum), Bundesland) %>% 
  print(n = 16)
```

    ## # A tibble: 954 x 6
    ##    Datum      Bundesland      Fallzahl Todeszahl Fallzahl_neu Todeszahl_neu
    ##    <date>     <chr>              <dbl>     <dbl>        <dbl>         <dbl>
    ##  1 2020-05-02 Baden-Württemb…    32146      1402          227            17
    ##  2 2020-05-02 Bayern             42658      1885          169            35
    ##  3 2020-05-02 Berlin              5943       152           56             3
    ##  4 2020-05-02 Brandenburg         2886       122           14             2
    ##  5 2020-05-02 Bremen               871        30           12             0
    ##  6 2020-05-02 Hamburg             4609       163            5             0
    ##  7 2020-05-02 Hessen              8486       364          110             4
    ##  8 2020-05-02 Mecklenburg-Vo…      695        18            2             0
    ##  9 2020-05-02 Niedersachsen      10246       451          105            22
    ## 10 2020-05-02 Nordrhein-West…    33216      1268          158             7
    ## 11 2020-05-02 Rheinland-Pfalz     6099       173           13             1
    ## 12 2020-05-02 Saarland            2597       135           16             0
    ## 13 2020-05-02 Sachsen             4617       163           25             1
    ## 14 2020-05-02 Sachsen-Anhalt      1571        44            7             0
    ## 15 2020-05-02 Schleswig-Hols…     2728       112           14             2
    ## 16 2020-05-02 Thüringen           2335        93           12             0
    ## # … with 938 more rows

Data is downloaded each day at 11am from the [website of the
RKI](https://www.rki.de/DE/Content/InfAZ/N/Neuartiges_Coronavirus/Fallzahlen.html)
(and updated again at 11pm). The time stamp refers to the day when the
data was downloaded.

Population sizes of the federal states were scraped from
[Wikipedia](https://de.wikipedia.org/wiki/Liste_der_deutschen_Bundesl%C3%A4nder_nach_Bev%C3%B6lkerung)
and are also available in this repo.

``` r
population <- read_csv("data/einwohner_bundesland.csv")
population
```

    ## # A tibble: 16 x 2
    ##    Bundesland             Einwohner
    ##    <chr>                      <dbl>
    ##  1 Baden-Württemberg       11069533
    ##  2 Bayern                  13076721
    ##  3 Berlin                   3644826
    ##  4 Brandenburg              2511917
    ##  5 Bremen                    682986
    ##  6 Hamburg                  1841179
    ##  7 Hessen                   6265809
    ##  8 Mecklenburg-Vorpommern   1609675
    ##  9 Niedersachsen            7982448
    ## 10 Nordrhein-Westfalen     17932651
    ## 11 Rheinland-Pfalz          4084844
    ## 12 Saarland                  990509
    ## 13 Sachsen                  4077937
    ## 14 Sachsen-Anhalt           2208321
    ## 15 Schleswig-Holstein       2896712
    ## 16 Thüringen                2143145

I’ll try to update the data daily. You can import the most recent
version directly from GitHub.

``` r
library(readr)
corona_rki <- read_csv("https://raw.githubusercontent.com/seb09/covid19-ger-rki/master/data/corona_deu_rki.csv")
```

I will also produce a plot from time to time, probably in German. You’re
welcome to use them.

-----

<img src="plots/covid19-deu-rki-entwicklung.png">

[Full
size](https://github.com/seb09/covid19-ger-rki/raw/master/plots/covid19-deu-rki-entwicklung.png)

-----

<img src="plots/covid19-deu-rki-entwicklung-original-skala.png">

[Full
size](https://github.com/seb09/covid19-ger-rki/raw/master/plots/covid19-deu-rki-entwicklung-original-skala.png)

-----

<img src="plots/covid19-deu-rki-faelle-pro-tag.png">

[Full
size](https://github.com/seb09/covid19-ger-rki/raw/master/plots/covid19-deu-rki-faelle-pro-tag.png)
