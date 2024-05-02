# WSI Task.ERD.1
Entity Relationship Diagram (Vertabelo)

## Task

Create an entity relationship diagram for requirements below. Diagram should be created using vertabelo (https://vertabelo.com/) .

After you finish:
Upload your solution (exported from vertabelo in png or svg format) as an attachment of your assignment

* Design an entity-relationship model for the car rental. 

* Before the first rent, client should be added to the database. 

* Client is described by the first name, surname, phone number, date of birth, address, driver license number, ID card serial number or if client is a foreigner, passport number. 

* Address consists of: street name, street number, apartment number (optional) and city. 

* We need to keep information about cars which client can rent such as name of manufacturer, model, production year, number of doors, engine capacity. 

* Client can rent multiple cars but only one at the same time. For every rent we want to insert date range (starting date and end date of the rent). 

* There is a possibility to add a comment about specified rent, but it is not required. 

* Rental price is calculated individually based on client’s discount.

---

## Solution

Based on the given requirements, here's an entity-relationship (ER) model for the car rental system:

Entities:
1. Client
2. Address
3. Car
4. Rent

Relationships
- A Client can have one Address (one-to-one relationship)
- A Client can rent multiple Cars, but only one at a time (one-to-many relationship)
- A Car can be rented by multiple Clients over time (many-to-one relationship)
- A Rent connects a Client with a Car for a specific date range and stores additional information about the rental (many-to-many relationship with additional attributes)

Attributes:
1. Client:
   - ClientID (primary key)
   - FirstName
   - Surname
   - PhoneNumber
   - DateOfBirth
   - DriverLicenseNumber
   - IDCardSerialNumber
   - PassportNumber (for foreigners)
   - Discount

2. Address:
   - AddressID (primary key)
   - StreetName
   - StreetNumber
   - ApartmentNumber (optional)
   - City
   - ClientID (foreign key referencing Client)

3. Car:
   - CarID (primary key)
   - Manufacturer
   - Model
   - ProductionYear
   - NumberOfDoors
   - EngineCapacity

4. Rent:
   - RentID (primary key)
   - ClientID (foreign key referencing Client)
   - CarID (foreign key referencing Car)
   - StartDate
   - EndDate
   - Comment (optional)
   - RentalPrice

ER Diagram:

```
+---------------+         +---------------+
|    Client     |         |    Address    |
+---------------+         +---------------+
| ClientID (PK) |         | AddressID (PK)|
| FirstName     |---------| StreetName    |
| Surname       |         | StreetNumber  |
| PhoneNumber   |         | ApartmentNumber|
| DateOfBirth   |         | City          |
| DriverLicenseNumber |   | ClientID (FK) |
| IDCardSerialNumber  |   +---------------+
| PassportNumber|           
| Discount      |           
+---------------+           
      |                     
      |                     
      |                     
+---------------+           
|     Rent      |           
+---------------+           
| RentID (PK)   |           
| ClientID (FK) |
| CarID (FK)    |
| StartDate     |
| EndDate       |
| Comment       |
| RentalPrice   |
+---------------+
      |
      |
+---------------+
|     Car       |
+---------------+
| CarID (PK)    |
| Manufacturer  |
| Model         |
| ProductionYear|
| NumberOfDoors |
| EngineCapacity|
+---------------+
```


This ER model captures the main entities, their attributes, and the relationships between them based on the provided requirements. The model ensures that a client can rent multiple cars, but only one at a time, and rental prices are calculated individually based on the client's discount.
