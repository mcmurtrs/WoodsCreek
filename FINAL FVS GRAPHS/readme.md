![TMT1_FINAL](https://user-images.githubusercontent.com/49656044/169945025-c187e107-4876-4977-9b10-120b83fa30b0.png)
## Figure 1: Model comparison of Woods Creek stands plots that were not thinned.

![TMT3_FINAL](https://user-images.githubusercontent.com/49656044/169945046-56a5e9a0-e44a-4b08-999e-91955c306a13.png)

## Figure 2: Model comparison of Woods Creek plots with light thinning.

![TMT2_FINAL](https://user-images.githubusercontent.com/49656044/169945032-6cbb39aa-f8f4-47f9-bb72-b75abcd53e0e.png)

## Figure 3: Model comparison of Woods Creek plots that were thinned.

# R Code Used For Graphing

---
title: "FVS_FINAL"
author: "Shawn McMurtrey"
date: "5/18/2022"
output: html_document
---

---
title: "FVS"
author: "Shawn"
date: "Winter 2021"
output:
  word_document: default
  pdf_document: default
---
## Import the data yet again
```{r include=FALSE}
# Load libraries we need for the assignment
install.packages("fvsLoad")
library(ggplot2)
install.packages(tidyverse)
install.packages(tidyr)
library(tidyverse)
library(dplyr)
library(tidyr)
library(readxl)

```

## READ IN DATA FILES
```{r}
#Total Modelled Data
fvs_data <- read_excel("C:/Users/shawn/Desktop/LAST_TIME/R_final/FVS_data.xlsx")
fvs_data_TMT2_3 <- read_excel("C:/Users/shawn/Desktop/LAST_TIME/R_final/FVS_data_TMT2_3.xlsx")
fvs_data_combined <- read_excel("C:/Users/shawn/Desktop/LAST_TIME/R_final/FVS_data_combined.xlsx")
fvs_data_combined_TPA <- read_excel("C:/Users/shawn/Desktop/LAST_TIME/R_final/FVS_data_combined_TPA.xlsx")
fvs_data_combined_TMT1 <- read_excel("C:/Users/shawn/Desktop/LAST_TIME/R_final/FVS_data_combined_TMT1_FINAL.xlsx")
fvs_data_combined_TMT2 <- read_excel("C:/Users/shawn/Desktop/LAST_TIME/R_final/FVS_data_combined_TMT2_FINAL.xlsx")
fvs_data_combined_TMT3 <- read_excel("C:/Users/shawn/Desktop/LAST_TIME/R_final/FVS_data_combined_TMT3_FINAL.xlsx")
#Mean with Error Bars
#fvs_default_TMT1_error <- read_excel("C:/Users/shawn/Desktop/new/TMT1_defualt_FVS_error.xlsx")
```




## TMT1
```{r}

library(ggplot2)
library(cowplot)

#install.packages(scales)
#library(scales)
#library(viridis)
AVERAGE_BA <- as.numeric(fvs_data_combined$AVERAGE_BA)
#as.numeric(fvs_data$FULL_Year)
#as.numeric(fvs_data$Full_MgmtID)
#(aes(fill = dose), show.legend = FALSE)
 gg1 <- ggplot(data = fvs_data_combined_TMT1, aes(x = FULL_Year, y = TMT1_BA, color = GRAPH, group = GRAPH), position = position_dodge(0.3)) +  
  geom_point(position = position_dodge(0.3)) +    
   geom_line(position = position_dodge(0.3)) + ylim(30, 95) +
    geom_errorbar(data =  fvs_data_combined_TMT1, aes(ymin=TMT1_BA - TMT1_SE,  ymax=TMT1_BA + TMT1_SE), width=.2, position=position_dodge(0.2)) + 
   scale_color_viridis(discrete=TRUE) + theme_classic()  + labs(x = "Year") +  
ylab(expression(paste(BA~m^2/ha)))  +
   scale_color_brewer(palette = "Dark2", name = "") 

 ggsave("TMT1_FINAL.png")
 

```
## TMT2
```{r}
gg2 <- ggplot(data = fvs_data_combined_TMT2, aes(x = FULL_Year, y = TMT2_BA, color = GRAPH, group = GRAPH), position = position_dodge(0.3)) +  
  geom_point(position = position_dodge(0.3)) +    
   geom_line(position = position_dodge(0.3)) + ylim(30, 95) +
    geom_errorbar(data =  fvs_data_combined_TMT2, aes(ymin=TMT2_BA - TMT2_SE,  ymax=TMT2_BA + TMT2_SE), width=.2, position=position_dodge(0.2)) + 
   scale_color_viridis(discrete=TRUE) + theme_classic()  + labs(x = "Year") +  
ylab(expression(paste(BA~m^2/ha))) +
scale_color_viridis(discrete=TRUE) + theme_classic()  + labs(x = "Year") +  
ylab(expression(paste(BA~m^2/ha)))  +
   scale_color_brewer(palette = "Dark2", name = "") 

ggsave("TMT2_FINAL.png")

```

## TMT3
```{r}

 
gg3 <- ggplot(data = fvs_data_combined_TMT3, aes(x = FULL_Year, y = TMT3_BA, color = GRAPH, group = GRAPH), position = position_dodge(0.3)) + 
  geom_point(position = position_dodge(0.3)) +    
   geom_line(position = position_dodge(0.3)) + ylim(30, 95) +
    geom_errorbar(data =  fvs_data_combined_TMT3, aes(ymin=TMT3_BA - TMT3_SE,  ymax=TMT3_BA + TMT3_SE), width=.2, position=position_dodge(0.2)) + 
   scale_color_viridis(discrete=TRUE) + theme_classic()  + labs(x = "Year") +  
ylab(expression(paste(BA~m^2/ha))) +
scale_color_viridis(discrete=TRUE) + theme_classic()  + labs(x = "Year") +  
ylab(expression(paste(BA~m^2/ha)))  +
   scale_color_brewer(palette = "Dark2", name = "") 

ggsave("TMT3_FINAL.png")
```

