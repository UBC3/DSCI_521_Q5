#    Data exploration, regression, GLM & GAM course
#    Highland Statistics Ltd.
#    www.highstat.com
   
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.


Addition from Birinder Singh:

You are doing good in the MDS program, trust me. You can make it :D

########################################################################
#Housekeeping
#Load packages from R and support functions that we wrote

library(lattice)  #For fancy multipanel graphs

#Copy the file HighstatLibV10.R into your working directory
#Ensure it is a .R file and not a .R.txt file!!!!!! 

source("HighstatLibV10.R")   #<------
#Now we can make fancy graphs



########################################################################
#Inspect the file
#What do we have?
names(Birds)

# "Site"    "ABUND"   "AREA"    "DIST"
# "LDIST"   "YR.ISOL" "GRAZE"
# "ALT"

str(Birds)  #Make sure that ABUND and AREA are num  and not factors!!!!!!
            #If they are factors then change the dec argument!
#'data.frame':   56 obs. of  8 variables:
# $ Site   : int  1 2 3 4 5 6 7 8 9 10 ...
# $ ABUND  : num  5.3 2 1.5 17.1 13.8 14.1 3.8 2.2 3.3 3 ...
# $ AREA   : num  0.1 0.5 0.5 1 1 1 1 1 1 1 ...
# $ DIST   : int  39 234 104 66 246 234 467 284 156 311 ...
# $ LDIST  : int  39 234 311 66 246 285 467 1829 156 571 ...
# $ YR.ISOL: int  1968 1920 1900 1966 1918 1965 1955 1920 1965 1900 ...
# $ GRAZE  : int  2 5 5 3 5 3 5 5 4 5 ...
# $ ALT    : int  160 60 140 160 140 130 90 60 130 130 ...
########################################################################




########################################################################
#Data exploration
# A Outliers in Y / Outliers in X
# B Collinearity X


###################################################
#First some elementary R commands.
# How do you acces variables in an object like Birds?
Birds               #All data
head(Birds)         #First 6 rows
head(Birds, 10)     #First 10 rows
Birds$ABUND         #ABUND variable
Birds[  ,1]         #First column
Birds[,2]           #Second coloumn
Birds[ , "ABUND"]   #ABUND variable 
Birds[1,"ABUND"]    #First row of ABUND variable
Birds[1:10,"ABUND"] #First 10 rows of ABUND
c("ABUND", "AREA")  #Two characters concatenated
Birds[ , c("ABUND", "AREA")] #ABUND and AREA variables

MyVar <- c("ABUND",  "AREA")  #Same as last two steps
Birds[, MyVar]

# Now you are an R expert!
##################################################





##############################################
#A Outliers
#Copy from here...
par(mfrow = c(1, 2))    #Two graphs next to each other
#abundance
boxplot(Birds$ABUND, 
        main = "Abundance")
dotchart(Birds$ABUND, 
	     xlab = "Range of data", 
	     ylab = "Order of the data")
#...to here and paste into R
#Distance
boxplot(Birds$DIST, 
        main = "Distance")
dotchart(Birds$DIST, 
         xlab = "Range of data", 
         ylab = "Order of the data")   #K-there is an outlier
#Ldist
boxplot(Birds$LDIST, 
        main = "LDistance")
dotchart(Birds$LDIST, 
         xlab = "Range of data", 
         ylab = "Order of the data")
#Yr.Isol
boxplot(Birds$YR.ISOL, 
        main = "Year of isolation")
dotchart(Birds$YR.ISOL, 
         xlab = "Range of data", 
         ylab = "Order of the data")
#altitute
boxplot(Birds$ALT, 
        main = "Altitute")
dotchart(Birds$ALT, 
         xlab = "Range of data", 
         ylab = "Order of the data")
#grazing level
boxplot(Birds$GRAZE, 
        main = "Grazing level")
dotchart(Birds$GRAZE, 
         xlab = "Range of data", 
         ylab = "Order of the data")


