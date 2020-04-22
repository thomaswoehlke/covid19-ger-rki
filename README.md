Data from the Robert-Koch-Institut on COVID-19 in Germany
================
Last update: 2020-04-22

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

    ## # A tibble: 794 x 6
    ##    Datum      Bundesland      Fallzahl Todeszahl Fallzahl_neu Todeszahl_neu
    ##    <date>     <chr>              <dbl>     <dbl>        <dbl>         <dbl>
    ##  1 2020-04-22 Baden-Württemb…    28898      1063          186            32
    ##  2 2020-04-22 Bayern             38814      1424          504            88
    ##  3 2020-04-22 Berlin              5312       105           75             8
    ##  4 2020-04-22 Brandenburg         2389        74          114             7
    ##  5 2020-04-22 Bremen               624        26           15             1
    ##  6 2020-04-22 Hamburg             4204        91            0             0
    ##  7 2020-04-22 Hessen              7380       265          149            14
    ##  8 2020-04-22 Mecklenburg-Vo…      656        15            1             0
    ##  9 2020-04-22 Niedersachsen       9236       328          138            22
    ## 10 2020-04-22 Nordrhein-West…    30185       964          796            68
    ## 11 2020-04-22 Rheinland-Pfalz     5593       122           32             6
    ## 12 2020-04-22 Saarland            2367        97           39             4
    ## 13 2020-04-22 Sachsen             4273       122           20             5
    ## 14 2020-04-22 Sachsen-Anhalt      1395        33           12             1
    ## 15 2020-04-22 Schleswig-Hols…     2496        79           82             9
    ## 16 2020-04-22 Thüringen           1872        71           74            16
    ## # … with 778 more rows

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

<img src="plots/covid19-deu-rki-faelle-pro-tag.png">

[Full
size](https://github.com/seb09/covid19-ger-rki/raw/master/plots/covid19-deu-rki-faelle-pro-tag.png)
