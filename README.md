# OOP GUI-based-Book-Store-System

## Name: 

BookStoreApplication  


## Participating Actors:

Owner and Customer  


## Entry Condition:

This use case begins when either the customer or the owner logs into the application. 

## Exit Condition:

The use case ends when the customer or owner logs out after completing their session.


## Exceptions:

The system verifies the username and password entered. If the credentials are 
incorrect, the application displays an "Incorrect" message and triggers an exception. Additionally, 
the system checks whether the customer has enough points to redeem rewards. 

 

## Flow of Events:
   
The bookstore system follows a structured workflow to manage books, customers, and transactions 
efficiently. 

Adding and Removing Books: 
- The store Owner can add new books to the inventory by entering the book's title and price in a 
new row within the book table. Once the details are entered, clicking the “Add” button updates 
the database, making the book available for customers. 
- If the Owner wishes to remove a book, they can simply select the corresponding row in the book 
table and click the “Delete” button. This action permanently removes the book from the 
inventory, ensuring that it is no longer available. 
Managing Customers: 
- To register a new customer, the Owner enters the customer's username and password into the 
customer table. After entering these details, clicking the “Add” button successfully adds the 
customer to the system. 
- If an account needs to be removed, the Owner can locate the customer in the table, select their 
row, and press the “Delete” button, effectively removing their profile and access to the bookstore 
system. 

Purchasing Books:
- Customers can browse the available books and select the ones they wish to purchase by checking 
the respective checkboxes next to each book title. After making their selection, they can choose 
between two purchasing options: 
1. Clicking the “Buy” button will proceed with the purchase without applying any reward 
points. 
2. Clicking the “Redeem and Buy” button will apply a discount based on the customer's 
accumulated points. For every 100 points they have, a $1 CAD deduction is applied to the 
total price of the books. 
Transaction and Reward System: 
- After a successful purchase, the system calculates the total transaction cost and displays the final 
amount paid by the customer. 
- If the purchase is made without redeeming points, the system awards new points to the customer. 
For every $1 CAD spent, the customer earns 10 points, encouraging future purchases. 
- Customers are assigned a “Silver” or “Gold” status based on their accumulated points. This status 
may offer additional benefits or perks, rewarding frequent buyers for their loyalty. 


## Special Requirements:

Each entry into the list of books is only for one copy, and once that copy 
is sold, it must be deleted from the booktable list.  

 
## Reasoning for Using the State Design Pattern: 

 When developing the bookstore application, the State Design Pattern was implemented. This 
pattern is used when an object's behavior needs to change based on its current state. A key characteristic 
of this pattern is that altering the state does not directly modify the current state itself. Instead, the state 
object handles the transition, ensuring that the object's behavior adapts accordingly without affecting the 
existing state. 

In the bookstore application, users interact with the system either as customers or owners. 
According to the class diagram, the Owner’s Table and Customer Table manage most of the application's 
operations. The CustomersTable serves as the context class, which is exposed to external interactions. It is 
responsible for maintaining the current state instance and delegating tasks to the appropriate concrete state 
classes. 

The CustomerState class acts as an abstract state class, defining the minimum set of behaviors or 
functionalities required for the concrete classes. The concrete state classes, Gold and Silver, implement 
these behaviors, each representing a different customer tier with distinct functionalities. 

The remaining classes in the design are interconnected through dependencies, meaning that 
modifications in one class trigger corresponding changes in related classes, ensuring consistent behavior 
across the application. 


## Owner Use of the Application:

 The bookstore owner(s) will be able to log into an admin account, which presents them with a 
screen with three buttons. These buttons are Books, Customers, and Logout. These buttons bring the 
owner to a screen with a list of books currently available with their prices and a list of customer 
usernames and passwords with their accumulated points, or take the owner back to the main screen 
respectively. The owner can add or remove books from the list on the respective screen or add and remove 
customer accounts. When a new customer account is added by the owner, it starts with a points balance of 
0.  
