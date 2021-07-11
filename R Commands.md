1.Read the csv data file.

pokemon_data=read.csv(file=file.choose(),header = TRUE)	


2.Display head of data

head(pokemon_data)


3.Display first n rows specified.

head(pokemon_data,n=10)


4.Display tail of data.

tail(pokemon_data)


5.Display n rows specified from bottom

tail(pokemon_data,n=10)


6.Determining Type of data
class(pokemon_data)


7.Table command
table(pokemon_data$Attack)
table(pokemon_data$HP)

8.Determine the structure of data

str(pokemon_data)


9.Summarising the data
 summary(pokemon_data)
 
 
10.Displaying Dimension of the data
   
dim(pokemon_data)


11.Displaying length of attack column

length(pokemon_data$Attack)

12.Displaying column names of data

colnames(pokemon_data)


13.Displaying structure of some columns in the data

class(pokemon_data$Name)typeof(pokemon_data$Name)


14.Displaying type of some data structure in the data

typeof(pokemon_data$Total)


15.List of variables present in pokemon data
ls(pokemon_data)

16.Some pattern matching operations on variable of pokemon_data

ls(pokemon_data,pattern="^Sp")
ls(pokemon_data,pattern="^[AD]")
ls(pokemon_data,pattern="t.l")


ls(pokemon_data,pattern="ce$")

17.Display 1st row and all columns of data frame
pokemon_data[1,]
							
							
18.Display all rows and 1st column of data frame

pokemon_data[,1]
  

19.Display data in 2nd row and 3rd column of the data frame


pokemon_data[2,3]


20.Display 1st and 2nd row and all columns
pokemon_data[1:2,]


21.Display all rows and first 3 columns

pokemon_data[,3]

22.Selecting data where pokemon name is Venusar with subset operator

temp_data=subset(pokemon_data,Name=="Venusaur")
temp_data
								
								
23.Renaming a column in data frame
temp_pokemon=pokemon_datanames(temp_pokemon)[names(temp_pokemon)=="Total"]<-"Total_Number")
temp_pokemon[1,]


24.Adding a new column to dataframe
temp_pokemon[["New_col"]]<-rep(c(1,2,3,4,5),209)
temp_pokemon[1:10,]

25.Display Sum of Attack column
sum(pokemon_data[4])

26.Display the maximum value of the Attack column

max(pokemon_data[4])

27.Display the minimum value of the Attack column

min(pokemon_data[4])

28.Attaching Pokemon data

attach(pokemon_data)


29.Now we can use variables inside pokemon data
min(Attack)

tail(Speed)

30.Sorting Attack variable in ascending order

sort(Attack)


31.Sorting Attack variable in descending order
sort(Attack,decreasing = TRUE)

32.Detaching Pokemon data
detach(pokemon_data)


33.Using with operator to use variables inside data
with(pokemon_data,Attack)
 
34.Finding median of data
median(pokemon_data$Attack)

35.Finding mean of data
mean(pokemon_data$Attack)

36.Finding standard deviation of data
sd(pokemon_data$Attack)

37.Finding variance of data
var(pokemon_data$Attack)

38.Order the Attack column in ascending order
order(pokemon_data[4])


39.Order the attack column in descending order
order(pokemon_data$Attack,decreasing =TRUE)

40.Rank of Speed column
rank(pokemon_data$Speed)

41.Rank of speed column with average as tie breaker
rank(pokemon_data$Speed,ties.method = "average")
DPLYR operations


42.Usage of mutate function
library(dplyr)
Attaching package: 'dplyr'
head(pokemon_data %>%mutate(mutated_Attack=Attack-mean(Attack)))


43.Adding extra column with user created vector
vec = rep(c(1,2,3,4,5),209)
head(pokemon_data %>% mutate(newcol = vec))


44.Group by function
new_pok=pokemon_data %>% group_by(Name)
head(new_pok)

45.Summarise function
head(pokemon_data %>% group_by(Attack,HP) %>% summarise(weight_Defence=mean(Defence)))
`summarise()` has grouped output by 'Attack'. You can override using the `.groups` argument.


46.Rename operation
copy_pokemon=pokemon_data
pd_mod <- copy_pokemon %>% rename(renamed_Attack = Attack)
head(pd_mod)


47.Selecting specific columns
copy_pokemon=pokemon_data
copy_pokemon %>% select(Name,HP,Attack,Speed,Total)


48.Reordering of columns using select function
copy_pokemon=pokemon_data
copy_pokemon %>% select(HP,Attack,Name)


49.Filter command
copy_pokemon=pokemon_data
copy_pokemon %>%  filter(Total >= 500 & Total <=505)

Histogram
ggplot(pokemon_data, aes(x = Attack)) +geom_histogram()

50.Histogram of Attack column and its density
ggplot(pokemon_data,aes(x=Attack))+
geom_histogram(fill="cornsilk",color="blue",
size=0.2)+geom_density(color="black")

51.Line graph of Attack column and its density
ggplot(pokemon_data,aes(x=Attack))+
geom_density(fill="blue",alpha=.4)

 52.Line graph of Attack column taking two alpha values
ggplot(pokemon_data,aes(x=Attack))+
geom_line(stat="density")+
geom_line(stat="density",adjust=0.25,
color="red")+geom_density(fill='blue',alpha=0.2)

53.Dot Plot
library(ggplot2)
ggplot(pokemon_data,aes(x=Attack,y=HP))+geom_dotplot(binaxis="y",stackdir = "center", binwidth = 4,fill="green")


54.Box Plot
ggplot(pokemon_data, aes(x=Attack,y=HP))+geom_boxplot(width=0.1,fill='black')+stat_summary(func='median',fill='white',shape=21)
54.Density plot for Attack and HP
ggplot(pokemon_data,aes(x=Attack,y=HP))+geom_density2d(aes(colour=..level..))


55.Violin Plot
Attack and HP
ggplot(pokemon_data,aes(x=Attack,y=HP))+geom_violin()



