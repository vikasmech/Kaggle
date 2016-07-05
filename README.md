# Kaggle
# path of the train.csv 
path = "C:\\Users\\vkkumar\\Documents\\Git\\Kaggle\\FB\\train.csv"

setwd(path)

#reading in the data
library(data.table) 


train <- fread("train.csv", integer64 = "character", showProgress = FALSE)

train1 = train[1:1000,]

for (i in 1:100)
{
    for (j in 1:100)
  {
    lower_limit_y = (i-1)*0.1;
    upper_limit_y = i*0.1;
    lower_limit_x = (j-1)*0.1;
    upper_limit_x = j*0.1;
    tmp_data = train[(lower_limit_y<y & y<upper_limit_y & lower_limit_x<x & x<upper_limit_x),]

    # writing the cell data in excel
    write.csv(tmp_data , file = paste("train_x", j,"y",i, sep="",".csv"),row.names=FALSE)
  }
}
