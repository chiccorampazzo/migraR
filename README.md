

# Project Title

migraR: package with functions to estimate Rogers and Castro models and other fuctions useful to estimate migration. 

## Getting Started

The package should be downloaded using devtools::install_github("elflacosebas/migraR"). Migration rates from Spain were calculated using the census 2011. The fucntion best_migramod has the complete example. 
There are probably some bugs that we pledge you can report to us using issues in github. 

### Prerequisites

What things you need to install the software and how to install them

```
install.packages('devtools')
install.packages('dplyr')
```

### Installing

A step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

The best_migramod function was designed using a tolerance that can be changed inside the functions. 

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
require(migraR)
require(dplyr)
data("es_asmr")
data1 <- es_asmr[-c(1,2),c(1,5)]
colnames(data1) <- c("x","y")
attach(data1)
model.rc.13 = MigraModel(
  name = 'castro_13',
  expr = rc_expression(profile = "thirteen")
)

model.rc.7 = MigraModel(
  name = 'castro_7',
  expr = rc_expression(profile = "seven")
)
model.rc.11 = MigraModel(
  name = 'castro_11',
  expr = rc_expression(profile = "eleven")
)

plot(data1, cex=0.1, xlab = 'Age', ylab = 'Standarized Migration Rate')
fitted.val.11 <- best_migramod(dataIn = data1, model.rc =model.rc.11, maxite = 5E2, profile = "eleven")
lines(data1[,1], model.rc.11$value(fitted.val.11$bestParam,data1), col="blue", lty=3)
fitted.val.7 <- best_migramod(dataIn = data1, model.rc =model.rc.7, maxite = 5E2, profile = "seven")
lines(data1[,1], model.rc.7$value(fitted.val.7$bestParam,data1), col="blue")
fitted.val.13 <- best_migramod(dataIn = data1, model.rc =model.rc.13, maxite = 5E2, profile = "thirteen")
lines(data1[,1], model.rc.13$value(fitted.val.13$bestParam,data1), col="green")
legend("topright",legend = c("seven","eleven","thirteen"),fill = c("red","blue","green"))

```

## Contributing

Please read [DESCRIPTION.md](https://github.com/elflacosebas/migrar) for more details.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **J. Sebastian Ruiz-Santacruz** - *Initial work* - [PurpleBooth](https://github.com/elflacosebas)

* **Jackson Garcés** - *Initial work* - [PurpleBooth](https://github.com/jackowacko)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.


## Acknowledgments

* to Joaquín Recaño Valverde (http://ced.uab.es/es/directori/joaquim-recano-valverde/), who inspires this work. 

