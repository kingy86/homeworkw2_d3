# Homework: Pizza Shop

## Today

Today we created a program that tracks pizza orders. We created a Ruby class (`PizzaOrder`) and a database table (pizza\_orders) which is able to persist objects of this type. Currently, our database table is structured as follows...

| first_name | last_name | topping         | quantity |
|------------|-----------|-----------------|----------|
| Luke       | Skywalker | Pepperoni       | 2        |
| Leia       | Organa    | Ham & Pineapple | 1        |

Our table stores a combination of pizza and customer details. This isn't ideal for a number of reasons. If a single customer makes many orders then their details appear in our database many times. Firstly, this is not efficient. It would be much nicer if we could create a customer once and then attribute many orders too them. This would also help to protect us against typos as we would only have to submit a new customer once.

## Tomorrow

Tomorrow we are going to refactor our program. We will add another class, `Customer`, which will also have the full set of CRUD actions. This class will be responsible for the customer details, while `PizzaOrders` will be responsible for the pizza order that is being processed.

We will also extract some of the database connection code into a new class, `SqlRunner`.

Once completed, our tables should be structured as follows...

### customers

| id | first_name | last_name |
|----|------------|-----------|
| 1  | Luke       | Skywalker |
| 2  | Leia       | Organa    |

### pizza_orders

| id | topping         | quantity | customer_id |
|----|-----------------|----------|-------------|
| 1  | Pepperoni       | 2        | 1           |
| 2  | Ham & Pineapple | 1        | 2           |
| 3  | Meat Feast      | 1        | 1           |

## Task

Your task this evening is to read over the completed end\_code for tomorrow's lesson, understand it as much as possible, and answer the following questions.

1) What is the relationship between customers and pizza\_orders?

    Looking at the console.rb, it seems that the PizzaOrder class takes in customer
    id attribute when creating a new class object. (console.rb, line 15). 

2) At what point is the id of a `PizzaOrder` created?

    The id of PizzaOrder is created when order1 class object has been saved in
    console.rb line 19 after being the method saved has been passed (pizza_order.rb, line 31).

3) At what point do we assign a value to the `@id` instance variables of our objects?

    '@id' gets assigned a value on both objects on the same line (line 31) in both 
    customer.rb and pizza_order.rb.

4) Name 2 things that the `Customer`'s `@id` property is used for.

    Customer '@id' property is used to identify the customer in customer.rb and
    is also used to identify which pizza the customer has ordered.

5) Why might it be important to check if `options['id']` is `nil` in our `initialize` method before assigning `@id` the value of `options[‘id’].to_i?`
    
    This could be to make sure that class objects are not updated or replace by
    accident and that the class object is given a unique id.

6) What are the responsibilities of `SqlRunner`?

    SqlRunner takes the information passed by the SQL command and stores that information in an array named values.

7) How does `SqlRunner` improve the quality of our code?

    SQL runner saves us from having  DRY code in our methods with db.prepare
    and db.exec_prepared.

    
