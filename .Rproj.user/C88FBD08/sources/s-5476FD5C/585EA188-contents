# declaration des Library
library(ggplot2)
library(tidyverse)
library(dplyr)
library(maps)
library(usmap)
library(maps)
library(mapdata)
library(viridis)

#Covid data
UStable<- read.csv("USvax.csv", header=TRUE, sep=",")
View(UStable)
us_states <- map_data("state")
head (us_states)
View(us_states)

#Merge data
UStable$states <- tolower(UStable$states)
data <- merge(us_states, UStable,
              by.x="region",
              by.y="states")
View(data)
#Plot

mapUS <- ggplot(data, aes(x=long, y=lat,
                 group=group,
                 fill= perc_covidcases))+
  geom_polygon(colour= "black", size=0.7)+
  coord_map("polyconic")+ labs(title="US Map Ratio cases and vaccines")+
  geom_point(data=data,aes(x=long, y=lat, size=perc_atleastonedose),
             colour="purple", 
             fill="Royal blue",pch=0, alpha=I(1/20))+
  scale_color_brewer(palette = "Dark2")+
  scale_fill_viridis(option="plasma", trans="sqrt")
  theme_dark() +
  theme(
    legend.position = "right",
    panel.background = element_rect(fill = "#2D2D2D2D"),
    legend.key = element_rect(fill = "#95DBE5FF")
  )
mapUS
