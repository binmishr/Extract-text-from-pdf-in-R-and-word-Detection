# Extract-text-from-pdf-in-R-and-word-Detection

Extract text from pdf in R, first we need to install pdftools package from cran.

Let’s install the pdftools package from cran.

install.packages("pdftools")

Load the package

library("pdftools")

The pdf file needs to save in local directory or get it from online. Here we are extracting one sample document from online.

Store the link in pdf.file variable.

pdf.file <- "https://file-examples-com.github.io/uploads/2017/10/file-sample_150kB.pdf"

Set the working directory

setwd("D:/RStudio/PDFEXTRACT/")

Let’s download the demo pdf file into the local directory

download.file(pdf.file, destfile = "sample.pdf", mode = "wb")

pdf_text() function, which returns a character vector of length equal to the number of pages in the file.
Extract text from pdf in R

Now we can extract the text from all pages.

pdf.text <- pdftools::pdf_text("sample.pdf")

Suppose if you want to display second page information then use below code,

cat(pdf.text[[2]]) 

Displayed only a few text here

In non mauris justo. Duis vehicula mi vel mi pretium, a viverra erat efficitur. Cras aliquam
est ac eros varius, id iaculis dui auctor. Duis pretium neque ligula, et pulvinar mi placerat
et. Nulla nec nunc sit amet nunc posuere vestibulum. Ut id neque eget tortor mattis
tristique. Donec ante est, blandit sit amet tristique vel, lacinia pulvinar arcu. Pellentesque
scelerisque fermentum erat, id posuere justo pulvinar ut. Cras id eros sed enim aliquam
lobortis. Sed lobortis nisl ut eros efficitur tincidunt. Cras justo mi, porttitor quis mattis vel, ultricies ut purus. Ut facilisis et lacus eu cursus.

Now if you want to extract a particular word from these pages, unlist the data and convert it into lower case letters

How to do t test statistical analysis in R, Assumptions and Inference

pdf.text<-unlist(pdf.text)
pdf.text<-tolower(pdf.text)

Suppose if we want to extract the page number details for the word contains “Suspendisse“

library(stringr)
res<-data.frame(str_detect(pdf.text,"suspendisse"))
colnames(res)<-"Result"
res<-subset(res,res$Result==TRUE)
row.names(res)

Output

1] "2" "3"

The word “suspendisse” contains on pages number 2 and 3.
Conclusion

This article described text data extraction from pdf files and particular word detection from pdf data in R.
