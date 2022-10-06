# Lab 1

## Question 1

```mermaid
classDiagram
class WebDisplay {
  +display()
  +search()
}
class MobileDisplay {
  +display()
  +search()
}
class IDisplay {
  <<interface>>
  +display()
  +search()
  +export()
}
class SearchView {
  +search()
  +filter()
  +sort()
}
class ExportView {
  +export()
  +toJson()
  +toCsv()
  +toYaml()
}

WebDisplay --|> IDisplay
MobileDisplay --|> IDisplay
IDisplay -- SearchView
IDisplay -- ExportView
```

## Question 2

```mermaid
classDiagram
class IDisplay {
  <<interface>>
}
class Product {
    -name
    -price
    -rating
    +...()
}
class ProductList {
    -type
    -products
    +addProduct()
    +newList()
    +sort()
    +filter()
    +display()
    +...()
}
class ShoeList {
    <<override>>
    +sort()
    +filter()
}
class BookList {
    <<override>>
    +sort()
    +filter()
}

IDisplay -- ProductList
Product <-- ProductList
ProductList <|-- ShoeList
ProductList <|-- BookList
```

## Question 3

```mermaid
classDiagram
class IVisualize {
  <<interface>>
  +toBarGraph()
  +toLineGraph()
  +increaseSampling()
  +decreaseSampling()
}
class ILocalStorage {
  <<interface>>
  +readFile()
  +writeFile()
}
class IDataStream {
  <<interface>>
  +openStream()
  +closeStream()
}
class IDataFormat {
  <<interface>>
  +readJson()
  +readXml()
  +readYaml()
  +toJson()
  +toXml()
  +toYaml()
}
class DataLogger {
  -...
  +...()
}

IDataStream <|-- DataLogger
ILocalStorage <|-- DataLogger
IDataFormat <|-- DataLogger
IVisualize <|-- DataLogger
```

## Question 4

```mermaid
classDiagram
class ISmartFarm {
  <<interface>>
  +newPowerMgmt()
  +newModule(IPowerMgmt)
  +runModule(IAutomationModule)
  +stopModule(IAutomationModule)
}
class IAutomationModule {
  <<interface>>
  -powerMgmtUnit
  +setPowerMgmtUnit(IPowerMgmt)
  +setPower()
}
class IPowerMgmt {
  <<interface>>
  +setPower()
  +getPower()
}
class SmartFarm {
  ...
  ...()
}
class IrrigationModule {
  ...
  ...()
}
class FeedingModule {
  ...
  ...()
}
class PowerGrid {
  ...
  ...()
}
class SolarPower {
  ...
  ...()
}

SmartFarm --|> ISmartFarm
ISmartFarm -- IAutomationModule
ISmartFarm -- IPowerMgmt
IAutomationModule <|-- IrrigationModule
IAutomationModule <|-- FeedingModule
IPowerMgmt <|-- PowerGrid
IPowerMgmt <|-- SolarPower
```
