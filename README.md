# Shirt Capsule

## Basic Transactional Capsule
Basic models to exercise a transactional flow for buying shirts. Very little work done here on presentation 
(some simple dialogs and no layouts). Check the stories for example use cases.

# Example flow

```
Buy a medium V-Neck
Change the size
(Select small)
Make that a large V-Neck and add an Oxford Dress Shirt
Remove Polo Shirt from my order
(Note above won't match any existing shirt so you get a prompt. Select V-Neck)
Add 2 Medium Polo Shirts to my order
Change the quantity
Note there are two items in the shopping cart so one must be selected. Select Polo Shirt
(Enter 5)
Change the quantity of the Polo Shirt
(Enter 3)
Click Yes
```

# Finding shirts

Example 1: List of all available shirts
```
Show a list of all shirts
```

Example 2: Find specific shirt

```
Show Polo Shirts
```

Example 3: Find shirt with specific brand

```
Show Ralph Lauren Shirts
```

# Creating an order

Example 1: No reference to a shirt. System will prompt for the user to pick a shirt from the list of all available shirts. User will also be prompted for size and quantity.

```
Find shirts I can buy
```

Example 2: Same as example 1 but no prompts for size or quantity.

```
Buy 2 medium shirts
```


Example 3: User refers to the name of the item that should be added to the cart.

```
Buy a Large Sweatshirt
```

Example 4: User makes an order with multiple items. Note that this is not trainable today (because of NL training limitation) but you can try using aligned-nl

```
Order 2 Polo Shirts and 1V-Neck Shirt
```

# Updating the order

## Adding an item to the cart

Continue on an order. 

```
Add 2 Medium Polo Shirts to my order
```

## Deleting an item from the cart

Continue on an order. Similar behavior as changing size or quantity.

Example: 
```
Remove Polo Shirt from my order
```

## Changing shirt size

Continue on an order.

Example 1: This should work without any prompts if there is only a single item in the cart.
If multiple items in the cart and none is referenced then user will be prompted to choose an item from the cart.
If there is no items in the cart then this should just state that there's no items.

```
Change the size to Large
```

Example 2: Use a searchTerm to reference one of the items in the cart.

```
Change the size of the Polo Shirt to small
```

## Changing shirt quantity

Continue on an order. Same behavior as change size. 

Example:

```
Change that to 3 Polo Shirts
```

## Changing and adding to the cart

Continue on an order and change an item and add another item in one input.

Example:
```
Make that  a Large V-Neck and add an Oxford Dress Shirt
```

## Changing shirt size without providing a value

Continue on an order.

Example 1:
```
Change the size
```

Example 2:
```
Change the size of the Polo Shirt
```

## Changing shirt quantity without providing a value

Continue on an order.

Example 1:
```
Change the quantity
```

Example 2:
```
Change the quantity of the Polo Shirt
```

# Cancelling the order

Continue on an order.

Example:

```
Cancel this order
```

# Committing the order

Commit the order.

```
Commit my order
```

# Asking for property projections

Property projections are best when there 1 or a few result entities (weather, uber, flightStatus). It is not recommended
when there is a large/unbounded number or result entities. So it is not a good idea to have training examples such as 
below assuming that there are many shirts that can be returned by the provider.

```
What shirt brands do you have?
```

If we wanted to support this kind of Q&A we should write a specific action for it (not actually done for this example):

```
What shirt brands do you have?
```

Just for demonstration purposes a property projection support for property projection is added for the case when user asks
contextually for the total price of an order. To try it out start an order: 

```
Buy a Large Sweatshirt
```

and then ask for the total price:

```
What is the total price of the order
```
