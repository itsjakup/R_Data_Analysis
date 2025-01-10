
---
output: pdf_document: default
  html_notebook: default
df_print: paged
---

##  {.tabset}

#### $$BACHELOR\ NE\ INXHINIERI\ MATEMATIKE\ DHE\ INFORMATIKE$$

#### $$DATA\ ANALYSIS\ NE\ RSTUDIO$$

#### $$Realizuar\ nga\ Jakup\ Ymeraj\ dhe\ Adisa\ Hoxhaj$$

$$Fakulteti\ i\ Shkencave\ te\ Natyres\\ Qershor\ 2024$$

### **`r colorize ("Prezantimi me RStudio", "blue")`**
$$RStudio$$

**Cfare\ eshte\ RStudio?**

**R eshte nje gjuhe programimi e specializuar ne llogaritje statistikore dhe vizualizimin e te dhenave, e miratuar nga fushat e nxjerrjes se te dhenave, bioinformatikes dhe analizes se te dhenave.**

**$RStudio$ eshte nje mjedis zhvillimi i integruar per gjuhen $R$**

**Kjo platforme eshte e disponueshme ne dy formate: $RStudio$ $Desktop$ i cila eshte nje aplikacion i rregullt desktop dhe $Rstudio$ $Server$ i cili funksionon ne nje server te madh dhe lejon hyrjen ne $RStudio$ duke perdorur nje shfletues web. $RStudio$ $IDE$ eshte nje produkt i $Posit$ $PBC$ (dikur $RStudio$ $PBC$, me pare $RStudio$ $Inc.$).**

*RStudio perfshin:*

**• nje mjet efektiv per trajtimin dhe ruajtjen e te dhenave;**

**• nje grup operatoresh per llogaritjet ne vargje, ne vecanti matrica;**

**• nje koleksion te madh, koherent dhe te integruar te mjeteve te ndermjetme per analizen e te dhenave;**

**• pajisje grafike per analizen dhe shfaqjen e te dhenave ne ekran ose ne kopje fizike;**

**• nje gjuhe programimi te zhvilluar mire, e thjeshte dhe efektive, e cila perfshin kushte, funksione rekursive te percaktuara nga perdoruesi dhe pajisje hyrese-dalese;**


$$Objektivat:$$

**Ne kete projekt kemi si synim:**

**~ Te shqyrtojme ne menyre analitike, statistikore dhe grafike te dhenat e datasetit ne gjuhen $R$;**

**~ Te jemi te afte te lexojme dhe interpretojme kodet e perdorura dhe te shpjegojme qellimin e perdorimit te tyre;**

**~ Te analizojme cdo grafik te ndertuar;**

**~ Te evidentojme dhe perdorim te gjithe funksionet dhe librarite e ndryshme te mesuara ne seancat laboratorike dhe me gjere;**




### **`r colorize("Njohje me Databazen", "blue")`**

$$Student\ Spending\ Dataset$$

**Dataseti i zgjedhur titullohet $Student$ $Spending$ dhe ne te listohen te ardhurat dhe shpenzimet e 1000 studenteve te zgjedhur ne nje zgjedhje te rastit, ku ne thelbin e studimit qendron fakti se ne varesi te moshes, formimit arsimor dhe gjinise, sa fiton, sa shpenzon dhe si i shpenzon nje student te ardhurat mujore te tij. Nje rendesi e vecante i eshte kushtuar edhe menyres sesi parate transaksionohen, duke na lene te kuptojme se si nje student preferon te paguaje dhe paguhet gjate veprimtarise se tij te perditshme.**

*CREDITS: $Student$ $Spending$ $Dataset$ eshte shkarkuar ne $kaggle.com/datasets$, duke qene brenda rregullave dhe kritereve me te cilat web-faqja $kaggle.com$ funksionon!*


**Le te njihemi me datasetin $Student$ $Spending$:**

**Ky dataset perbehet nga variabla dhe vlera si me poshte:**

**Fillimisht na duhet te importojme datasetin nga file explorer dhe per ta bere kete na duhet libraria $readxl$ e cila do te lexoje skedarin excel dhe me pas perdorim funksionin $setwd()$ i cili do te marre si parameter path-in e file qe duam te importojme:**

```{r}
library(readxl)
setwd("C:/Users/Perdorues/Downloads")
getwd()
data  = read.csv("student_spending.csv")
data
```

**$Student$ $Spending$ permban 17 lloje te ndryshme ndryshoresh, ku seciles ndryshore i korrespondojne 1000 te dhena;**

**Dataseti ka gjithsej 4 $ndryshore$ $cilesore$ dhe 13 $ndryshore$ $sasiore$;**

$Ndryshoret$ $Cilesore:$

**Gjinia;**

**Viti i Studimeve;**

**Diplomimi;**

**Metoda e Pageses;**

$Ndryshoret$ $Sasiore:$

**Mosha**

**Te ardhurat mujore**

**Ndihma financiare**

**Shkollimi**

**Strehimi**

**Ushqimi**

**Transporti**

**Mjetet shkollore**

**Argetim**

**Kujdesi personal**

**Teknologji**

**Mireqenia shendetesore**

**Te ndryshme/ Te tjera**

#### $$Cdo\ ndryshore\ do\ te\ analizohet\ nga\ ana\ statistikore!$$


### **`r colorize ("Analiza e te Dhenave", "blue")`**

**$Analiza$ $e$ $te$ $dhenave$ në $RStudio$ eshte nje proces ku perpunohen, vizualizohen dhe interpretohen te dhenat per te nxjerre informacione dhe kuptim nga to. Ne kete proces perfshihet importimi, pastrimi, perpunimi, vizualizimi dhe interpretimi i te dhenave ne nje menyre sa me te sakte.**

**Per te bere nje analize te sakte te te dhenave do fillojme te aplikojme disa metoda te cilat jane themelore ne data analysis.**

$Librarite$ $e$ $perdorura$ $ne$ $analizimin$ $e$ $te$ $dhenave$ $jane:$

**library(readxl)**

**library(ggpubr)**

**library(tidytext)**

**library(correlation)**

**library(tidyr)**

**library(corrplot)**

**library(DataExplorer)**

**library(MASS)**

**library(survey)**

**library(datawizard)**

**library(stats)**

**library(grid)**

**library(wordcloud)**

**library(tidyverse)**

**library(RColorBrewer) etj..**

$$PERPUNIMI\ I\ TE\ DHENAVE$$

**Per te nisur perpunimin e te dhenave fillimisht duhet te lexojme datasetin me ane te funksionit $stwd()$, gjithashtu duhet te perdorim edhe librarine $readxl$ e cila do te lexoje skedarin tone excel.**
```{r}
library(readxl)
setwd("C:/Users/Perdorues/Downloads")
getwd()
```

**Funksioni $getwd()$ na jep file path.**

**Tregojme cfare klase eshte dataseti:**
```{r}
class(data)
```

**Percaktojme dimensionin/permasen e datasetit:**
```{r}
dim(data)
```

**Rezultati i shfaqur na tregon se dataseti perbehet nga 1000 rreshta dhe 17 kolona.**

**Shfaqim strukturen e objektit tone te te dhenave ($Data$ $Frame$). Ky veprim arrihet duke aplikuar funksionin $str(data)$ dhe me anen e tij ne percaktojme:**

**1.Numrin e rreshtave dhe kolonave te datasetit;**

**2.Tipin e te dhenave per secilen kolone si int, char, boolean etj.;**

**3.Nje pjese te vogel te te dhenave ne dataset;**
```{r}
str(data)
```

**Aplikojme funksionin $summary(data)$ per te kryer nje permbledhje te shpejte, paraprake te te dhenave ne dataset.**

**Rezultati i kthyer nga $summary(data)$ perfshin informacione si:**

**~Vlerat ekstremale (max, min), mesatarja, mesorja, moda,kuartili i pare, kuartili i 3-te;**

**~Numrin e vlerave qe mungojne ne secilen nga kolonat e datasetit (NAN).**

**~Nje permbledhje te te dhenave per vlerat e ndryshoreve cilesore, duke perfshire numrin e vlerave unike dhe frekuencen e tyre.**

**Kjo ndihmon ne njohjen e shperndarjes se te dhenave ne kolona duke perfshire vlerat minimale dhe maksimale, vleren mesatare dhe tendencat e tjera statistikore.**

```{r}
summary(data)
```

**Kontrollojme per numra qe mungojne:**
```{r}
num <- sum(is.na(data))
num
```

**Kontrollojme per vlera duplicated:**
```{r}
dupl <- sum(duplicated(data))
dupl
```
**Meqenese nuk mungojne vlera dhe nuk ka vlera duplicated, grupi i te dhenave eshte i paster.**



#### $$ANALIZA\ E\ NDRYSHOREVE\ SASIORE$$

**$Ndryshoret$ $Sasiore$ klasifikohen ne ndryshore $diskrete$ dhe $te$ $vazhdueshme$.**

**Ndryshoret Sasiore ne datasetin tone jane diskrete, me vlera te fundme, qe do te thote se ato do te pershkruhen numerikisht nepermjet efektivave, frekuencave dhe tabelave statistikore.**

**Ne kete headline do te trajtojme analizen e treguesve te pozicionit ku perfshihen mesatarja, moda, mesorja, kuartilet dhe treguesit e shperhapjes, intervalet nderkuartilore, amplituda, dispersioni dhe menjanimi mesatar katror.**

**Mesatarja, Moda, Mesorja & Kuartilet, Intervalet Nderkuartilore;**

$$Mesatarja\ Aritmetike$$

**$Mesatarja$ $Aritmetike$ ne statistike eshte nje parameter qe tregon pozicionin e vlerave te ndryshores. Ajo paraqet vleren e pergjithshme te nje grupi te te dhenave dhe ka kuptim vetem kur ndryshorja eshte sasiore. Per te llogaritur vleren mesatare te dhenat mblidhen se bashku dhe me pas pjesetohen me numrin e tyre te pergjithshem.**

$$Formula\ matematike:\\{\displaystyle {\overline {X}}={\frac {X_{1}+\cdots +X_{n}}{n}}}={\frac {1}{n} \sum _{i=1}^{n}{x_{i}}}$$

**Le te kryejme nje llogaritje te vlerave mesatare per cdo variabel sasiore ne dataset nepermjet funksionit $mean()$.**

**Per te kryer kete llogaritje per cdo ndryshore sasiore do ti therrasim ato me ate te funksionit $df$`$`$emri$`_`$variablit$: **

**Mosha mesatare e nje studenti ne dataset eshte:**
```{r}
mean_mosha <- mean(data$mosha)
print(mean_mosha)
```

**Te ardhurat mesatare te studenteve jane:**
```{r}
mean_te_ardhurat_mujore <- mean(data$te_ardhurat_mujore)
print(mean_te_ardhurat_mujore)
```

**Ndihma financiare qe i atribohet cdo studenti mesatarisht arrin vleren:**
```{r}
mean_ndihma_financiare <- mean(data$ndihma_financiare)
print(mean_ndihma_financiare)
```

**Shuma qe nje student shpenzon mesatarisht per shkollimin e tij:**
```{r}
mean_shkollimi <- mean(data$shkollimi)
print(mean_shkollimi)
```

**Shuma qe nje student shpenzon mesatarisht per te siguruar strehimin e tij:**
```{r}
mean_strehimi <- mean(data$strehimi)
print(mean_strehimi)

```

**Shuma qe nje student shpenzon mesatarisht ne muaj per te siguruar ushqimin e tij:**
```{r}
mean_ushqimi <- mean(data$ushqimi)
print(mean_ushqimi)
```

**Shuma qe nje student shpenzon mesatarisht ne muaj per sa i perket transportit:**
```{r}
mean_transporti <- mean(data$transporti)
print(mean_transporti)
```

**Shuma qe nje student shpenzon mesatarisht ne muaj per te siguruar mjetet e tij shkollore (ketu perfshihen libra, fotokopje, lapsa, ngjyra etj.):**
```{r}
mean_mjetet_shkollore <- mean(data$mjetet_shkollore)
print(mean_mjetet_shkollore)
```

**Shuma qe nje student shpenzon mesatarisht ne muaj per t'u argetuar:**
```{r}
mean_argetim <- mean(data$argetim)
print(mean_argetim)
```

**Shuma mesatare qe nje student ia dedikon kujdesit te tij personal si qethje, parukiere, veshje, higjiene etj.**
```{r}
mean_kujdesi_personal <- mean(data$kujdesi_personal)
print(mean_kujdesi_personal)
```

**Shuma qe nje student shpenzon mesatarisht ne muaj ne aspektin e teknologjise; ketu perfshihen telefon, laptop/pc dhe cdo angazhim tjeter ne kete fushe:**
```{r}
mean_teknologji <- mean(data$teknologji)
print(mean_teknologji)
```

**Shuma qe nje student ia dedikon mireqenies se tij shendetesore, duke perfshire vizitat mjekesore, konsultat te dentisti, medikamente farmaceutike etj.:**
```{r}
mean_mireqenia_shendetesore <- mean(data$mireqenia_shendetesore)
print(mean_mireqenia_shendetesore)
```

**Shuma qe nje student shpenzon per cdo aktivitet tjeter ne perditshmerine e tij; kjo shume varet nga teprica e shumes monetare te mbetur ne llogarine e tij:**
```{r}
mean_te_ndryshme <- mean(data$te_ndryshme)
print(mean_te_ndryshme)
```

$$Mesatarja\ e\ Grupuar$$

**Tani le te llogarisim shpenzimet mujore te studenteve sipas kategorive/grupimeve;**

**Per ta realizuar na duhen dy librari: libraria $dplyr$ dhe $tidyr$; Ne fillimisht do ti kategorizojme te dhenat ne disa grupime dhe me pas do te llogarisim se sa shpenzon secila prej tyre mesatarisht;**

**Grupojme te dhenat me ane te funksionit $group$`_`$by$:**
```{r}
library(dplyr)
library(tidyr)

grupi_mosha <- data %>% group_by(data$mosha)
grupi_gjinia <- data %>% group_by(data$gjinia)
grupi_viti_i_studimeve <- data %>% group_by(data$viti_i_studimeve)
grupi_diplomimi <- data %>% group_by(data$diplomimi)
```

**Shpenzimet e grupimit $mosha$:**
```{r}
shpenzimet_mesatare_mosha <- grupi_mosha %>%
  summarize(
    shkollimi = mean(shkollimi),
    strehimi = mean(strehimi),
    ushqimi = mean(ushqimi),
    transporti = mean(transporti),
    mjetet_shkollore = mean(mjetet_shkollore),
    argetim = mean(argetim),
    kujdesi_personal = mean(kujdesi_personal),
    teknologji = mean(teknologji),
    mireqenia_shendetesore = mean(mireqenia_shendetesore),
    te_ndryshme = mean(te_ndryshme)
  )
```

**Shpenzimet mesatare per cdo kategori te shpenzimeve brenda cdo grupi te moshes jane:**
```{r}
print(shpenzimet_mesatare_mosha)
```

**Kodi:**

**Fillimisht therrasim librarite e nevojshme $dplyr$ dhe $tidyr$.**

**$grupi$`_`$mosha$ $<-$ $data$ $`%>%`$ $group$`_`$by(data`$`mosha)$ kryen grupimin e kerkuar, duke marre si parameter emrin e kolones se datasetit mbi te cilen kerkojme te kryejme nje llogaritje te tille statistikore ($mosha$). E njejta procedure perdoret ne 3 rreshtat pasues te kodit, ku kryhet grupimi per variablat $gjinia$, $viti$`_`$i$`_`$studimeve$ dhe $diplomimi$**

**Pasi kemi kryer te gjitha grupimet e deshiruara, duke perdorur funksionin $summarize(...)$ ne llogaritim nje mesatare te grupimeve te mesiperme ku perfshihen fushat si $shkollimi$, $strehimi$, $ushqimi$ etj., te cilat afishohen ne nje tabele.**

**Leximi i tabeles eshte i tille: 18 vjecaret shpenzojne mesatarisht $4485.952 per shkollimin, $712.2419 per strehim, e keshtu me rradhe per te gjitha kategorite e tjera ne tabele.**

**E njejta menyre interpretimi vlen per cdo tabele tjeter te ndertuar me poshte.**

**Shpenzimet e grupimit $gjinia$:**
```{r}
shpenzimet_mesatare_gjinia <- grupi_gjinia %>%
  summarize(
    shkollimi = mean(shkollimi),
    strehimi = mean(strehimi),
    ushqimi = mean(ushqimi),
    transporti = mean(transporti),
    mjetet_shkollore = mean(mjetet_shkollore),
    argetim = mean(argetim),
    kujdesi_personal = mean(kujdesi_personal),
    teknologji = mean(teknologji),
    mireqenia_shendetesore = mean(mireqenia_shendetesore),
    te_ndryshme = mean(te_ndryshme)
  )
```

**Shpenzimet mesatare per cdo kategori te shpenzimeve brenda cdo grupi te gjinise jane:**
```{r}
print(shpenzimet_mesatare_gjinia)
```

**Shpenzimet e grupimit $viti$ $i$ $studimeve$:**
```{r}
shpenzimet_mesatare_viti_i_studimeve <- grupi_viti_i_studimeve %>%
  summarize(
    shkollimi = mean(shkollimi),
    strehimi = mean(strehimi),
    ushqimi = mean(ushqimi),
    transporti = mean(transporti),
    mjetet_shkollore = mean(mjetet_shkollore),
    argetim = mean(argetim),
    kujdesi_personal = mean(kujdesi_personal),
    teknologji = mean(teknologji),
    mireqenia_shendetesore = mean(mireqenia_shendetesore),
    te_ndryshme = mean(te_ndryshme)
  )
```

**Shpenzimet mesatare per cdo kategori te shpenzimeve brenda cdo grupi te vitit te studimeve jane:**
```{r}
print(shpenzimet_mesatare_viti_i_studimeve)
```

**Shpenzimet e grupimit $diplomimi$:**
```{r}
shpenzimet_mesatare_diplomimi <- grupi_diplomimi %>%
  summarize(
    shkollimi = mean(shkollimi),
    strehimi = mean(strehimi),
    ushqimi = mean(ushqimi),
    transporti = mean(transporti),
    mjetet_shkollore = mean(mjetet_shkollore),
    argetim = mean(argetim),
    kujdesi_personal = mean(kujdesi_personal),
    teknologji = mean(teknologji),
    mireqenia_shendetesore = mean(mireqenia_shendetesore),
    te_ndryshme = mean(te_ndryshme)
  )
```

**Shpenzimet mesatare per cdo kategori te shpenzimeve brenda cdo grupi te diplomimit jane:**
```{r}
print(shpenzimet_mesatare_diplomimi)
```

$$Moda$$

**$Moda$ ne statistike eshte vlera qe paraqitet me shpesh ne nje grup te te dhenave.**

**Moda mund te aplikohet ne te dhenat e shprehura ne forme numerike, si dhe ne te dhenat kategorike qe perbehen nga kategori ose etiketa.**

**Ne disa raste nje grup i te dhenave mund te kete me shume se nje modalitet me vlera te njejte te shpeshta. Ne kete rast grupi quhet $bimodal$ ose $multimodal$. Perveç kesaj, ndonjehere mund te ndodhe qe grupi te mos kete mode fare, ne rastin kur te dhenat jane te shperndara ne menyre te barabarte dhe nuk ka vlere qe paraqitet me shume se te tjerat.**

**Le te gjejme vlerat modale ne te dhenat tona per secilen variabel sasiore me ane te funksionit $names$($table$($df$`$`$variabli$))[$table$($df$`$`$variabli$) $==$ $max$($table$($df$`$`$variabli$))]:**

**Mosha e perseritur me shpesh:**
```{r}
mode_mosha <- names(table(data$mosha))[table(data$mosha) == max(table(data$mosha))]
print(mode_mosha)
```

**Vlera e te ardhurave qe perseritet me teper:**
```{r}
mode_te_ardhurat_mujore <- names(table(data$te_ardhurat_mujore))[table(data$te_ardhurat_mujore) == max(table(data$te_ardhurat_mujore))]
print(mode_te_ardhurat_mujore)
```

**Vlera e ndihmes financiare e perseritur me shpesh:**
```{r}
mode_ndihma_financiare <- names(table(data$ndihma_financiare))[table(data$ndihma_financiare) == max(table(data$ndihma_financiare))]
print(mode_ndihma_financiare)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi shkollimin:**
```{r}
mode_shkollimi <- names(table(data$shkollimi))[table(data$shkollimi) == max(table(data$shkollimi))]
print(mode_shkollimi)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi strehimin:**
```{r}
mode_strehimi <- names(table(data$strehimi))[table(data$strehimi) == max(table(data$strehimi))]
print(mode_strehimi)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi ushqyerjen:**
```{r}
mode_ushqimi <- names(table(data$ushqimi))[table(data$ushqimi) == max(table(data$ushqimi))]
print(mode_ushqimi)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi transportin:**
```{r}
mode_transporti <- names(table(data$transporti))[table(data$transporti) == max(table(data$transporti))]
print(mode_transporti)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi mjetet shkollore:**
```{r}
mode_mjetet_shkollore <- names(table(data$mjetet_shkollore))[table(data$mjetet_shkollore) == max(table(data$mjetet_shkollore))]
print(mode_mjetet_shkollore)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi argetimin:**
```{r}
mode_argetim <- names(table(data$argetim))[table(data$argetim) == max(table(data$argetim))]
print(mode_argetim)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi kujdesin personal:**
```{r}
mode_kujdesi_personal <- names(table(data$kujdesi_personal))[table(data$kujdesi_personal) == max(table(data$kujdesi_personal))]
print(mode_kujdesi_personal)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi teknologjine:**
```{r}
mode_teknologji <- names(table(data$teknologji))[table(data$teknologji) == max(table(data$teknologji))]
print(mode_teknologji)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimit mbi mireqenien shendetesore:**
```{r}
mode_mireqenia_shendetesore <- names(table(data$mireqenia_shendetesore))[table(data$mireqenia_shendetesore) == max(table(data$mireqenia_shendetesore))]
print(mode_mireqenia_shendetesore)
```

**Vlera e perseritur me shpesh per sa i perket shpenzimeve te tjera qe studentet kryejne:**
```{r}
mode_te_ndryshme <- names(table(data$te_ndryshme))[table(data$te_ndryshme) == max(table(data$te_ndryshme))]
print(mode_te_ndryshme)
```

$$Mesorja$$

**$Mesorja$ në statistike eshte nje mase qendrore e cila paraqet vleren e mesme ose vleren qe ndan nje grup te dhene te te dhenave ne dy pjese te barabarta. Nenkupton qe gjysma e te dhenave jane me te medha se mesorja dhe gjysma tjeter jane me te vogla.**

**Mesorja llogaritet duke e renditur grupin e të dhenave ne rradhe te rritjes se vlerave dhe duke gjetur vleren qe ndodhet ne mesin e tyre. Nese numri i te dhenave eshte çift, atehere mesorja eshte vlera e mesme e dy vlerave të qendruara. Nese numri i te dhenave eshte tek, atehere mesorja eshte vlera e vetme qe ndodhet ne mes te grupit.**

**Gjejme mesoren per secilen ndryshore sasiore me ane te funksionit $median()$:**

**Mesorja e moshes:**
```{r}
median_mosha <- median(data$mosha)
print(median_mosha)
```

**Mesorja e te ardhurave mujore:**
```{r}
median_te_ardhurat_mujore <- median(data$te_ardhurat_mujore)
print(median_te_ardhurat_mujore)
```

**Mesorja e ndihmes financiare:**
```{r}
median_ndihma_financiare <- median(data$ndihma_financiare)
print(median_ndihma_financiare)
```

**Mesorja e shumave te shpenzuara per shkollim:**
```{r}
median_shkollimi <- median(data$shkollimi)
print(median_shkollimi)
```

**Mesorja e shumave te shpenzuara per strehim:**
```{r}
median_strehimi <- median(data$strehimi)
print(median_strehimi)
```

**Mesorja e shumave te shpenzuara per ushqim:**
```{r}
median_ushqimi <- median(data$ushqimi)
print(median_ushqimi)
```

**Mesorja e shumave te shpenzuara per transport:**
```{r}
median_transporti <- median(data$transporti)
print(median_transporti)
```

**Mesorja e shumave te shpenzuara per mjete shkollore:**
```{r}
median_mjetet_shkollore <- median(data$mjetet_shkollore)
print(median_mjetet_shkollore)
```

**Mesorja e shumave te shpenzuara per argetim:**
```{r}
median_argetim <- median(data$argetim)
print(median_argetim)
```

**Mesorja e shumave te shpenzuara per kujdes personal:**
```{r}
median_kujdesi_personal <- median(data$kujdesi_personal)
print(median_kujdesi_personal)
```

**Mesorja e shumave te shpenzuara ne fushen e teknologjise:**
```{r}
median_teknologji <- median(data$teknologji)
print(median_teknologji)
```

**Mesorja e shumave te shpenzuara per mireqenien shendetesore:**
```{r}
median_mireqenia_shendetesore <- median(data$mireqenia_shendetesore)
print(median_mireqenia_shendetesore)
```

**Mesorja e shumave te shpenzuara per shpenzime te tjera te ndryshme:**
```{r}
median_te_ndryshme <- median(data$te_ndryshme)
print(median_te_ndryshme)
```

$$Kuartilet$$

**$Kuartilet$ ne statistike jane vlerat qe ndajne nje grup te te dhenave ne kater pjese te barabarta. Keto pjese perbehen nga 25% te te dhenave te renditura ne rradhe te rritjes se tyre.**

**Kuartilet perdoren per te vleresuar shperndarjen e te dhenave dhe per te identifikuar vlerat e rendesishme ne grup. Ketu jane tre lloje kuartilesh te zakonshme:**

**1. Kuartili i pare $Q1$ eshte vlera qe ndan 25% te te dhenave me te vogla nga grupi i te dhenave te renditura. Nenkupton se 25% e te dhenave jane me te vogla se kuartili i pare dhe 75% jane me te medha se kjo vlere.**

**2. Kuartili i dyte ose mesi $Q2$ eshte vlera qe ndan grupin e te dhenave ne dy pjese te barabarta. Njeren gjysme me vlerat me te vogla dhe gjysmen tjeter me vlerat me te medha.**

**3. Kuartili i trete $Q3$ eshte vlera qe ndan 75% te te dhenave me te medha nga grupi i te dhenave te renditura. Kjo nenkupton se 75% e te dhenave jane me te vogla se kuartili i trete dhe 25% jane me te medha.**

**Le te llogaritim kuartilet me ane te funksionit $quantile()$ dhe intervalet nderkuartilore per secilen ndryshore sasiore me ane te funksionit $IQR()$:**

**Kuartilet e moshes:**
```{r}
q75 <- quantile(data$mosha, 0.75)
q25 <- quantile(data$mosha, 0.25)
quantile(data$mosha)
IQR(data$mosha)
```

**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "mosha" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 18.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 20. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 22. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 24. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 25.**

**Funksioni IQR afishon vleren 4, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 4. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 4 njesi.**


**Kuartilet e te ardhurave mujore:**
```{r}
q75 <- quantile(data$te_ardhurat_mujore, 0.75)
q25 <- quantile(data$te_ardhurat_mujore, 0.25)
quantile(data$te_ardhurat_mujore)
IQR(data$te_ardhurat_mujore)
```

**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "te_ardhurat_mujore" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 501.00.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 770.75. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 1021.00. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 1288.25. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 1500.00.**

**Funksioni IQR afishon vleren 517.5, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 517.5. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 517.5 njesi.**


**Kuartilet e ndihmave financiare:**
```{r}
q75 <- quantile(data$ndihma_financiare, 0.75)
q25 <- quantile(data$ndihma_financiare, 0.25)
quantile(data$ndihma_financiare)
IQR(data$ndihma_financiare)
```

**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "ndihma_financiare" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 0.0.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 261.0. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 513.0. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 751.5. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 1000.00.**

**Funksioni IQR afishon vleren 490.5, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 490.5. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 490.5 njesi.**


**Kuartilet e shumave te shpenzuara ndaj shkollimit:**
```{r}
q75 <- quantile(data$shkollimi, 0.75)
q25 <- quantile(data$shkollimi, 0.25)
quantile(data$shkollimi)
IQR(data$shkollimi)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "shkollimi" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 3003.00.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 3779.75. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 4547.50. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 5285.00. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 6000.00.**

**Funksioni IQR afishon vleren 1505.25, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 1505.25. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 1505.25 njesi.**


**Kuartilet e shumave te shpenzuara ndaj strehimit:**
```{r}
q75 <- quantile(data$strehimi, 0.75)
q25 <- quantile(data$strehimi, 0.25)
quantile(data$strehimi)
IQR(data$strehimi)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "strehimi" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 401.00.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 538.75. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 704.50. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 837.25. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 1000.00.**

**Funksioni IQR afishon vleren 298.5, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 298.5. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 298.5 njesi.**


**Kuartilet e shumave te shpenzuara ndaj ushqimit:**
```{r}
q75 <- quantile(data$ushqimi, 0.75)
q25 <- quantile(data$ushqimi, 0.25)
quantile(data$ushqimi)
IQR(data$ushqimi)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "ushqimi" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 100.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 175. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 255. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 330. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 400.**

**Funksioni IQR afishon vleren 155, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 155. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 155 njesi.**


**Kuartilet e shumave te shpenzuara ndaj  transportit:**
```{r}
q75 <- quantile(data$transporti, 0.75)
q25 <- quantile(data$transporti, 0.25)
quantile(data$transporti)
IQR(data$transporti)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "transporti" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 50.00.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 88.00. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 123.00. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 162.25. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 200.00.**

**Funksioni IQR afishon vleren 74.25, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 74.25. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 74.25 njesi.**


**Kuartilet e shumave te shpenzuara ndaj mjeteve shkollore:**
```{r}
q75 <- quantile(data$mjetet_shkollore, 0.75)
q25 <- quantile(data$mjetet_shkollore, 0.25)
quantile(data$mjetet_shkollore)
IQR(data$mjetet_shkollore)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "mjetet_shkollore" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 50.00.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 112. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 175. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 238. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 300.**

**Funksioni IQR afishon vleren 126, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 126. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 126 njesi.**


**Kuartilet e shumave te shpenzuara ndaj argetimit:**
```{r}
q75 <- quantile(data$argetim, 0.75)
q25 <- quantile(data$argetim, 0.25)
quantile(data$argetim)
IQR(data$argetim)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "argetim" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 20.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 54. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 86. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 116. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 150.**

**Funksioni IQR afishon vleren 62, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 62. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 62 njesi.**

**Kuartilet e shumave te shpenzuara ndaj kujdesit personal:**
```{r}
q75 <- quantile(data$kujdesi_personal, 0.75)
q25 <- quantile(data$kujdesi_personal, 0.25)
quantile(data$kujdesi_personal)
IQR(data$kujdesi_personal)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "kujdesi_personal" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 20.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 41. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 62. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 80. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 100.**

**Funksioni IQR afishon vleren 39, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 39. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 39 njesi.**


**Kuartilet e shumave te shpenzuara ne fushen e teknologjise:**
```{r}
q75 <- quantile(data$teknologji, 0.75)
q25 <- quantile(data$teknologji, 0.25)
quantile(data$teknologji)
IQR(data$teknologji)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "teknologji" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 50.**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 114. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 178. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 241. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 300.**

**Funksioni IQR afishon vleren 127, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 127. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 127 njesi.**


**Kuartilet e shumave te shpenzuara ndaj mireqenies shendetesore:**
```{r}
q75 <- quantile(data$mireqenia_shendetesore, 0.75)
q25 <- quantile(data$mireqenia_shendetesore, 0.25)
quantile(data$mireqenia_shendetesore)
IQR(data$mireqenia_shendetesore)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "mireqenia_shendetesore" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 30**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 73. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 115. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 158. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 200.**

**Funksioni IQR afishon vleren 85, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 85. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 85 njesi.**


**Kuartilet e shumave te shpenzuara ndaj shpenzimeve te tjera te ndryshme:**
```{r}
q75 <- quantile(data$te_ndryshme, 0.75)
q25 <- quantile(data$te_ndryshme, 0.25)
quantile(data$te_ndryshme)
IQR(data$te_ndryshme)
```
**Ky rezultat tregon vlerat perkatese te kuantileve per kolonen "te_ndryshme" ne dataset:**

**•	0%: Vlera minimale e te dhenave eshte 20.00**

**•	25%: Kjo eshte vlera e kuantilit te 25%, qe ne kete rast eshte 63.75. Kjo do te thote qe 25% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	50%: Kjo eshte vlera qendrore, e njohur si mesorja, qe ne kete rast eshte 110.00. Kjo tregon se 50% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	75%: Kjo eshte vlera e kuantilit te 75%, qe ne kete rast eshte 153.00. Kjo do te thote qe 75% e te dhenave jane me te vogla ose te barabarta me kete vlere.**

**•	100%: Vlera maksimale e te dhenave eshte 200.00.**

**Funksioni IQR afishon vleren 89.25, kjo do te thote se diferenca midis kuantilit te 25% dhe kuantilit te 75% eshte 89.25. Kjo tregon se 50% e te dhenave jane te perhapura ne nje interval prej 89.25 njesi.**


$$Vlerat\ Ekstremale:\ Maximum,\ Minimum$$

*$Vlerat$ $ekstremale$ $min,$ $max;$ $indekset$ $perkatese;$ $Amplituda;$*

**Gjetja e vleres maksimale do te kryhet me ane te funksionit $max()$, gjetja e vleres minimale do te kryhet me ane te funksionit $min()$ ndersa pozicionet perkatese do te gjenden me ane te funksionit $which.max()$ dhe $which.min()$.**

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $mosha:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$mosha)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$mosha)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $te$ $ardhurat$ $mujore:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$te_ardhurat_mujore)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$te_ardhurat_mujore)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $ndihma$ $financiare:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$ndihma_financiare)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$ndihma_financiare)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $shkollimi:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$shkollimi)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$shkollimi)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $strehimi:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$strehimi)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$strehimi)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $ushqimi:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$ushqimi)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$ushqimi)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $transporti:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$transporti)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$transporti)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $mjetet$ $shkollore:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$mjetet_shkollore)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$mjetet_shkollore)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $argetim:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$argetim)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$argetim)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $kujdesi$ $personal:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$kujdesi_personal)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$kujdesi_personal)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $teknologji:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$teknologji)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$teknologji)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $mireqenia$ $shendetesore:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$mireqenia_shendetesore)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$mireqenia_shendetesore)
print(pozicioni-1)
```

**Gjetja e vleres maksimale dhe pozicionit te saj ne kolone per variablin $te$ $ndryshme:$**

**Vlera maksimale:**
```{r}
max_values <- max(data$mireqenia_shendetesore)
print(max_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.max(data$mireqenia_shendetesore)
print(pozicioni-1)
```

**Gjetja e vlerës minimale dhe pozicionit te saj ne kolone per variablin $mosha:$**

**Vlera minimale:**
```{r}
min_values <- min(data$mosha)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$mosha)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $te$ $ardhurat$ $mujore:$**

**Vlera minimale:**
```{r}
min_values <- min(data$te_ardhurat_mujore)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$te_ardhurat_mujore)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $ndihma$ $financiare:$**

**Vlera minimale:**
```{r}
min_values <- min(data$ndihma_financiare)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$ndihma_financiare)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $shkollimi:$**

**Vlera minimale:**
```{r}
min_values <- min(data$shkollimi)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$shkollimi)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $strehimi:$**

**Vlera minimale:**
```{r}
min_values <- min(data$strehimi)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$strehimi)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $ushqimi:$**

**Vlera minimale:**
```{r}
min_values <- min(data$ushqimi)
print(pozicioni-1)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$ushqimi)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $transporti:$**

**Vlera minimale:**
```{r}
min_values <- min(data$transporti)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$transporti)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $mjetet$ $shkollore:$**

**Vlera minimale:**
```{r}
min_values <- min(data$mjetet_shkollore)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$mjetet_shkollore)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $argetim:$**

**Vlera minimale:**
```{r}
min_values <- min(data$argetim)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$argetim)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $kujdesi$ $personal:$**

**Vlera minimale:**
```{r}
min_values <- min(data$kujdesi_personal)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$kujdesi_personal)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $teknologji:$**

**Vlera minimale:**
```{r}
min_values <- min(data$teknologji)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$teknologji)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $mireqenia$ $shendetesore:$**

**Vlera minimale:**
```{r}
min_values <- min(data$mireqenia_shendetesore)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$mireqenia_shendetesore)
print(pozicioni-1)
```

**Gjetja e vleres minimale dhe pozicionit te saj ne kolone per variablin $te$ $ndryshme:$**

**Vlera minimale:**
```{r}
min_values <- min(data$te_ndryshme)
print(min_values)
```

**Pozicioni ne kolone:**
```{r}
pozicioni <- which.min(data$te_ndryshme)
print(pozicioni-1)
```

**Sqarim:\ Indeksi\ i\ vlerave\ maksimale\ dhe\ minimale\ eshte\ zbritur\ me\ 1\ per\ arsye\ se,\ nese\ shohim\ ne\ kolonat\ e\ datasetit,\ indeksi\ real\ rezulton\ i+1,\ pra,\ pershembull\ pozicioni\ i\ minimumit\ te\ ndryshores\ $te$\$ndryshme$\ ne\ dataset\ do\ te\ jete\ 432 .**

$$Amplituda\\ A = {x_{max}}\ +\ {x_{min}}$$
**Diferenca midis vleres maksimale dhe minimale percakton $amplituden$.**

**Llogaritja e amplitudes per variablin $mosha:$**
```{r}
amplituda <- max(data$mosha) - min(data$mosha)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $te$ $ardhurat$ $mujore:$**
```{r}
amplituda <- max(data$te_ardhurat_mujore) - min(data$te_ardhurat_mujore)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $ndihma$ $financiare:$**
```{r}
amplituda <- max(data$ndihma_financiare) - min(data$ndihma_financiare)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $shkollimi:$**
```{r}
amplituda <- max(data$shkollimi) - min(data$shkollimi)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $strehimi:$**
```{r}
amplituda <- max(data$strehimi) - min(data$strehimi)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $ushqimi:$**
```{r}
amplituda <- max(data$ushqimi) - min(data$ushqimi)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $transporti:$**
```{r}
amplituda <- max(data$transporti) - min(data$transporti)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $mjetet$ $shkollore:$**
```{r}
amplituda <- max(data$mjetet_shkollore) - min(data$mjetet_shkollore)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $argetim:$**
```{r}
amplituda <- max(data$argetim) - min(data$argetim)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $kujdesi$ $personal:$**
```{r}
amplituda <- max(data$kujdesi_personal) - min(data$kujdesi_personal)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $teknologji:$**
```{r}
amplituda <- max(data$teknologji) - min(data$teknologji)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $mireqenia$ $shendetesore:$**
```{r}
amplituda <- max(data$mireqenia_shendetesore) - min(data$mireqenia_shendetesore)
print(amplituda)
```

**Llogaritja e amplitudes per variablin $te$ $ndryshme:$**
```{r}
amplituda <- max(data$te_ndryshme) - min(data$te_ndryshme)
print(amplituda)
```

#### $$Varianca/Dispersioni$$

**$Dispersioni$ dhe $Menjanimi$ $Mesatar$ $Katror$ jane dy parametra te rendesishem te shperhapjes. Dispersioni eshte mesatarja aritmetike e katroreve te diferencave midis cdo te dhene dhe mesatares. Pra ai mat shperhapjen e vlerave rrotull vleres mesatare.**

**Per te llogaritur Dispersionin perdoret funksioni $var(x);$**

$$Formula\ matematike:\\ \displaystyle {S}^2 = \frac {1}{n}{\displaystyle\sum_{i=1}^{n}(x_i - \mu)^2}\\ e\ cila\ llogarit\ variancen\ e\ grupit\ te\ te\ dhenave,\   indeksi\ "i"\ specifikon\ vleren\ e\  i^{{th}}\  ne\ grupin\ e\ te\ dhenave,\\  "μ"\ specifikon\ mesataren\ e\ grupit\ te\ te\ dhenave,\ dhe\ "n"\ specifikon\ numrin\ total\ te\ vezhgimeve.$$

**$Menjanimi$ $Mesatar$ $Katror$ eshte rrenja katrore e dispersionit dhe mat te njejten gje njesoj si dispersioni dhe ka permasen e te dhenave. Eshte nje numer qe ndihmon per te kuptuar se si vlerat individuale te vrojtuara shperndahen rrotull mesatares.**

**$Menjanimi$ $Mesatar$ ka permasen e te dhenave sepse gjendet si rrenje katrore e dispersionit (dollar, euro, metra, kilograme).**

$$\displaystyle Devijimi\ Standard:\ {S} = \sqrt{\frac{\displaystyle\sum_{i=1}^{n}(x_i - \mu)^2} {n}}\\ {S} = \sqrt{Varianca} = \sqrt{{S}^2}$$

**Per te llogaritur menjanimin mesatar ne R nuk egziston nje funksion i gatshem, keshtu qe ai do te merret sa rrenja katrore e dispersionit te llogaritur se pari: $sqrt(var(x))$;**

**Le te llogaritim variancen dhe menjanimin mesatar per ndryshoret tona me ane te funksionit $var(x)$ dhe $sqrt(var(x))$:**

**Varianca per ndryshoren $mosha$:**
```{r}
v1 <- c(data$mosha)
var(v1)
```
**Menjanimi Mesatar Katror per ndryshoren $mosha$:**
```{r}
d1 <- sqrt(var(v1))
d1
```

**Varianca per ndryshoren $te$ $ardhurat$ $mujore$:**
```{r}
v2 <- c(data$te_ardhurat_mujore)
var(v2)
```

**Menjanimi Mesatar Katror per ndryshoren $te$ $ardhurat$ $mujore$:**
```{r}
d2 <- sqrt(var(v2))
d2
```

**Varianca per ndryshoren $ndihma$ $financiare$:**
```{r}
v3 <- c(data$ndihma_financiare)
var(v3)
```

**Menjanimi Mesatar Katror per ndryshoren $ndihma$ $financiare$:**
```{r}
d3 <- sqrt(var(v3))
d3
```

**Varianca per ndryshoren $shkollimi$:**
```{r}
v4 <- c(data$shkollimi)
var(v4)
```

**Menjanimi Mesatar Katror per ndryshoren $shkollimi$:**
```{r}
d4 <- sqrt(var(v4))
d4
```

**Varianca per ndryshoren $strehimi$:**
```{r}
v5 <- c(data$strehimi)
var(v5)
```

**Menjanimi Mesatar Katror per ndryshoren $strehimi$:**
```{r}
d5 <- sqrt(var(v5))
d5
```

**Varianca per ndryshoren $ushqimi$:**
```{r}
v6 <- c(data$ushqimi)
var(v6)
```

**Menjanimi Mesatar Katror per ndryshoren $ushqimi$:**
```{r}
d6 <- sqrt(var(v6))
d6
```

**Varianca per ndryshoren $transporti$:**
```{r}
v7 <- c(data$transporti)
var(v7)
```

**Menjanimi Mesatar Katror per ndryshoren $transporti$:**
```{r}
d7 <- sqrt(var(v7))
d7
```

**Varianca per ndryshoren $mjetet$ $shkollore$:**
```{r}
v8 <- c(data$mjetet_shkollore)
var(v8)
```

**Menjanimi Mesatar Katror per ndryshoren $mjetet$ $shkollore$:**
```{r}
d8 <- sqrt(var(v8))
d8
```

**Varianca per ndryshoren $argetim$:**
```{r}
v9 <- c(data$argetim)
var(v9)
```

**Menjanimi Mesatar Katror per ndryshoren $argetim$:**
```{r}
d9 <- sqrt(var(v9))
d9
```

**Varianca per ndryshoren $kujdesi$ $personal$:**
```{r}
v10 <- c(data$kujdesi_personal)
var(v10)
```

**Menjanimi Mesatar Katror per ndryshoren $kujdesi$ $personal$:**
```{r}
d10 <- sqrt(var(v10))
d10
```

**Varianca per ndryshoren $teknologji$:**
```{r}
v11 <- c(data$teknologji)
var(v11)
```

**Menjanimi Mesatar Katror per ndryshoren $teknologji$:**
```{r}
d11 <- sqrt(var(v11))
d11
```
**Varianca per ndryshoren $mireqenia$ $shendetesore$:**
```{r}
v12 <- c(data$mireqenia_shendetesore)
var(v12)
```

**Menjanimi Mesatar Katror per ndryshoren $mireqenia$ $shendetesore$:**
```{r}
d12 <- sqrt(var(v12))
d12
```
**Varianca per ndryshoren $te$ $ndryshme$:**
```{r}
v13 <- c(data$te_ndryshme)
var(v13)
```

**Menjanimi Mesatar Katror per ndryshoren $te$ $ndryshme$:**
```{r}
d13 <- sqrt(var(v13))
d13
```

**Interpretimi i rezultateve do te jete i tille per cdo ndryshore mbi te cilen kemi llogaritur variancen dhe menjanimin mesatar katror: le te marrim ndryshoren $mosha$; vlera 5.3947 tregon se vlerat jane te shperhapura mesatarisht 5.3947 njesi katrore larg nga vlera mesatare e grupit te te dhenave. Vlera 2.322664 tregon se vlerat jane 2.322664 njesi larg nga vlera mesatare.**

**I njejti interpretim vlen per te gjitha ndryshoret e tjera.**


#### $$ANALIZA\ E\ NDRYSHOREVE\ CILESORE$$

**$Ndryshoret$ $Cilesore$ klasifikohen si ndryshore $nominale$ dhe $ordinale$.**

**$Ndryshoret$ $Nominale$ jane ato lloje ndryshoresh cilesore mbi te cilat nuk mund te kryhet veprimi i renditjes. Ndersa nje $Ndryshore$ $Ordinale$ eshte nje lloj i ndryshoreve cilesore mbi te cilat mund te kryejme renditje (ordinal , order - renditje).**

**Ne dataset ndryshoret nominale jane $gjinia$, $diplomimi$ dhe $metoda$ $e$ $pageses$, ndersa ndryshoret ordinale jane dhe $viti$ $i$ $studimeve$**

**Analiza e ndryshoreve cilesore do te perfshije ndertimin e tabelave te frekuences, tabelave te kontigjences, ku bashke me keto do te ndertojme edhe tabelat me vlerat probabilitare perkatese per cdo tabele kontigjence e gjithashtu edhe testin Hi-katror.*

#### $$Tabelat\ e\ frekuencave:\ Moda\ dhe\ Frekuenca\ e\ saj$$

**Tabela e Frekuences per ndryshoren cilesore $gjinia$ dhe moda: cilesia e perseritur me shpesh;**

**Tabela e Frekuences:**
```{r}
tab <- table(data$gjinia)
print(tab)
```

**Moda:**
```{r}
moda <- names(tab)[tab == max(tab)]
print(moda)
```

**Frekuenca:**
```{r}
max_frequency = max(tab)
print(max_frequency)
```

**Interpretimi i tabeles se frekuences:**

**Funksioni $table()$ na sherben per ndertimin e tabeles, duke marre si parameter emrin e ndryshores per te cilen deshirojme te ndertojme nje tabele frekuence. Funksioni $names(tab)[tab == max(tab)]$ sherben per te gjetur moden e ndryshores ndersa $max(tab)$ sherben per te gjetur frekuencen e saj. Veme re qe moda per kete ndryshore eshte $male$ dhe frekuenca e saj eshte 356, pra ajo shfaqet 356 here ne grupin e te dhenave. I njejti interpretim do te vleje per cdo tabele tjeter te ndertuar me poshte.**


**Tabela e Frekuences per ndryshoren cilesore $viti$ $i$ $studimeve$ dhe moda: cilesia e perseritur me shpesh;**

**Tabela e Frekuences:**
```{r}
tab <- table(data$viti_i_studimeve)
print(tab)
```

**Moda:**
```{r}
moda <- names(tab)[tab == max(tab)]
print(moda)
```

**Frekuenca:**
```{r}
max_frequency = max(tab)
print(max_frequency)
```

**Tabela e Frekuences per ndryshoren cilesore $diplomimi$ dhe moda: cilesia e perseritur me shpesh;**

**Tabela e Frekuences:**
```{r}
tab <- table(data$diplomimi)
print(tab)
```

**Moda:**
```{r}
moda <- names(tab)[tab == max(tab)]
print(moda)
```

**Frekuenca:**
```{r}
max_frequency = max(tab)
print(max_frequency)
```

**Tabela e Frekuences per ndryshoren cilesore $metoda$ $e$ $pageses$ dhe moda: cilesia e perseritur me shpesh;**

**Tabela e Frekuences:**
```{r}
tab <- table(data$metoda_e_pageses)
print(tab)
```

**Moda:**
```{r}
moda <- names(tab)[tab == max(tab)]
print(moda)
```

**Frekuenca:**
```{r}
max_frequency = max(tab)
print(max_frequency)
```

#### $$Tabelat\ e\ Kontigjences$$

**Tabelat e kontigjences, te njohura gjithashtu si tabela e ndarjes se kryqezuar, perdoren per te paraqitur frekuencat e kombinimeve te dy variablave ne nje format te strukturuar. Keto tabela jane te rendesishme ne analizen e lidhjeve midis variablave dhe ne zhvillimin e testimeve statistikore si testi Chi-Squared.**

**Me krijimin e ketyre tabelave interesohemi per ndonje marredhenie te mundshme midis dy variablave cilesore.**

**Me poshte do te ndertojme Tabelat e Kontigjences per variablat cilesore me ane te funksionit $table()$. Vecmas ketij funksioni do te perdorim edhe funksionin $prop.table()$ i cili do te marre si parameter emrin e tabeles se kontigjences dhe do te na afishoje perseri tabelen e kontigjences, por kesaj here me vlera probabilitare/perqindje. Pra sa perqind ze ne te dhena kjo pjese e popullimit.**

**Tabela e Kontigjences per ndryshoret $gjinia$ dhe $viti$ $i$ $studimeve:$**
```{r}
tabela1 <- table(data$gjinia, data$viti_i_studimeve)
print(tabela1)
```

**Leximi i tabeles se kontigjences eshte i tille: vlera 78 ne tabele, ne pozicionin (1,1) tregon se 78 nga gjithe popullimi jane femra dhe jane ne statusin studente te vitit te pare (freshman), 81 meshkuj qe jane ne statusin junior dhe keshtu veprojme per te gjitha vlerat e tjera ne cdo tabele tjeter kontigjence.**

```{r}
prop.table(tabela1, 1)
```

**Interpretimi: vlera 0.2414861 ne tabele tregon se 24.14861% e te dhenave jane femra dhe jane ne statusin freshman. 25.2609% jane meshkuj ne statusin senior, e keshtu me radhe. I njejti interpretim do te vleje per te gjitha tabelat e meposhtme.**

**Tabela e Kontigjences per ndryshoret $gjinia$ dhe $diplomimi:$**
```{r}
tabela2 <- table(data$gjinia, data$diplomimi)
print(tabela2)
```
```{r}
prop.table(tabela2, 1)
```

**Tabela e Kontigjences per ndryshoret $gjinia$ dhe $metoda$ $e$ $pageses:$**
```{r}
tabela3 <- table(data$gjinia, data$metoda_e_pageses)
print(tabela3)
```
```{r}
prop.table(tabela3, 1)
```

**Tabela e Kontigjences per ndryshoret $diplomimi$ dhe $metoda$ $e$ $pageses:$**
```{r}
tabela4 <- table(data$diplomimi, data$metoda_e_pageses)
print(tabela4)
```
```{r}
prop.table(tabela4, 1)
```

**Tabela e Kontigjences per ndryshoret $viti$ $i$ $studimeve$ dhe $metoda$ $e$ $pageses:$**
```{r}
tabela5 <- table(data$viti_i_studimeve, data$metoda_e_pageses)
print(tabela5)
```
```{r}
prop.table(tabela5, 1)
```

#### $$Testi\ Hi-Katror$$

**Çfare eshte nje statistike $Hi-katror$?**

**Testi χ2 shikon modelin e vezhgimeve dhe na tregon nese disa kombinime te kategorive ndodhin me shpesh sesa do te prisnim rastesisht, duke pasur parasysh numrin e pergjithshem te hereve qe ka ndodhur secila kategori. Pra kerkon nje lidhje midis variablave.**

$$Formula\ matematike:\\ χ2=\displaystyle\sum_{i=1}^{n}\frac{(O_{ij}-E_{ij})^2}{E_{ij}}\\ χ2\ eshte\ statistika\ e\ testit;\ Σ\ eshte\ operatori\ shumator;\\ O\ eshte\ frekuenca\ e\ vezhguar;\ E\ eshte\ frekuenca\ e\ pritur;$$

**Per te llogaritur vleren e Hi-katrorit ndertohet nje tabele me efektiva teorike. Keta efektiva i korrespondojne rastit kur ndryshoret jane te pavarura. Testi χ2 do te kryhet me ane te funksionit $chisq.test()$ i cili merr si parameter emrin e tabeles se kontigjences.**

**Ne gjithashtu duhet te percaktojme shkallet e lirise per tabelen tone**

**Per te zbatuar testin $Hi-katror$ ndaj dy ndryshoreve na duhet nje tabele kontigjence e tyre, te cilat i kemi ndertuar me siper.**

**Le ta zbatojme:**

**Testi Hi-katror per ndryshoret $gjinia$ dhe $viti $i$ $studimeve:$**
```{r}
test1 <- chisq.test(tabela1)
test1
```

**Ne kete rezultat, ka disa informacione kyçe qe na ndihmojne ne interpretimin e rezultateve.**

**1.	Test i kryer eshte testi Hi-katror i Pearson-it.**

**2.	Vlera e testit Hi-katror eshte 2.4488.**

**3.	Numri i shkalleve te lirise eshte 6.**

**4.	P-vlera e testit eshte 0.8742.**

**Interpretimi i ketyre rezultateve eshte si me poshte:**

**•	Vlera e testit Hi-katror 2.4488 tregon se diferenca midis te dhenave te vezhguara dhe te pranuara nuk eshte shume e madhe.**

**•	P-value 0.8742 eshte me e madhe se niveli i zakonshem i rendesise (p-value > 0.05). Kjo do te thote se duhet te pranojme hipotezen zero, e cila supozon pavaresi statistikore midis dy variablave ne tabelen e kontigjences.**


**Testi Hi-katror per ndryshoret $gjinia$ dhe $diplomimi:$**
```{r}
test2 <- chisq.test(tabela2)
test2
```

**Ne kete rezultat, ka disa informacione kyçe qe na ndihmojne ne interpretimin e rezultateve.**

**1.	Test i kryer eshte testi Hi-katror i Pearson-it.**

**2.	Vlera e testit Hi-katror eshte 7.3338.**

**3.	Numri i shkalleve te lirise eshte 8.**

**4.	P-vlera e testit eshte 0.2202.**

**Interpretimi i ketyre rezultateve eshte si me poshte:**

**•	Vlera e testit Hi-katror 7.3338 tregon se diferenca midis te dhenave te vezhguara dhe te pranuara nuk eshte shume e madhe.**

**•	P-value 0.5011 eshte me e madhe se niveli i zakonshem i rendesise (p-value > 0.05). Kjo do te thote se nuk mund te refuzojme hipotezen zero, e cila supozon pavaresi statistikore midis dy variablave ne tabele.**


**Testi Hi-katror per ndryshoret $gjinia$ dhe $metoda$ $e$ $pageses:$**
```{r}
test3 <- chisq.test(tabela3)
test3
```

**Ne kete rezultat, ka disa informacione kyçe qe na ndihmojne ne interpretimin e rezultateve.**

**1.	Test i kryer eshte testi Hi-katror i Pearson-it.**

**2.	Vlera e testit Hi-katror eshte 1.4315.**

**3.	Numri i shkalleve te lirise eshte 4.**

**4.	P-vlera e testit eshte 0.8387.**

**Interpretimi i ketyre rezultateve eshte si me poshte:**

**•	Vlera e testit Hi-katror 8.2527 tregon se diferenca midis te dhenave te vezhguara dhe te pranuara nuk eshte shume e madhe.**

**•	P-value-ja 0.8387 eshte me e madhe se niveli i zakonshem i rendesise (p-value > 0.05). Kjo do te thote se nuk mund te refuzojme hipotezen zero, e cila supozon pavaresi statistikore midis dy variablave ne tabele.**


**Testi Hi-katror per ndryshoret $diplomimi$ dhe $metoda$ $e$ $pageses:$**
```{r}
test4 <- chisq.test(tabela4)
test4
```

**Ne kete rezultat, ka disa informacione kyçe qe na ndihmojne ne interpretimin e rezultateve.**

**1.	Test i kryer eshte testi Hi-katror i Pearson-it.**

**2.	Vlera e testit Hi-katror eshte 2.352.**

**3.	Numri i shkalleve te lirise eshte 8.**

**4.	P-vlera e testit eshte 0.9683.**

**Interpretimi i ketyre rezultateve eshte si me poshte:**

**•	Vlera e testit Hi-katror 2.352 tregon se diferenca midis te dhenave te vezhguara dhe te pranuara nuk eshte shume e madhe.**

**•	P-value-ja 0.9683 eshte me e madhe se niveli i zakonshem i rendesise (p-value > 0.05). Kjo do te thote se nuk mund te refuzojme hipotezen zero, e cila supozon pavaresi statistikore midis dy variablave ne tabele.**



**Testi Hi-katror per ndryshoret  $viti$ $i$ $studimeve$ dhe $metoda$ $e$ $pageses:$**
```{r}
test5 <- chisq.test(tabela5)
test5
```

**Ne kete rezultat, ka disa informacione kyçe qe na ndihmojne ne interpretimin e rezultateve.**

**1.	Test i kryer eshte testi Hi-katror i Pearson-it.**

**2.	Vlera e testit Hi-katror eshte 8.2527.**

**3.	Numri i shkalleve te lirise eshte 6.**

**4.	P-vlera e testit eshte 0.2202.**

**Interpretimi i ketyre rezultateve eshte si me poshte:**

**•	Vlera e testit Hi-katror 8.2527 tregon se diferenca midis te dhenave te vezhguara dhe te pranuara nuk eshte shume e madhe.**

**•	P-value-ja 0.2202 eshte me e madhe se niveli i zakonshem i rendesise (p-value > 0.05). Kjo do te thote se nuk mund te refuzojme hipotezen zero, e cila supozon pavaresi statistikore midis dy variablave ne tabele.**



### **`r colorize("Paraqitje Grafike", "blue")`**

#### $$VIZUALIZIMI\ I\ TE\ DHENAVE$$

**$Vizualizimi$ $i$ $te$ $dhenave$ eshte teknika e perdorur per te dhene njohuri ne te dhena duke perdorur metoda vizuale si grafiket, diagramat, histogramat, hartat dhe shume trajta te tjera. Kjo eshte e dobishme pasi ndihmon ne kuptimin intuitiv dhe te lehte te sasive te medha te te dhenave dhe ne kete menyre per te marre vendime me te mira ne lidhje me to.**

**R eshte nje gjuhe qe eshte krijuar per llogaritje statistikore, analiza grafike te te dhenave dhe kerkime shkencore. Zakonisht preferohet per vizualizimin e te dhenave pasi ofron fleksibilitet dhe kodim minimal te kerkuar permes paketave te saj.**

**Vizualizimi i te dhenave ne analizen e te dhenave ka rendesi te madhe per disa arsye:**

**1.	Kuptimi i mire i te dhenave;**

**2.	Interpretimi i rezultateve: Vizualizimi i te dhenave eshte nje menyre e mire per te komunikuar rezultatet e analizes. Grafiket jane me te lehte per t'u kuptuar dhe per te shpjeguar se si ndryshojne te dhenat ne kohe, hapesire ose ndaj nje variabli tjeter.**

**3.	Zbulimi i modeleve dhe tendencave;**

**Sigurisht, per paraqitjen grafike sa me egzakte dhe estetike te te dhenave do te na duhen disa librari kryesore, sic jane $ggplot2$, $correlation$, $ggpubr$ & $tidyr$, $dataExplorer$ etj.;**



#### $$Histogrami$$

**Nje $histogram$ eshte nje paraqitje vizuale e shperndarjes se te dhenave sasiore. Ata japin nje kuptim te perafert te densitetit dhe shpesh here vleren e sakte te tij.**

**Me poshte do te ndertojme nje histogram per variablin tone sasior $mosha$. Do te na duhen 2 librari kryesore: $ggplot2$ e cila sherben per ndertimin e grafikeve dhe libraria $scales$ e cila do te na sherbeje per kostumizimin e grafikut.**

**Per te paraqitur grafikisht nje ndryshore sasiore te vazhdueshme ndertohet nje histogram.**

**Per kete qellim intervali I vlerave te mundshme te tiparit ndahet ne nje numer intervalesh ose klasash.**

**Histogrami paraqet se sa eshte numri i studenteve per secilen grupmoshe duke filluar nga 18 vjec deri ne 25. Nga lartesia e kolonave veme re se pjesen me te madhe e ze mosha 25 vjec (moda) dhe me te voglen mosha 19 vjec.**

```{r}
library(ggplot2)
library(scales)

g1 <- hist(data$mosha, breaks=seq(17.5, 25.5, by=1), density = 40, angle=60, xlab="Grupmoshat e studenteve", ylab="Efektivat", main="Histogrami i Moshes", las=1, col="purple4", fill = "purple4",
          ylim=c(0,200),xlim=c(18,25), cex.main=1.4, cex.lab=1.2, axt='n')

#kustomizojme grafikun me disa vija te pjerreta 60  degrees
axis(1, at=18:25, labels=18:25)
text(g1$mids, g1$counts, labels=ifelse(g1$counts != 0, g1$counts, ""), pos=3, cex=0.8)

```
**Per te ndertuar histogramin na sherben libraria $ggplot2$ dhe $scales$.**

**Me ane te te funksionit $hist()$ percaktojme llojin e grafikut qe duam te ndertojme, ne kete rast histogram.**

**$data$`$`$mosha$: therrasim te dhenat te cilat do te paraqesim ne histogram.**

**$breaks=seq(17.5, 25.5, by=1)$ percakton kufijte e histogramit, qe variojne nga 17.5 ne 25.5, me hap 1.**

**$density=40$: denduria e vijave brenda shtyllave te histogramit;**

**$angle=60$: vendosim nje kend per vijat brenda histogramit;**

**$xlab$, $ylab$ dhe $main$: percaktojne emertimin e boshteve x, y dhe titullin e histogramit;**

**$las=1$ pozicionon emertimet e boshteve;**

**Vendosim ngjyrat me ane te funksionit $col=""$;**

**$ylim=c(0,200)$ dhe $xlim=c(18, 25)$ vendos kufijte e vlerave te histogramit;**

**$cex.main=1.4$ dhe $cex.lab=1.2$ rrit madhesine e shkrimit te titullit kryesore dhe emertimeve te boshteve;**

**$axt=n$ heq emertimet e meparshme te boshtit x;**

**$axis(1, at=18:25, labels=18:25)$ shton shenjat dhe emertimet e bushtit x nga 18 ne 25;**

**$text(g1$`$`$mids$, $g1$`$`$counts$, $labels=ifelse$($g1$`$`$counts$ $!=0$, $g1$`$`$counts$, “”), $pos=3$, $cex=0.8)$ shton vlerat numerike siper cdo shtylle, por vetem ne rastet kur vlerat jane te ndryshme nga zero. Parametri $pos=3$ pozicionon vlerat ndersa $cex=0.8$ percakton madhesine e shkrimit.**

**Interpretimi i histogramit eshte relativisht i thjeshte. Shohim qe shperndarja e studenteve eshte e tille: 124 individe kane moshen 18 vjecare, 108 jane 19 vjecare, 111 jane 20 vjecare, 118 jane 21 vjecare, 130 jane 22 vjecare, 128 kane moshen 23 vjec, 136 jane 24 vjecare dhe 145 jane 25 vjecare. Ajo qe vihet re tjeter eshte edhe se cila nga grupmoshat eshte me e shpeshte: eshte ajo 25 vjecare me 145 individe, ndersa ajo me pak eshte grupmosha 19 vjecare me 108 individe.**


#### $$Grafiket\ Violine$$

```{r}
library(ggplot2)
library(gridExtra)

violinplot1 <- ggplot(data, aes(x = "", y=data$te_ardhurat_mujore)) +
  geom_violin(fill="dodgerblue2", color="black") +
  labs(title = "Violin PLot per te Ardhurat Mujore", x="Te Ardhurat Mujore", y="Shperndarja")

violinplot2 <- ggplot(data, aes(x = "", y=data$ndihma_financiare)) +
  geom_violin(fill="dodgerblue2", color="black") +
  labs(title = "Violin PLot per Ndihmen Financiare", x="Ndihma Financiare", y="Shperndarja")

grid.arrange(violinplot1, violinplot2, ncol=2)
```

**Forma e grafikut violine tregon shperndarjen e te ardhurave mujore dhe te ndihmes financiare. Ne pjeset ku grafiku eshte me i gjere do te thote se ka me shume te dhena rreth atyre vlerave. Kur eshte me i ngushte atehere ka me pak te dhena. Vlera mesatare tregohet nga brezi me i gjere qe ndodhet ne qender. Nje shperndarje me te madhe kane vlerat qe jane teorikisht midis 1250-1500, pasi aty dallohet nje brez me i gjere. Ndersa ne rastin e ndryshores tjeter vlerat kane nje shperndarje me te larte ne intervalin 500-600. Pra ,te ardhurat mujore mesatare sipas grafikut jane afersisht $1020.65 ,ndersa ndihma financiare mesatare eshte  afersisht $504**



#### $$Box plot$$

**Nje $box$ $plot$ eshte nje lloj grafiku statistikor i cili ofron nje permbledhje vizuale te shperndarjes se nje grupi te dhenash. Ai shfaq informacionin kryesor te meposhtem:**

**1. Mesoren: Vlera mesore perfaqesohet nga vija horizontale brenda kutise;**

**2. Intervali Nderkuartilor: kutia perfaqeson 50% te vlerave te mesit te te dhenave, fundi I saj tregon 25% te te dhenave dhe pjesa e siperme tregon 75% te tyre. IQR eshte diferenca Q3 – Q1.**

**3. Vlerat maksimale dhe minimale: jane ato vija vertikale qe dalin nga kutia.**

```{r}
library(ggplot2)

ggplot(data)+aes(x=mosha, y=gjinia, fill=viti_i_studimeve, colour = te_ardhurat_mujore, size=ndihma_financiare)+
  geom_boxplot()+ scale_fill_hue(direction=2) + scale_color_gradient() +
  labs(x="Mosha", y="Gjinia", fill="Viti i Studimeve")+
  theme_classic()
```

**Ne kete grafik eshte paraqitur nje boxplot i cili tregon lidhjen midis gjinise dhe vitit te studimit te studenteve. Per gjinine femerore jane paraqitur 4 box-plote per kategorine e Freshman, Junior, Senior, Sophomore. Nga box-plotet arrijme te dallojme qe vlera min per te katert eshte 18, ndersa vlera max 25. Keto jane dy vlerat ne skaje. Ana e majte tregon kuartilin e pare qe ne rastin e Sophomore dhe Junior eshte 20, ndersa per Senior dhe Freshman eshte 19. Vija ne mes tregon $mesoren$, perkatesisht 21 per Junior dhe Senior dhe 22 per Freshman dhe Sophomor. Ana e djathte tregon kuartilin e trete, 24 per Sophomore dhe 23 per Junior dhe Senior. Meqe jashte box-plotit nuk kemi pika te tjera atehere themi se nuk ka $outliers§$. Njesoj veprojme dhe per te tjeret.**


```{r}
library(ggplot2)

ggplot(data, aes(x=gjinia, y=mosha, fill=gjinia)) +
  geom_boxplot(outlier.shape = NA)+
  geom_jitter(aes(color=gjinia, shape=gjinia), width=0.2, size=1.5) +
  scale_color_manual(values=c("black", "gold", "red"))+
  scale_fill_manual(values = c("blue", "red", "green"))+
  labs(title = "Box Plot Gjinia~Mosha", x="Gjinia", y="Mosha", fill="Gjinia", color="Gjinia", color="Gjinia", shape="Gjinia")+ theme_classic()
```


**Rezultatet dhe interpretimi I tyre:**

**Sipas grafikut te mesiperm, kutite e krijuara shprehin shperndarjen e moshes sipas gjinise. Meset e kutise se box-ploteve bien ne moshen 22, per te treja rastet. Pikat jitter tregojne shperndarjen e te dhenave ne secilin grup.**

**Kodi:**

**Fillimisht therrasim librarite qe na nevojiten: $ggplot2$, e cila na ndihmon per vizualizimin e te dhenave.**

**Krijojme nje variable te quajtur $data$ e cila do te permbaje dy parametra kryesore:**

**i: $mosha$;**

**ii: $gjinia$;**

**Krijimi I box plot pergjithesisht eshte I njejte si ne rastin e mesiperm, me perjashtim te funksionit $geom$`_`$jitter()$ I cili shton nje sasi te vogel pikash qe tregojne nje shperndarje sipas kutise se box plot.**

**Shtimi i linjave te references:**

**$scale$`_`$color$`_`$manual()$ vendos ngjyren e pikave jitter ne box plot. Ngjyra blu perdoret per femrat, e kuqja perdoret per meshkujt ndersa gold per ata non-binary;**

**$scale$`_`$fill$`_`$manual()$ vendos ngjyren e mbushjes se kutive;**

**$labs()$ shton titullin, emertimet e boshteve $x$,$y$ dhe legjenden.**


#### $$Grafiku\ Densitet$$

```{r}
library(ggplot2)
ggplot(data, aes(x=ushqimi))+
  geom_density(aes(fill="Ushqimi"), alpha=0.5)+
  geom_density(aes(x=strehimi, fill="Strehimi"), alpha=0.5)+
    geom_density(aes(x=transporti, fill="Transporti"), alpha=0.5)+
    geom_density(aes(x= mjetet_shkollore, fill="Mjetet Shkollore"), alpha=0.5)+
  geom_density(aes(x=argetim, fill="Argetimi"), alpha=0.5) +
  labs(x="Vlera", y="Densiteti", title="Grafiku Densitet per 5 variabla numerike", fill="Legjenda:")+
  scale_fill_manual(values=c("dodgerblue2", "red", "purple3", "green2", "yellow2"))+
  theme_classic()
```

**Rezultati:**

**Ketu kemi paraqitur grafikun e densiteteve per 5 ndryshore numerike (argetimi,mjetet shkollore ,strehimi,transporti,ushqimi).**

**Boshti i y paraqet densitetin e secilit variabel brenda intervalit te vlerave te dhena(boshti x). Dendesia i referohet sa shpesh ndodhin vlerat brenda nje intervali specifik. Zona nen cdo kurbe perfaqeson perqindjen e te te dhenave qe ndodhen brenda nje intervali. Nje kurbe me e larte (densitet me te larte) do te thote qe me shume te dhena kane vlera rreth asaj pike ne boshtin X. Ne grafikun tone shohim qe kategoria $argetim$ ka densitet me te madh duke qene se kurba eshte me e larte ,ndersa $strehimi$ ka densitet me te vogel. Lartesia e kurbave eshte shkallezuar ne menyre qe siperfaqja nen kurbe te jete e barabarte me 1.**


#### $$Grafiku\ Mozaik$$

**Nje nje projekt Data Science eshte shume e rendesishme nxjerja e sa me shume rezultateve dhe perfundimeve te nevojshme nga te dhenat tona. Ne nje nga fazat e analizes se te dhenave eshte edhe ajo e vizualizimit te cilen jemi duke e trajtuar akualisht.**

**Nje karakteristike e vecante eshte marredhenia midis dy variablave. Nese te dyja variablat jane cilesore (kategorike), atehere, per te shprehur nje marredhenie mes tyre ne perdorim ate qe quhet $Grafiku$ $Mozaik$. Ne disa disiplina nuk njihet, por ne R eshte i shpeshte dhe teper i nevojshem ne disa raste.**

**Grafiku Mozaik bazohet ne te dhena probabilitare. Per ti marre keto te dhena na nevojiten tabelat; $tabelat$ $e$ $kontigjences$.**

**Me siper, ne kreun $Tabelat$ $e$ $Kontigjences$ ne kemi ndertuar keto tabela per variablat tona kategorike dhe gjithashtu me ane te funksionit $prop.table$ ne konvertuam keto tabela kontigjence ne tabela me vlera probabilitare.**

**Jane pikerisht keto tabela te cilat do te na hyjne ne pune.**

**Me poshte eshte ndertuar nje grafik mozaik per tabelen e katert te kontigjences $diplomimi$`~`$metoda$`_`$e$`_`$pageses$:**

```{r}
library(ggplot2)
ggplot(data) + aes(x=diplomimi, y=metoda_e_pageses, fill=gjinia, colour=viti_i_studimeve, group = metoda_e_pageses)+
  labs(x="Diplomimi", y="Metoda e Pageses", title = "Grafiku Mozaik i Metodes se Preferuar te Pageses", fill="Legjenda:")+
geom_tile()+
  scale_fill_manual(values=c(Female="gold", Male="red",`Non-binary`="cyan" ))+
  scale_color_manual(values = c(Female="gold", Male="red", `Non-binary`="cyan"))+
  theme_minimal()
```

**Analizojme kodin:**

**Variabli $data$ permban te dhenat tona;**

**Funksioni $aes()$ do te kombinoje te dhenat ne estetikat e ndryshme ne grafik;**

**$x = diplomimi$: I atribon variablin $diplomimi$ boshtit x;**

**$y=metoda$`_`$e$`_`$pageses$: I atribon variablin $metoda$ $$e $pageses$ boshtit y;**

**$fill = gjinia$: do te ndihmoje ne ngjyrosjen e copezave te grafikut mozaik;**

**$color=viti I studimeve$: I atribon variablin $viti$ $i$ $studimeve$ ngjyres se copezave;**

**$group = metoda$`_`$e$`_`$pageses$: grupon copezat bazuar ne variablin $metoda$ $e$ $pageses$;**

**Etiketimi: funksioni $labs()$ vendos titujt per boshtet x, y.**

**$geom$`_`$tile()$: krijon grafikun mozaik, ku cdo copez perfaqeson kombinimin e ndryshoreve $diplomimi$ dhe $metoda$ $e$ $pageses$;**

**Ngjyrat: funksionet $scale$`_`$fill$`_`$manual()$ dhe $scale$`_`$color$`_`$manual()$ perdoren per te ngjyrosur secilen nga pllakat e grafikut bazuar ne percaktimet  e mesiperme.**

**Grafiku mozaik paraqet nje pamje vizuale te marredhenies midis Variablave $diplomimi$, $metoda$ $e$ $pageses$, $gjinia$ dhe $viti$ $i$ $studimeve$. Madhesia, ngjyrimi dhe pozicionimi I copezave te grafikut percjell frekuencat relative te secilit kombinim prej ketyre Variablave cilesore.**


**Rezultatet:**

**Metoda e Pageses: boshti $y$ shfaq tre metodat e pageses; $Cash$, $Aplikacion$ dhe $Karte$ $Krediti$.**

**Gjinia: cdo pjesez ne grafik eshte e ngjyrosur per te perfaqesuar gjinine.**

**Diplomimi: boshti $x$ I kategorizon njerezit sipas diplomimit te tyre.**

**Nga grafiku dalim ne perfundimin se: **

**Metoda me e popullarizuar e pageses eshte ajo $Cash$, ndjekur nga $Karta$ $e$ $Kreditit/Debitit$ dhe me pak ajo nepermjet aplikacioneve.**

**Kategoria gjinore me e shpeshte eshte ajo $Non-binary$ e cila ndeshet me teper ne grafik (ngjyra blu e celet).**

**Mes te diplomuarve aplikacionet jane me pak te perdorura se kartat e kreditit.**

#### *Kujdes: grafiku mozaik nuk na tregon asgje per numrin e personave qe perdorin keto metoda pagese;*

**Madhesia e copezave nuk tregon asnjehere se sa eshte numri i individeve qe e perbejne ate pjese. Ajo tregon vetem proporcionin relative brenda cdo kategorie te metodes se preferuar te pageses.**

#### $$Grafiku\ me\ Shtylla$$

```{r}
library(plotly)
plot_ly (data, x=~diplomimi, color =~ metoda_e_pageses, colors="Accent")
```

**Grafikut te cilit i referohemi eshte nje grafik me shtylla qe tregon perdorimin e metodave te ndryshme te pageses ne disiplina te ndryshme akademike.**

**Nga grafiku arrijme te dallojme qe studentet e shkencave kompjuterike dhe inxhinierise duken kryesisht indiferente, duke shfaqur pak ndryshime ne zgjedhjet e tyre te metodes se pageses. Nje kontrast i forte shfaqet midis studenteve te ekonomise dhe biologjise ,ku egzistojne pabarazi te konsiderueshme ne preferencat e tyre midis pagesave elektronike dhe atyre me para.**

**Gjithashtu dhe studentet e psikologjise shfaqin pabarazi te dukshme ne zgjedhjen e metodes se pageses ,ku me e preferuar rezulton $Mobile$ $Payment$ $App$. Kjo metode rezulton gjithashtu e preferuar dhe nga studentet e inxhinierise. Ndersa per studentet e ekonomise dhe biologjise me e preferuara rezulton metoda $Credit/Debit$ $Card$.**


#### $$Pie\ Chart$$

**Kodi I meposhtem afishon nje $pie$ $chart$ qe vizualizon shpenzimet totale ne kategori te ndryshme shpenzimesh per te dhenat tona numerike.**

```{r}
library(ggplot2)
library(tidyverse)

shpenzimet_totale <- data.frame( kategorite_e_shpenzimit = c("shkollimi","strehimi","ushqimi","transporti","mjetet_shkollore","argetim","kujdesi_personal","teknologji","mireqenia_shendetesore","te_ndryshme"),
shpenzimet = c(sum(data$shkollimi), sum(data$strehimi), sum(data$ushqimi), sum(data$transporti), sum(data$mjetet_shkollore), sum(data$argetim), sum(data$kujdesi_personal), sum(data$teknologji), sum(data$mireqenia_shendetesore), sum(data$te_ndryshme)))

#llogaritim perqindjen per secilen kategori:
shuma_totale <- sum(shpenzimet_totale$shpenzimet)
shpenzimet_totale$percentage <- round(shpenzimet_totale$shpenzimet / shuma_totale * 100, 2)

#grafiku
ggplot(shpenzimet_totale, aes(x="", y=shpenzimet, fill=kategorite_e_shpenzimit, type='3D pie')) +
  geom_bar(stat="identity", width = 2) +
  geom_text(aes(label=paste0(percentage, "%")), position=position_stack(vjust=0.6), size = 2, color="black", fontface="bold") +
coord_polar("y", start=1)+
  labs(title="Shpenzimet Totale sipas Kategorive", x=NULL, y=NULL)+
  scale_fill_manual(values = c("lightblue", "orange", "green", "red","blue","yellow","maroon3", "cyan", "pink2","purple") )+
  theme_void()+
  theme(plot.title = element_text(hjust=0.5, size=15, face="bold"),
        legend.title=element_blank(),
        legend.text = element_text(size=8),
        legend.position = "right")

```


**Interpretimi:**

**Kodi krijon nje permbledhje te te gjitha shumave te shpenzuara per te gjitha kategorite (shkollimi, ushqimi, transporti etj.). **

**1. $shpenzimet$`_`$totale$ paraqet shumen totale te te gjitha shpenzimeve te kryera.**

**2. $Llogaritja$ $e$ $perqindjeve$: kodi llogarit perqindjen e seciles nga shpenzimet totale te kryera, cfare pjese do te zere secila pjese e shpenzimeve ne pie chart. Ato do te paraqiten te rrumbullakosura ne 2 shifra pas presjes dhjetore.**

**3. Vizualizimi I pie chart-it: Funksioni $ggplot()$ perdoret per te krijuar kete grafik.**

**Funksioni $aes()$ lidh kategorite e shpenzimeve me $fill()$ aesthetic dhe shpenzimet totale me y aesthetic.**

**Funksioni $geom$`_`$bar()$ perdoret per te krijuar copetimet/copat e grafikut pie, ku se bashku me parametrin $width$, jep nje efekt 3D.**

**$geom$`_`$text()$ perdoret per te shtuar vlerat e perqindjes ne copat perkatese. Parametri $position()$ vendos keto vlera brenda copave, pra I pozicionon ato. **

**Funksioni $coord$`_`$polar()$ perdoret per te transformuar krafikun drejtkendor ne nje grafik rrethor (rreth). $scale$`_`$fill$`_`$manual()$ perdoret per te vendosur ngjyra te vecanta per secilen nga copat e pie chart-it.**

**Funksioni $theme$`_`$void()$ perdoret per te ndertuar legjenden e cila na sherben per orientim ndaj te dhenave te paraqitura ne pie chart.**

**Ky lloj vizualizimi eshte I rendesishem per te kuptuar shperndarjen e shpenzimeve dhe identifikimin e kategorive me te rendesishme te kostos per te dhenat qe ne disponojme.**


#### $$Korrelacioni\\ Matrica\ e\ Korrelacionit\\ Regresi\ Linear$$

**Korrelacioni eshte cdo marredhenie statistikore midis dy ndryshoreve te rastit. Zakonisht i referohet shkalles ne te cilen nje pale ndryshoresh jane te lidhura ne menyre lineare.**

$$Formula\ matematike:\\ {𝜌(𝑋,𝑌)} = {\frac{\displaystyle\ S_{xy}} {{S_x}{S_y}}}$$

**Me poshte do te ndertojme matricen e korrelacionit ne baze te se ciles do te ndertohet drejteza e regresit linear.**

**Ngjyra blu do te tregoje nje lidhje te dobet mes variablave, ndersa ngjyra e kuqe do te tregoje nje lidhje te forte mes tyre.**

```{r}
correlation_matrix <- cor(numeric_df)

library(pheatmap)
pheatmap(correlation_matrix,
         color = colorRampPalette(c("darkblue", "white", "red3"))(200),
         fontsize = 10,
         fontsize_row = 8,
         fontsize_col = 8,
         main = "Correlation Heatmap i Variablave Numerike",
         display_numbers = TRUE,
         number_color = "white" )
```

**Per te arsyetuar mbi varesine ndermjet ndryshoreve numerike shikojme grafikun dhe vlerat e koeficienteve te korrelacionit.**

**Nga matrica verejme se te dhenat nuk kane nje lidhje te forte me njera tjetren, dhe kjo percaktohet nga ngjyrimi blu i kufizave te matrices.Ne do te zgjedhim disa ndryshore qe mendojme se kane pak varesi me njera tjetren (dy qe e kane ngjyren me te zbehte).**

```{r}
library(ggplot2)
library(ggpubr)

ggplot(data, aes(x = argetim, y = te_ardhurat_mujore)) +
  geom_point(color = "#FF0000",size=0.9) +
  labs(x = "Shpenzimet per argetim", y = "Te ardhurat mujore", title = "Shpenzimet per argetim krahasuar me te ardhurat mujore") +
  geom_smooth(method = "lm", color = "black", formula = y ~ x) +
  stat_cor(label.x = 100, label.y = 1400, size = 5) +
  stat_regline_equation(label.x = 100, label.y = 1300, size = 5)
```



```{r}
library(ggplot2)
library(ggpubr)

ggplot(data, aes(x = transporti, y = te_ardhurat_mujore)) +
  geom_point(color = "black",size=0.9) +
  labs(x = "Shpenzimet per transport", y = "Te ardhurat mujore", title = "Shpenzimet per transport krahasuar me te ardhurat mujore") +
  geom_smooth(method = "lm", color = "black", formula = y ~ x) +
  stat_cor(label.x = 100, label.y = 1400, size = 5) +
  stat_regline_equation(label.x = 100, label.y = 1300, size = 5)
```



```{r}
library(ggplot2)
library(ggpubr)

ggplot(data, aes(x = shkollimi, y = te_ardhurat_mujore)) +
  geom_point(color = "blue", size = 1) +
  labs(x = "Shkollimi", y = "Te ardhurat mujore", title = "Shpenzimet per shkollim krahasuar me te ardhurat mujore") +
  geom_smooth(method = "lm", color = "black", formula = y ~ x) +
  stat_cor(label.x = 4000, label.y = 1400, size = 5, alpha = 2) +
  stat_regline_equation(label.x = 4000, label.y = 1300, size = 5, alpha = 2)
```



```{r}
library(ggplot2)
library(ggpubr)

ggplot(data, aes(x = kujdesi_personal, y = te_ardhurat_mujore)) +
  geom_point(color = "purple3", size = 1) +
  labs(x = "Shpenzimet per kujdes personal", y = "Te ardhurat mujore", title = "Shpenzimet per kujdes personal krahasuar me te ardhurat mujore") +
  geom_smooth(method = "lm", color = "black", formula = y ~ x) +
  stat_cor(label.x = 15, label.y = max(data$te_ardhurat_mujore) * 0.95, size = 5) +
  stat_regline_equation(label.x = 15, label.y = max(data$te_ardhurat_mujore) * 0.90, size = 5)
```

**Nga grafiket e ndertuar me siper se bashku me drejtezat e regresit shohim qe lidhja ndermjet te ardhurave mujore dhe shpenzimeve sipas kujdesit personal, transportit, shkollimit dhe argetimit eshte shume pak lineare. Ne po marrim ne shqyrtim njerin grafik prej tyre.**


$$Koeficenti\ i\ Korrelacionit$$

**Koeficenti i korrelacionit na ndihmon te kuptojme nese ndermjet te dhenave ka lidhje lineare apo jo.**

**Vetite e tij:**

**Koeficenti i korrelacionit merr vlera nga -1 ne 1.**

**Nese vlera e ketij koeficenti eshte afer 0 (midis -0.2 dhe 0.2 ) na tregon se ndermjet variablave nuk ka nje varesi lineare.**

**Mund te perdorim dy funksione per te pare vleren e korrelacionit qe jane pjese e librarise status:**

**1.$cor.test$**

**2.$cor$;**

```{r}

cor(data$transporti, data$te_ardhurat_mujore)

koeficentet <- cor.test(data$transporti,data$te_ardhurat_mujore)

koeficentet$estimate
```

**Shohim qe vlera e koeficentit te korrelacionit eshte 0.04615186 qe eshte shume prane 0.**

**Pra midis variablave nuk ka nje lidhje lineare.**

**Po te veme re dhe grafiket e tjere dhe drejtezat e tyre, gjithashtu nuk ka nje varesi te dukshme.**

#### $$Ndertimi\ i\ nje\ modeli\ te\ thjeshte\ linear$$

  $$Y\ = \  β_0\ +\  β_1\ +\ gabimi\\ ku\  β_0\ dhe\  β_1\ jane\ parametrat\ e\ vijes$$

**Perdorim funksionin $lm()$ per te ndertuar nje model linear.**

```{r}
set.seed(123)
zgjedhja<-sample(c(TRUE,FALSE),nrow(data),replace=T,prob=c(0.6,0.4))
```

**Specifikojme qe te dhenat do te ndahen 40% testues dhe 60% trajnues; ndajme te dhenat ne test dhe train:**

```{r}
train<-data[zgjedhja,]
test<-data[!zgjedhja,]
```

**Ndertohet modeli duke marre si te dhena te dhenat train (trajnuese)**

```{r}
model1<-lm(transporti~te_ardhurat_mujore,data= train)
model1
```

$$Miresia\ e\ modelit$$
**Per te kontrolluar miresine e nje modeli shikojme:**

**1.$RSE->residual$ $standart$  $error$: eshte distanca mesatare qe vlerat e vezhguara te jene larg vleres se modelit. Sa me e vogel kjo vlere aq me i mire modeli sepse kuptojme qe vlerat qe jep modeli ndodhen afer atyre qe jane vlera te verteta.**

**2.$R^2$-> na tregon sasa perqind te dhenave te shpjegohen nga modeli.**

**3.$p-value$->nese kjo vlere eshte me e vogel se 0.05 atehere themi qe kemi nje lidhje te rendesishme ndermjet ndryshoreve.**

**Bejme nje summary te modelit per te pare perfundimet:**

```{r}
summary(model1)
```

**Shohim qe:**

**Residual standard error: 43.93.**
**Kjo do thote qe shpenzimet reale per transport devijojne nga modeli linear ne vleren 43.93. Mund ta kthejme ne %:**

```{r}
mesatarja_RSE<-sigma(model1)/mean(train$transporti)
sprintf("Gabimi ne perqindje i modelit:%s%%",round(mesatarja_RSE*100,2))
```

**Gabimi ne % eshte 35.54%. Kjo do te thote se modeli yne nuk pershtatet shume mire me te dhenat e verteta.**

**Vlera e R^2 = 0.001228 modeli shpjegon 0.1228% te te dhenave, pothuajse aspak.**


**Kontrollojme mbetjet e modelit:**

**Mbetja eshte distanca ndermjet vleres aktuale dhe asaj qe jep modeli qe ne kemi ndertuar.**

```{r}
vlerat_e_modelit <- predict(model1, data = train)
 vlerat_e_modelit
 mbetjet_e_modelit <- resid(model1)
 mbetjet_e_modelit
```

**Ne te dhenat tona trajnuese mund te shtojme nje kolone te re qe permban vlerat qe parashikon modeli.**

```{r}
train$vlerat_e_modelit<-predict(model1)
 train$mbetjet_e_modelit<-residuals(model1)
 View(train)

 grafik1<-ggplot(train,aes(transporti , te_ardhurat_mujore)) + geom_point() + geom_point (aes(y = vlerat_e_modelit,color = "red2"))
 grafik1
```

**Mund te ndertojme segmentet qe paraqesin gabimet:**

```{r}
library(ggplot2)

grafik2 <- ggplot(train,aes(transporti ,te_ardhurat_mujore))+geom_point() + labs(x="Transporti", y= "Te Ardhurat Mujore") + geom_point(aes(y=vlerat_e_modelit),color="blue")+geom_segment(aes(xend= transporti, yend=vlerat_e_modelit),color="red")
grafik2
```


```{r}
library(correlation)

plot(data$ushqimi, data$mjetet_shkollore)
cor(data$ushqimi,data$mjetet_shkollore)
model1<-lm(ushqimi ~ mjetet_shkollore, data=data)
model1

```

```{r}
library(ggplot2)

ggplot(data) + aes(x = ushqimi, y= mjetet_shkollore) +
  geom_point(size = 1L, colour = "#000000") +
  geom_smooth(method = "lm", formula  = y~x, se = TRUE, color = "blue") +
  stat_cor(label.x=2, label.y=4) +
  stat_regline_equation(label.x=1, labe.y=2, size=3) +
  labs(x = "Ushqimi", y = "Mjetet Shkollore",
       title = "Shpenzimet per ushqim vs Shpenzimet per Mjete Shkollore",
       subtitle = "A ndikojne shpenzimet ne ushqyerje ne ato per mjete shkollore?") +
  theme_classic()
```

**Le te analizojme nje nga rezultatet e regreseve te ndertuara me siper:**

**REZULTATI: Nga pergjigjja e mesiperme ne modelin $Shpenzimet$ $per$ $ushqim$ $vs$ $Shpenzimet$ $per$ $Mjete$ $Shkollore$ kemi se ekuacioni qe i pershtatet ketij modeli regresi eshte**

$$Vleresimi\ = \ 160\ +\ 0.063X$$
**qe do te thote se per cdo njesi shpenzimi ne ushqim, kemi nje rritje me 0.063 njesi ne mjete shkollore.**

**Mundemi te gjejme edhe intervalin e besimit nepermjet funksionit $confint()$:**

```{r}
confint(model1, level = 0.95)
```

**Sic duket edhe nga rezultati, intervali i besimit eshte [222.73 ; 250.86]**

**Funksioni $predict()$ parashikon se sa do te jete vlera e ndryshores se varur kur jepen disa vlera te ndryshores se pavarur.**

```{r}
summary(model1)
```

**Interpretimi i rezultateve te modelit:**

**1. $Interpretimi$ $i$ $mbetjeve$: mbetjet paraqesin diferencat midis vlerave te vezhguara te ndryshores se varur $ushqimi$ dhe vlerave te parashikuara nga modeli. Rangu i mbetjeve te modelit sugjeron qe modeli nuk i pershtatet ne menyre te persosur te dhenave. Mbetja minimale eshte -160.913, Kuartili i pare eshte -77.172, mesatarja eshte 3.852, Q3 eshte 74.67  dhe vlera e mbetur 155.764 eshte mbetja maksimale.**

**2. $Intercept$ $(nderprerja)$ 236.80006 paraqet vleren e parashikuar te ndryshores se varur $ushqimi$ kur ndryshorja e pavarur $mjetet$ $shkollore$ eshte 0. Koeficienti per variablin e pavarur eshte 0.09065. Kjo do te thote qe per cdo rritje prej 1 njesi ne variablin e pavarur, ndryshorja e varur parashikohet te rritet me 0.09065 njesi, duke mbajtur te gjithe variablat e tjere konstante.**

**3. $P-value$: vlera $p$ per variablin e pavarur eshte 0.01696, e cila eshte me e vogel se niveli i rendesise 0.05. Kjo tregon se lidhja midis variablit te pavarur dhe ndryshores se varur eshte statistikisht e rendesishme, qe do te thote se ndryshorja e pavarur ka nje efekt te rendesishem ne variablin e varur.**

**4. $Vlera$ $R^2$ eshte 0.005698, qe do te thote se ndryshorja e pavarur shpjegon rreth 0.57% te variances ne variablin e varur.**

**Ne menyre te permbledhur rezultatet sugjerojne se variabli i pavarur $mjetet$ $shkollore$ ka nje efekt statistikisht domethenes por relativisht te vogel ne variablin e varur $ushqimi$.**

**Duke qene se modeli yne ka 3 yje, aq me shume te rendesishme jane rezultatet e modelit te ndertuar.**

**Nese bejme plot te modelit qe kemi krijuar ate do te marrim 4 grafike:**

**1.Residuals vs Fitted;**

**2.Normal Q-Q;**

**3.Fitted vs sqrt (standardized residuals);**

**4.Leverage vs standardized residuals; **

$$Scale\ Location\ Plot$$

```{r}
model <- lm(ushqimi~mjetet_shkollore, data = data)

plot(model)

```

$$Residuals\ vs\ Fitted\ Plot$$
**Grafiku i pare na tregon qe nuk kemi nje varesi lineare ndermjet te dhenave tona. Pra nuk jemi ne homoskedasticitet.**


$$Q-Q\ Plot$$
**Nje menyre tjeter paraqitje per te dhenat tona eshte dhe grafiku Normal Q-Q. Ky lloj grafiku perdoret per te percaktuar nese nje grup te dhenash jane apo jo  te shperndara normalisht. Nese ato jane, atehere te gjitha pikat e tij duhet te shtrihen ne nje vije te drejte diagonale. Ne rastin tone te dhenat nuk perputhen shume mire me shperndarjen normale, sepse nje pjese e konsiderueshme e pikave nuk shtrihen mbi drejtez. Kjo do te thote se shpenzimet minimale per ushqim nuk jane mjaftueshem te ulta sa duhen per tu perputhur me drejtezen dhe shpenzimet max nuk jane mjaftueshem te larta sa te shtrihen mbi drejtez. Kjo tregon se bishtat e shperndarjes jane shume "te dobet" ne krahasim me shperndarjen.**

$$Scale\ Location\ Plot$$

**Grafiku Scale-Location eshte i njejte me grafikun e pare, por me ndryshimin qe ne boshtin vertikal kemi mbetjet e standartizuara. Shikohet dhe ketu lidhja ndermjet mbetjeve te standartizuara dhe vlerave te pershtatura dhe shikohet homoskedasticiteti. Ne rastin tone po te shikohet vija e kuqe ajo eshte thuajse horizontale pra nuk ka ndonje lidhje mes vlerave te perafruara dhe mbetjeve te standartizuara.**


$$Residuals\ vs.\ Leverage\ Plot$$

**Grafiku Residuals vs. Leverage na lejon te shikojme nese ka vezhgime qe ndikojme ne modelin e regresit qe kemi ndertuar. E thene ndryshe, shikojme nese ka vezhgime qe po te mos merren ne konsiderate ndryshojne modelin tone.**


```{r}

y_i_perafruar <- fitted.values(model1)
View(y_i_perafruar)


y_i_parashikuar <- predict(model1, newdata = data, interval='confidence')
head(y_i_parashikuar, 500)

```

**Ky kod na sherben per te identifikuar vlerat e parashikuara. Do te na hapet nje dritare e re e cila ne nje tabele do te kete te afishuara te gjitha vlerat e parashikuara.**

**Le te ndertojme nje grafik per vlerat tona te parashikuara:**

```{r}
plot(y_i_parashikuar)
```

**Nisur nga grafiku i ndertuar me siper, shperndarja e vlerave ne ate grafik ngjason me nje shperndarje logaritmike. Mund te themi se me rritjen e vlerave ne boshtin 'fit' nuk kemi nje rritje lineare te vlerave ne boshtin 'lwr'. Pra vlerat y nuk rriten ne menyre te drejteperdrejte me ato ne boshtin horizontal.**


#### $$Paired\ Plots$$

**Libraria $GGally$ na ofron nje opsion te ngjashem me $ggplot$: ate te quajtur $ggpairs$. Nga fjala pairs menjehere nenkuptojme cifte, pra cifte ose grupime grafikesh.**

**Me poshte kemi ndertuar nje paired plot per 9 variabla te datasetit tone.**
```{r}
library(GGally)
ggpairs(data[, c(1, 2, 3, 4, 5, 6, 7, 8, 9)], ggplot2::aes(color="red"))
```

**Ne grafik verejme pjeset perberese te tij. Ai perbehet nga grafike densiteti, box plote, histograma, dhe gjithashtu koeficiente korrelacioni te cilet na tregojne varesine midis ndryshoreve cilesore.**
**Pra me ane te ketij grafiku ne marrim ne nje fare menyre nje permbledhje te gjithe vizualizimit te kryer.**

**Cfare tregojne vlerat ne perqindje?**

**$plot: [2, 1] [===========>---------------]$ 12% tregon qe ne nje moment te kohes (gjate ekzekutimit te kodit) eshte duke u krijuar grafiku i pozicionuar ne (2,1) ne matrice dhe perben 12% te saj.**

**$stat$`_`$bin()$ $using$ $bins = 30$ do te thote se funksioni $stat$`_`$bin$ po perdor 30 pika per histogramet dhe tenton te zgjedhi nje vlere sa me te mire $binwidth$ per te permiresuar paraqitjen e tyre.**

**Ne menyre te ngjashme arsyetojme per cdo element tjeter te afishuar.**



### **`r colorize("Perfundime dhe Referenca", "blue")`**

#### $$Perfundime$$

**Ashtu sic e kemi cituar ne hyrje te projektit, $Student$ $Spending$ $Dataset$ ishte nje zgjedhje e jona per te studiuar dhe analizuar nje fenomen (nese do te quhet i tille) i cili na karakterizon te gjitheve ne si studente ne jeten tone te perditshme studentore. Pra per te analizuar shpenzimet e nje grupi studentesh me ane te metodave pergjithesisht te njohura statistikore, ku ne ndihme na vjen gjuha R dhe mjedisi i saj i zhvillimit $RStudio$.**

**Duke qene projekti i pare i mirefillte per ne, gjate gjithe kohes jemi perpjekur qe te tregohemi te sakte dhe te qarte ne strukturimin, analizimin dhe interpretimin e te dhenave tona. Jemi perpjekur tu kushtojme rendesi dhe vemendje te gjitha elementeve statistikore, madhesive te njohura, koncepteve.**

**Mbyllja e ketij projekti sigurisht qe do te perfshije ato cka ne kishim si objektiv: nje permbledhje te strukturuar te gjithe rezultateve te nxjerra nga cdo llogaritje statistikore e kryer mbi dataset.**

``
``
``
``

#### *Ne perfundim te analizimit te datasetit $Student$ $Spending$ arritem ne keto rezultate te rendesishme:*

**Mosha mesatare e studenteve te zgjedhur eshte 21 vjec, ndersa gjinia dominuese eshte ajo mashkullore.**

**Te ardhurat mujore mesatare te nje studenti rezultojne $1020.65.**

**Nga rezultatet e nxjerra arritem ne perfundimin se studentet shpenzonin me shume per shkollim, ndjekur nga strehimi dhe ushqimi.**

**Sipas gjinise me shume shpenzime benin meshkujt ne kategorite shkollim ,strehim , ushqim dhe  teknologji ,ndersa vajzat shpenzonin me shume ne kategorite e tjera si: transport, mjete shkollore, argetim, kujdes personal, mireqenie shendetesore dhe te ndryshme.**

**Sipas vitit te studimit per shkollim  me teper shpenzonin studentet $Junior$ ndjekur nga  $Sophomore$, $Freshman$ dhe me pak $Senior$.**

**Per strehim me shume shpenzonin $Senior$ dhe me pak $Sophomore$.**

**Per ushqim dhe kujdes personal me shume shpenzojne $Seniors$, ndersa me pak $Junior$.**

**Per transport, mjete shkollore, argetim, teknologji me shume shpenzojne $Freshman$, ndersa me pak $Junior$.**

**Sipas deges se diplomuar me shume per shkollim shpenzojne studentet e psikologjise dhe me pak ata te inxhiniersie.**

**Per strehim me shume shpenzojne ata te shkencave kompjuterike dhe me pak te ekonomikut.**

**Per ushqim me shume shpenzojne studentet e ekonomikut, ndersa me pak ata per shkenca kompjuterike.**

**Per transport me shume shpenzojne studentet e psikologjise, ndersa me pak ata te inxhinierise.**

**Per mjete shkollore, argetim, teknologji, mireqenie shendetesore shpenzojne me shume studentet e biologjise.**

**Per varesine midis ndyshoreve te datasetit nga matrica e korrelacionit dhe testeve Hi-katror dolem ne perfundim qe ndryshoret jane te pavarura me njera-tjetren.**

**Nga kjo pavaresi edhe modelet e testeve parashikuese rezultuan me nje marzh shpjegimi shume te ulet.**

#### $$Referenca$$

**Ne analizen e te dhenave gjate punes se pavarur shpesh jemi ndeshur ne situata per te cilat kishim nevoje per nje shpjegim dhe orientim. Per kete arsye i jemi referuar tekstit te statistikes, por edhe faqeve si $google.com$, platformave si $wikipedia.com$, $geekforgeeks.com$, $youtube.com$ etj.. Me poshte listohen disa nga sitet ne te cilat perfituam nje sasi informacioni:**

**Credits to: $Hyrje$ $ne$ $Statistiken$ $e$ $Zbatuar$ $3$ nga $Prof.$ $Dr.$ $Llukan$ $Puka$;**

**Link to dataset:** https://www.kaggle.com/datasets/sumanthnimmagadda/student-spending-dataset/data

https://posit.co/download/rstudio-desktop/

https://www.khanacademy.org/math/statistics-probability/summarizing-quantitative-data/mean-median-basics/a/mean-median-and-mode-review

https://search.yahoo.com/search?fr2=p%3ads%2cv%3aomn%2cm%3asa%2cbrws%3achrome%2cpos%3a4&fr=mcafee&type=E210US91215G0&p=degrees+of+freedom+formula

https://search.yahoo.com/search;_ylt=AwrFaE1RmD9mZQQA8lVXNyoA;_ylc=X1MDMjc2NjY3OQRfcgMyBGZyA21jYWZlZQRmcjIDc2ItdG9wBGdwcmlkA0FaSlRvNUJVVDNxTXZuVks0VHlHaUEEbl9yc2x0AzAEbl9zdWdnAzEEb3JpZ2luA3NlYXJjaC55YWhvby5jb20EcG9zAzAEcHFzdHIDBHBxc3RybAMwBHFzdHJsAzI1BHF1ZXJ5A3RhYmxlJTIwb2YlMjBjb250aW5nZW5jeSUyMGluJTIwUgR0X3N0bXADMTcxNTQ0Mzc5OQ--?p=table+of+contingency+in+R&fr=mcafee&type=E210US91215G0&fr2=sb-top&iscqry=

https://search.yahoo.com/search?fr=mcafee&type=E210US91215G0&p=imi+fshn

**Chi-squared Test:** https://search.yahoo.com/search?fr2=p%3ads%2cv%3aomn%2cm%3asa%2cbrws%3achrome%2cpos%3a1&fr=mcafee&type=E210US91215G0&p=chi-square+test

http://www.sthda.com/english/articles/32-r-graphics-essentials/133-plot-one-variable-frequency-graph-density-distribution-and-more/

**Mosaic Plot:** https://search.yahoo.com/search?fr=mcafee&type=E210US91215G0&p=mosaic+plot

**Word Cloud in R:** https://www.marsja.se/how-to-create-a-word-cloud-in-r/#google_vignette

**Visualization using $ggplot2$:** https://www.dataquest.io/blog/data-visualization-in-r-with-ggplot2-a-beginner-tutorial/

**Residuals vs Leverage Plot:** https://images.search.yahoo.com/search/images;_ylt=AwrEq4z_UlRmRAQAoeJXNyoA;_ylu=Y29sbwNiZjEEcG9zAzEEdnRpZAMEc2VjA3BpdnM-?p=residuals+vs+leverage+plot+in+r&fr2=piv-web&type=E210US91215G0&fr=mcafee

**How to interpret a Scale-Location Plot:** https://www.statology.org/scale-location-plot/

**Predicted y values:** https://search.yahoo.com/search?fr=mcafee&type=E210US91215G0&p=predicted+value+of+y+in+plots

**R installation & more:** https://youtu.be/FIrsOBy5k58?si=fDkTBu06nhf8UA0A

https://youtu.be/2_tW7e4e_dM?si=-sRLFJpb7hPEGoTf

https://youtu.be/YrEe2TLr3MI?si=fLCYGjaiW6VH6ZRg

https://youtu.be/48b4BzxHHH8?si=LOR1OgqnS-fAiAiL

https://youtu.be/Uo1C7Iligw0?si=5Eg3vqXA1aisYarv

https://youtu.be/ePD96i0YHII?si=zHZdVeTEwm6rMjzw

https://youtu.be/svgEpRzhG7M?si=n1IEDUfyOIgy9DT3

**Link to esquisser: esquisse::esquisser(data, viewer = "browser")**

#### $$Word\ Cloud$$

```{r}
library(wordcloud)
library(wordcloud2)
library(RColorBrewer)

fjalet <- c("Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup", "Adisa", "Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa",
"Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data", "Science","Science","Science","Science","Science","Science","Science","Science","Engineer","Engineer","Engineer","Engineer","Engineer","Engineer","Engineer", "FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI", "2024","2024","2024","2024","2024","2024","2024","2024","2024","2024","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup","Jakup", "Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Adisa","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data","Data", "Science","Science","Science","Science","Science","Science","Science","Science","Engineer","Engineer","Engineer","Engineer","Engineer","Engineer","Engineer", "FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","FSHN","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI","IMI", "2024","2024","2024","2024","2024","2024","2024","2024","2024","2024")

frekuencat <- rep(frekuencat, length.out = length(fjalet))
data <- data.frame(word = fjalet, freq = frekuencat)

wordcloud2(data = data, size = 0.1, shape='random', color='random-dark')
```

#### $$"Do\ not\ trust\ any\ statistics\ you\ did\ not\ fake\ yourself.\ Facts\ are\ stubborn,\ but\ statistics\ are\ more\ pliable."\\ :)$$

