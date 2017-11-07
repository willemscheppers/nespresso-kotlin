# Nespresso-kotlin

## Events

* InvestmentMade
    * amount
    * Tab
* CoffeePurchased
    * price
    * Tab
* CoffeeOrdered
    * Cups

## Value Objects

* Cup

## Entities

* Tab

## Usecases

* We want to keep track of which User purchased a Cup to make a Coffee. 
  When a User wishes to purchase a Coffee, he is given a list of all Cups and their availibility to choose from.
  When a Coffee is purchased the Inventory is updated and the Coffee is added to the Tab of the User.
* We want to be able to Order more Cups using a general Pot. This Pot is replenished by Users making an Investment. 
  When a User wishes to order more Coffee, he is given a list of all Cups and their availibility. 
  He can enter an amount of Cups he wishes to order, previewing the result in Inventory and Pot.
* We want an easy overview of a User's Investment. 
  When a User wishes to know how much he or another User is attributing to the Pot, he can view Statistics about that User
  containing a history of all Investments and purchased Coffees by that User.
* We want to give a discount to registered Users. When a User has a Tab, the cost of the Cup is added. If he doesn't have a Tab,
  the User will be asked to pay a cost of 0.50€ to the Pot. 