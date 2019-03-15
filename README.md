################# Simple-linear-Regression  ###################
# Data set : calories_consumed
# Prediction : predict weight gained using calories consumed
library(lattice)
wg<-calories_consumed
colnames(wg)
#Dotplot & Boxplot
Calories.Consumed<-wg[,2]
dotplot(Calories.Consumed,main="Dotplot of Calories.Consumed")
Weight.gained..grams<-wg[,1]
Weight.gained..grams
dotplot(Weight.gained..grams,main="Dotplot of Weight.gained..grams",col="firebrick3")
boxplot(Calories.Consumed,main="Boxplot of Calories.Consumed",col="firebrick3")
boxplot(Weight.gained..grams,main="Boxplot of Weight.gained..grams",col="firebrick3")
#scatterplot
plot(Weight.gained..grams,Calories.Consumed,main="Scatterplot",col.main="chartreuse3",col="firebrick3",col.lab="firebrick3",xlab ="Calories.Consumed",ylab ="Weight.gained..grams",pch=18)
#Building a regression model
model_wg<-lm(Weight.gained..grams~Calories.Consumed,data =wg)
#summary
summary(model_wg)
#prediction intervals for new variables
predict(model_wg,data.frame(Calories.Consumed=c(1600)))
#Residuals
model_wg$residuals
pred<-predict(model_wg)
data<-data.frame("pred"=pred,"error"=model_wg$residuals)
write.csv(data,"data1.csv")
