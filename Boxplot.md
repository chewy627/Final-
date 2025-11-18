setwd("/cloud/project")
sleep <- read.csv("Sleep_health_and_lifestyle_dataset.csv", header=TRUE)
names(sleep)   
"Sleep.Duration" 
"Occupation" 
"Gender" 

sleep$Gender <- as.factor(sleep$Gender)
sleep$Occupation <- as.factor(sleep$Occupation)


#Install the ggplot2 package
#install.packages("ggplot2")


#Load the package and all of its dependencies
library(ggplot2)

##############
## BOX PLOT ##
##############




boxplot_Gender <- ggplot(sleep, aes(Gender  , Sleep.Duration))
boxplot_Gender + geom_boxplot() 


boxplot_occupation <- ggplot(sleep, aes(Occupation  , Sleep.Duration))
boxplot_occupation + geom_boxplot() 
