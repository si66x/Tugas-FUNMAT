# Tugas-FUNMAT
library(datasets)  # Load base packages manually
install.packages('plyr')
library(plyr)

if (!require("pacman")) install.packages("pacman")

pacman::p_load(pacman, rio,dplyr,tidyr,stringr,
               lubridate,httr,ggvis,ggplot2, shiny, rmarkdown) 


# import excel FMA
rio_xlsx <- import("c:\\Users\\User\\Desktop\\FMA_Milano_Ery_Kevin.xlsx") #untuk parameter di fungsi import, silahkan isi dengan lokasi file masing2
head(rio_xlsx)

#mencari frekuensi k5####
count(rio_xlsx,'k5') #output berupa tabel dari kolom K5

#mencari frekuensi kumulatif###

#assign data dari tiap kelas ke variabel
frek1<-count(rio_xlsx, 'k1') 
frek2<-count(rio_xlsx, 'k2') 
frek3<-count(rio_xlsx, 'k3') 
frek4<-count(rio_xlsx, 'k4') 
frek5<-count(rio_xlsx, 'k5') 
frek6<-count(rio_xlsx, 'k6') 
frek7<-count(rio_xlsx, 'k7') 
frek8<-count(rio_xlsx, 'k8') 
frek9<-count(rio_xlsx, 'k9') 
frek10<-count(rio_xlsx, 'k10')

#assign jumlah dari frekuensi tiap variabel ke variabel
rfrek1<-sum(frek1$freq)
rfrek2<-sum(frek2$freq)
rfrek3<-sum(frek3$freq)
rfrek4<-sum(frek4$freq)
rfrek5<-sum(frek5$freq)
rfrek6<-sum(frek6$freq)
rfrek7<-sum(frek7$freq)
rfrek8<-sum(frek8$freq)
rfrek9<-sum(frek9$freq)
rfrek10<-sum(frek10$freq)

#hasil total frekuensi tiap kelas####
rfrek1 + rfrek2 + rfrek3 + rfrek4 + rfrek5 + rfrek6 + rfrek7 +rfrek8 + rfrek9 + rfrek10

# import excel FMB
rio2_xlsx <- import("c:\\Users\\User\\Desktop\\FMB_Milano_Ery_Kevin.xlsx")  #untuk parameter di fungsi import, silahkan isi dengan lokasi file masing2
head(rio2_xlsx)

#mencari tau nilai median, kuartil, mean######
summary(rio2_xlsx$Data)
sd(rio2_xlsx$Data) #nilai standar deviasi

?hist #untuk membuka documentasi mengenai histogram

#membuat histogram dari FMB
hist(rio2_xlsx$Data,
     main = "Histogram penjualan",
     xlab = "promosi",
     ylab = "penjualan",
     breaks = 20,
     col = "red",
     )

?plot
#membuat scatterplot dari FMB
plot(rio2_xlsx$Data,
     main = "scatter-plot penjualan",
     xlab = "promosi",
     ylab = "penjualan",
     col = "blue"
)
#membuat regresi
scatter.smooth(x = rio2_xlsx$Hari, y = rio2_xlsx$Data,
               main = "Data~Hari"
               )

#membuat korelasi
cor(x = rio2_xlsx$Hari, y = rio2_xlsx$Data)

#bersihkan konsol
cat("\014")



