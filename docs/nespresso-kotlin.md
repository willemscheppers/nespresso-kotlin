# Nespresso-kotlin

## Use cases

* We want to keep track of which _User_ purchased how many _Cups_ to make _Coffees_.
  When a _User_ wishes to purchase a _Coffee_, he is given a list of all _Cups_ and their availability to choose from.
  When a _Coffee_ is purchased, is it added to the list of purchased _Coffees_ of the User, and that User's balance is
  updated accordingly.
* We want to keep track of the availability of _Cups_ through a general _Pot_.
  When a _User_ wishes to purchase a _Coffee_, the availability of a _Cup_ corresponds to the amount of that _Cup_ in the _Pot_.
  After a _Coffee_ was purchased, the _Pot_ is updated.
* We want to be able to add more _Cups_ to the _Pot_ through an _Order_.
  When a _User_ wishes to order more _Coffee_, he is given a list of all _Cups_ and their availability.
  He can enter an amount of _Cups_ he wishes to _Order_, previewing the result in the amount of _Cups_ as well as the balance of the _Pot_.
* We want an easy overview of a _User's_ _Investments_.
  When a _User_ wishes to know how much he or another _User_ is attributing to the _Pot_, he can view _Statistics_ about that _User_
  containing a history of all _Investments_ and purchased _Coffees_ by that _User_.
* We want to give a discount to registered _Users_.
  When a _User_ is registered, the cost of the _Cup_ is added. If he isn't registered,
  the _User_ will be asked to pay a cost of **0.50€** to the _Pot_.

## Value Objects

* Cup
    * has a name
    * has an intensity
    * has a cost
* Coffee
    * has a Cup
    * has a User

## Entities

* User
    * has a list of Investments.
    * has a list of purchased Coffees.
    * has a balance, which is the sum the Investments made by this User, subtracted by
       the sum of the costs of purchased Coffees
* Pot
    * has a map of Cups and their amount, representing their availability.
    * has a balance, which is the sum of all Investments subtracted by the sum of the costs of all Orders.
* Investment
    * has an amount
* Order
    * has a map of Cups and their amount.
    * has a cost, equal to the sum of the cost of the Cups multiplied by their amount.

## Events

* InvestmentMade
    * has an amount
    * has a User
* CoffeePurchased
    * has a Cup
    * has a User
* CoffeeOrdered
    * has an Order

## Event sourcing

* User
    * InvestmentMade adds a new Investment to the list of Investments.
    * CoffeePurchased adds a new Coffee to the list of purchased Coffees.
    * InvestmentMade increases the balance by the amount of the Investment.
      CoffeePurchased decreases the balance by the cost of the Cup.
* Pot
    * InvestmentMade increases the balance by the amount of the Investment.
    * CoffeeOrdered increases the amount of Cups by the amount of the Order and decreases the balance by the cost of the Order.