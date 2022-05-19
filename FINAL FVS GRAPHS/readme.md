![TMT1_FINAL](https://user-images.githubusercontent.com/49656044/169206204-002614df-34d2-4d55-b7c4-52518a2ddf09.png)
![TMT2_FINAL](https://user-images.githubusercontent.com/49656044/169206207-08641ccf-c106-4c56-a2d5-7ccdf7e48edb.png)
![TMT3_FINAL](https://user-images.githubusercontent.com/49656044/169207484-2b0ab2f9-31d0-49f9-a8e9-a87e7e37aad4.png)

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
#Import the data yet again
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

#READ IN DATA FILES
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




#TMT1
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
#TMT2
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

#TMT3
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

