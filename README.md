R syntax.

thailand open data https://www.data.go.th/

Attribute type
- String
- Number
- NA (null)
- vector
- Boolean 

```R
#Oparator
# + - / * %
1+1 # 2

'string' # string
"string" # string
3<4 # TRUE
2+2 == 5 # FALSE
T == TRUE # TRUE
F == FALSE # TRUE

#Assign Value to attribute
x <- 42 # x = 42
x # 42
x/2 # 21
```

Function
```R
print( attribute_name ) # print attribute value
sum( [...] ) # sum x values
sqrt( x ) # square root of x
rep( {string,number} , times = x ) # repeat {string,number} x times 
mean ( [...] ) # mean of x values
median ( [...] ) # median of x values
sd ( [...] ) # standard deviation

help( function_name ) # explain function 
example( function_name ) # example function
```

Trick remove NA from vector 
```R
a <- c(1,3,NA,7,9)
sum(a, na.rm = TRUE)
```

File system
```R
list.files() # list files system from current directory
source( file_name ) # print out content from file
# read data into data frames
read.csv( file_csv ) # read csv
read.table­("infantry­.txt", sep="­\t")  # read txt with separator \t
read.table("infantry.txt", sep="\t", header=TRUE) # keep header

```

Vectors
- like an array of other language
- can be numbers , strings , logical , or other 
- must be all the same type
- vector index start at 1 

```R
c(4,7,9) # [1] 4 7 9
c(1, TRUE, 'three') # "1" "TRUE" "three" convert all to string type 

sentence <- c('walk','the','plank') # assign vector to attribute
sentence[3] # "plank"
sentence[3] <- 'dog'
sentence[3] # "dog"
sentence[4] <- 'to' # assign value to array 

sentence # "walk" "the" "dog" "to"

sentence[c(1,3)] # "walk" "dog"
sentence[2:4] # "the" "dog" "to"

sentence[5:7] <- c('the', 'poop', 'deck')
sentence # "walk"­ "the" "d­og" "to"  "the" "­poop" "dec­k"

#-----------------------------------------
#Sequence Vectors

#step up
5:9 # 5 6 7 8 9
seq(5,9) # 5 6 7 8 9
seq(5, 9, 0.5) # 5.0 5.5 6.0 6.5 7.0 7.5 8.0 8.5 9.0

#step down
9:5 # 9 8 7 6 5
seq(9,5) # 9 8 7 6 5
seq(5, 9, -0.5) # 9.0 8.5 8.0 7.5 7.0 6.5 6.0 5.5 5.0

#-----------------------------------------
#Assign Vector column name
ranks <- 1:3
names(ranks) <- c("first", "second", "third")
ranks
# first second  third
#     1      2      3

ranks["first"]
# first 
#     1

ranks["third"] <- 4
ranks
# first second  third
#     1      2      4

#Vector Math
# - work with math function
# - be able to oparate with other vertoc

a <- c(1, 2, 3) # 1 2 3
a+1 # [1] 2 3 4
a # 1 2 3
a/2 # [1] 0.5 1.0 1.5

b <- c(4, 5, 6) # 4 5 6
a+b # [1] 5 7 9

a == c(1, 99, 3) #[1]  TRUE FALSE  TRUE
```

Plotting One Vector
```R
vesselsSunk <- c(4, 5, 1)
names(vesselsSunk) <- c("England", "France", "Norway")

barplot(vesselsSunk)
abline( h = { mean([...]) , ... } ) # draw horizontal line at the mean of values

limbs <- c(4, 3, 4, 3, 2, 4, 4, 4)
names(limbs) <- c('One-Eye', 'Peg-Leg', 'Smitty', 'Hook', 'Scooter', 'Dan', 'Mikey', 'Blackbeard')
abline(h = mean(limbs))
abline(h = mean(limbs), sd(limbs) )
```

Scatter Plots (2 vector)
- relationship of 2 vector
```R
x <- seq(1, 20, 0.1)
y <- sin(x)
plot(x, y)
```

Other Plotting libraries
```R
ggplot2 # http://www.cookbook-r.com/Graphs/
```

Matrices
- like a array 2 dimensional

```R
# matrix 
# - 3 rows
# - 4 columns
# - fields set to 0

matrix(0, 3, 4)

#     [,1] [,2] [,3] [,4]
#[1,]    0    0    0    0
#[2,]    0    0    0    0
#[3,]    0    0    0    0

# assign matrix s value
# use vector
a <- 1:12
matrix(a, 3, 4)
#     [,1] [,2] [,3] [,4]
#[1,]    1    4    7   10
#[2,]    2    5    8   11
#[3,]    3    6    9   12


plank <- 1:8
dim(plank) <- c(2, 4)
#     [,1] [,2] [,3] [,4]
#[1,]    1    3    5    7
#[2,]    2    4    6    8

plank[2, 3] # [1] 6
plank[2,] # [1] 2 4 6 8
plank[, 4] # [1] 7 8
plank[, 2:4]
#     [,1] [,2] [,3]
#[1,]    3    5    7
#[2,]    4    6    8
```

Matrix Plotting
example 
- elevation map of a sandy beach.
- everything is 1 meter above sea level.
- We'll create a 10*10 matrix with all values initialized to 1
- we dug down to sea level to retrieve a treasure chest. At the fourth row, sixth column, set the elevation to 0
```R
elevation <- matrix(1, 10, 10)
elevation[4, 6] <- 0
contour(elevation) # plot 2D
persp(elevation) # plot 3D
persp(elevation, expand=0.2) # plot 3D incline 0.2
image( matrix_name ) # plot heat map
```

Factors

- groupping data by category
```R
chests <- c('gold', 'silver', 'gems', 'gold', 'gems')
types <- factor(chests)

print(chests)
#[1] "gold"   "silver" "gems"   "gold"   "gems"  

print(types)
#[1] gold   silver gems   gold   gems  
#Levels: gems gold silver

as.integer(types) # groups of unique values
#[1] 2 3 1 2 1

levels(types)
#[1] "gems"   "gold"   "silver"

#plot by category
weights <- c(300, 200, 100, 250, 150)
prices <- c(9000, 5000, 12000, 7500, 18000)

plot(weights, prices, pch=as.integer(types))
legend("topright", c("gems", "gold", "silver"), pch=1:3)
# descibe symbol on top-right of plotting 

legend("topright", levels(types), pch=1:length(levels(types)))
```

Data Frames

```R
chests <- c('gold', 'silver', 'gems', 'gold', 'gems')
types <- factor(chests)
weights <- c(300, 200, 100, 250, 150)
prices <- c(9000, 5000, 12000, 7500, 18000)

treasure <- data.frame(weights, prices, types)

print(treasure)
#  weights prices  types
#1     300   9000   gold
#2     200   5000 silver
#3     100  12000   gems
#4     250   7500   gold
#5     150  18000   gems

treasure[[2]]
#[1]  9000  5000 12000  7500 18000

treasure[["prices"]]
# [1] 9000  5000 12000  7500 18000

treasure$prices
# [1] 9000  5000 12000  7500 18000
```

merging data frames
```R
targets <- read.csv("targets.csv")
#         Port Population Worth
#1   Cartagena      35000 10000
#2 Porto Bello      49000 15000
#3      Havana     140000 50000
#4 Panama City     105000 35000

infantry <- read.table("infantry.txt", sep="\t", header=TRUE)
#         Port Infantry
#1 Porto Bello      700
#2   Cartagena      500
#3 Panama City     1500
#4      Havana     2000

merge(x = targets, y = infantry)
#         Port Population Worth Infantry
#1   Cartagena      35000 10000      500
#2      Havana     140000 50000     2000
#3 Panama City     105000 35000     1500
#4 Porto Bello      49000 15000      700
```
