# R-cheatsheet


c(10:40)
10 11 12 .... 39 40

c menyimpan variabel vektor
c(1, 2, 3) #[1] 1 2 3
bisa menyimpan string

nama_variabel <- "nili variabel" #deklarasi variable

data.frame(list,list)

## GGPLOT2

library("ggplot2")
#menggunakannya
gambar <- ggplot(info_mahasiswa, aes(x=fakultas, y=jumlah_mahasiswa, fill=fakultas))
gambar <- gambar + geom_bar(width=1, stat="identity")

#Menambahkan judul grafik
gambar <- gambar + ggtitle("Jumlah Mahasiswa per Fakultas")

#Menambahkan caption pada sumbu x
gambar <- gambar + xlab("Nama Fakultas")

#Menambahkan caption pada sumbu y
gambar <- gambar + ylab("Jumlah Mahasiswa")

library(openxlsx)

#Membaca file mahasiswa.xlsx
mahasiswa <- read.xlsx("https://storage.googleapis.com/dqlab-dataset/mahasiswa.xlsx",sheet = "Sheet 1")

#Menghitung Jumlah Data by Fakultas, 3 bar chart
summarybyfakultas <- aggregate(x=mahasiswa$JUMLAH, by=list(Kategori=mahasiswa$Fakultas, Tahun=mahasiswa$ANGKATAN), FUN=sum)
summarybyfakultas <- setNames(summarybyfakultas, c("fakultas","tahun", "jumlah_mahasiswa"))
summarybyfakultas

summarybyfakultas$tahun = as.factor(summarybyfakultas$tahun)

ggplot(summarybyfakultas, aes(x=fakultas, y=jumlah_mahasiswa)) + 
  geom_bar(stat = "identity", aes(fill = tahun), width=0.8, position = position_dodge(width=0.8)) + 
  theme_classic() 
  
  
 summarybyfakultas[summarybyfakultas$fakultas %in%c("ICT", "Ilmu Komunikasi"),] #filter data
  
  
