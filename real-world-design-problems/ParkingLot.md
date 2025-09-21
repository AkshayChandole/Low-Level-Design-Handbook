# [Parking Lot](#parking-lot)
Make an object-oriented design for a multi-entrance and exit parking lot system.

## [Problem definition](#problem-definition)
A parking lot is a designated area for parking vehicles, commonly found in venues like shopping malls, sports stadiums, and office buildings. It consists of a fixed number of parking spots allocated for different types of vehicles. Each spot is charged based on the duration a vehicle remains parked. Parking time is tracked using a parking ticket issued at the entrance. Upon exit, the customer can pay using either an automated exit panel or through a parking agent, with a credit/debit card or cash as accepted payment methods.
<p align="center">
  <img src="https://github.com/user-attachments/assets/e5d770a6-81da-47a5-b2ac-98f4c6d13f0d" alt="image" width="70%" height="70%">
</p>

---

#### Which design pattern(s) should be used for solving the problem of managing a parking lot efficiently?
  - Singleton: Useful for managing the payment processor and central ticket tracking to ensure only one instance controls critical operations across floors and exits.
  - Strategy: Allows for applying different pricing models based on time parked and vehicle type.
  - Factory Method: Helps create various parking spot and vehicle type objects dynamically without changing client code.
  - Observer (Optional): Can notify parking agents or automated panels when spots become available or full.
  - Proxy (Optional): Can manage access to payment gateways or ticket validation, adding security and caching if needed.

---

## [Requirements collection](#requirements-collection)
1. The parking lot must support a total capacity of up to 40,000 vehicles.
2. The parking lot must support multiple types of parking spots:
   - Accessible (for individuals with disabilities)
   - Compact
   - Large
   - Motorcycle
3. The parking lot should provide multiple entrance and exit points to support efficient traffic flow.
4. The system must support parking for four types of vehicles: cars, trucks, vans, and motorcycles.
<p align="center">
  <img src="https://github.com/user-attachments/assets/258825d1-51a4-4883-9a95-14046d6aceb6" alt="image" width="40%" height="40%">
</p>

5. A display board at each entrance and on every floor should show the current number of available parking spots for each parking spot type.
<p align="center">
  <img src="https://github.com/user-attachments/assets/0088acd1-8d48-4e1a-add4-1df029159d97" alt="image" width="40%" height="40%">
</p>

6. The system must not allow more vehicles to enter once the parking lot reaches its maximum capacity.
7. When the parking lot is fully occupied, a clear message should be shown at each entrance and on all parking lot display boards.
8. Customers must be issued a parking ticket at entry, which will be used to track parking time and calculate payment at exit.
9. Customers should be able to pay for parking at the automated exit panel.
10. The parking lot system must support configurable pricing rates based on vehicle type and/or parking spot type and different rates for different parking durations (e.g., first hour, subsequent hours).
11. Payments must be accepted via credit/debit card and cash at all payment points.
<p align="center">
  <img src="https://github.com/user-attachments/assets/84781e1b-53e0-4b90-a7dd-c62507238182" alt="image" width="50%" height="50%">
</p>

---

## [Use Case Diagram for the Parking Lot](#use-case-diagram-for-the-parking-lot)
### [System](#system)
Our system is the parking lot system. It manages the entire parking process, including vehicle entry and exit, parking spot allocation, payment processing, and administration of parking lot resources.

### [Actors](#actors)
Here are the main actors of our parking lot system:
#### Primary actors -
  - **Customer:** Parks their vehicle, obtains a parking ticket, pays the parking fee, and exits the parking lot.

#### Secondary actors -
  - **Admin:** Manages system resources, such as parking spots, entry/exit panels, and pricing. Also handles account and system configuration.

### [Use cases](#use-cases)
#### Admin use cases -
| Use Case                | Description |
|------------------------|-------------|
| **Add a parking spot** | Add a new parking spot by specifying type (accessible, compact, large, motorcycle) and location (floor, section). |
| **Remove the parking spot** | Remove a spot from the system (e.g., maintenance, repurposing). |
| **Update the parking spot** | Change details like type or status (available/unavailable). |
| **Add/modify rate** | Configure or update pricing rates by duration, vehicle, or spot type. |
| **Update the account** | Update admin/agent account details, manage payment info or permissions. |
| **Login/Logout** | Securely access or exit the system. |
| **View the account** | View account details: payment status, balances, activity history. |

#### Customer use cases -
| Use Case              | Description |
|------------------------|-------------|
| **Take ticket**        | Receive a parking ticket at the entrance, which records vehicle information and entry time. |
| **Scan ticket at exit**| Present the ticket at the exit to calculate the total parking fee based on duration, vehicle, and spot type. |
| **Pay for ticket**     | Pay the parking fee using cash or card at an automated exit panel. |
| **Park vehicle**       | Park the vehicle in the spot assigned by the system. |

#### Parking Lot System use cases -
| Use Case                 | Description |
|---------------------------|-------------|
| **Assign parking spot**   | Automatically select and allocate an available spot based on vehicle type, spot type, and real-time availability. |
| **Remove parking spot**   | Update the spot’s status to unavailable if the spot is out of service or being removed from inventory. |
| **Show FULL status**             | Display a “FULL” status at entrances and on display boards when the parking lot or a specific spot type is at capacity. |
| **Show available spots**  | Provide real-time updates of available spots by type at each entrance, exit, and floor. |
| **Calculate parking fee** | Determine the total amount owed by the customer based on duration, vehicle type, and spot type, triggered when the ticket is scanned at exit. |

Here is the use case diagram of the parking lot system:
<img width="1386" height="933" alt="image" src="https://github.com/user-attachments/assets/7210da1e-4322-417b-af70-ab9829df9879" />

## [Class Diagram for the Parking Lot](#class-diagram-for-the-parking-lot)

### Vehicle
- Our parking lot system should have a vehicle object according to the requirements. The vehicle can be a car, a truck, a van, or a motorcycle.
- There are two ways to represent a vehicle in our system:
    1. Enumeration
    2. Abstract class
- Enumeration approach is not proficient for object-oriented design because if we want to add one more vehicle type later in our system, we would need to update the code in multiple places, violating the Open/Closed principle of the SOLID design principle. The Open/Closed principle states that classes can be extended but not modified. Therefore, it is recommended not to use the enumeration data type as it is not a scalable approach.
- The abstract class for Vehicle is the best approach. It allows us to create derived child classes for the Vehicle class. It can also be extended easily in case the vehicle type changes.
<p align="center">
  <img src="https://github.com/user-attachments/assets/ba7a06ac-3fd2-46ce-8bd8-c2f956533f3e" alt="image" width="50%" height="50%">
</p>

### Parking spot
Similar to the Vehicle class, the ParkingSpot should also be an abstract class. There are four types of parking spots: handicapped, compact, large, and motorcycle. These classes can be derived from the parking spot abstract class.
<p align="center">
  <img src="https://github.com/user-attachments/assets/a6b99b61-7845-4ee0-b980-1749094056cb" alt="image" width="50%" height="50%">
</p>

### Account
Similar to the Vehicle and ParkingSpot classes, Account should also be an abstract class. The Admin class is derived from this abstract class.
<p align="center">
  <img src="https://github.com/user-attachments/assets/c153b9a1-538a-4c3d-b89c-bfd3abe53be0" alt="image" width="50%" height="50%">
</p>

### Display board
This class represents the free parking spot types and the number of empty slots.
<p align="center">
  <img src="https://github.com/user-attachments/assets/92420d44-fe59-492b-a9ef-d32b93f42eb1" alt="image" width="50%" height="50%">
</p>

### Entrance and exit 
The Entrance class is responsible for generating the parking ticket whenever a vehicle arrives. It contains the ID attribute, since there are multiple entrances to the parking lot. It also has the getTicket() method.

The ```Exit``` class is responsible for validating the parking ticket’s payment status before allowing the vehicle to exit the parking lot. It contains the ID attribute, since there are multiple exits to the parking lot. It also has the **`validateTicket()`** method.
<p align="center">
  <img src="https://github.com/user-attachments/assets/691ef67b-2f2a-4724-a218-d4f98e448ead" alt="image" width="50%" height="50%">
</p>


### Parking ticket
The **`ParkingTicket`** class is one of the central classes of the system. It keeps track of the entrance and exit times of the vehicles, the amount, and the payment status.

<p align="center">
  <img src="https://github.com/user-attachments/assets/72de33ef-9a08-46f9-97dd-e04ac3a74146" alt="image" width="25%" height="25%">
</p>

### Payment
The **`Payment`** class will be an abstract class and will have two child classes, **`card`** and **`cash`**, since these are two payment methods of the parking lot system.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e9d8c54f-94fa-4020-ae7f-849d9e941c96" alt="image" width="25%" height="25%">
</p>

### Parking rate
The **`ParkingRate`** class is responsible for calculating the final payment based on the time spent in the parking lot.
<p align="center">
  <img src="https://github.com/user-attachments/assets/dfea7832-1a21-45a2-b957-9091fb82b022" alt="image" width="15%" height="15%">
</p>

### Parking lot
Now, we will discuss the design of the whole **`ParkingLot`** system class. This parking lot system is composed of smaller objects we have already designed, like entrance/exit, parking spots, parking rates, etc.
<p align="center">
  <img src="https://github.com/user-attachments/assets/dfadbaa6-f71f-45c1-b84d-441bfe32812c" alt="image" width="25%" height="25%">
</p>

### The enumerations and custom data types
The following provides an overview of the enumerations and custom data types used in this problem:
- **`PaymentStatus`**: We need to create an enumeration to keep track of the payment status of the parking ticket, whether it is paid, unpaid, canceled, refunded, and so on.
- **`AccountStatus`**: We need to create an enumeration to keep track of the status of the account, whether it is active, canceled, closed, and so on.
- **`TicketStatus`**: We need to create an enumeration to keep track of the current status of a parking ticket, whether it is issued, in use, paid, validated, canceled, refunded, and so on.
<p align="center">
  <img src="https://github.com/user-attachments/assets/54cdf87d-c231-4e02-ab6b-3cb90909904e" alt="image" width="50%" height="50%">
</p>

### Address
We also need to create a custom data type, **`Address`**, that will store the location of the parking lot.
<p align="center">
  <img src="https://github.com/user-attachments/assets/c19932b7-6f72-48e3-99df-43de0cc5a5b3" alt="image" width="30%" height="30%">
</p>

### Person
The **`Person`** class is used to store information related to a person like a name, street address, country, etc.
<p align="center">
  <img src="https://github.com/user-attachments/assets/36114419-b565-41fa-a44d-367d5770d2d5" alt="image" width="30%" height="30%">
</p>


---


## [Relationship between the classes](relationship-between-the-classes)

### Association
Association represents a loose relationship between two classes, where one class refers to another to use its functionality or store a reference. Associations typically do not imply ownership, and the associated object may exist independently of the referring object.

In the parking lot system, association relationships include:
- Each **`ParkingSpot`** is associated with a **`Vehicle`** object. When a vehicle is parked, the spot keeps a reference to the vehicle. This allows the parking spot to track which vehicle is currently occupying it. However, the vehicle does not directly reference its spot.
- A **`Vehicle`** holds an association to its current **`ParkingTicket`**. When a vehicle enters the lot, it receives a ticket, and this association allows for tracking and processing of parking sessions.
- The **`ParkingTicket`** class maintains references to the **`Entrance`**, **`Exit`**, and **`Vehicle`** involved in the parking session, allowing the system to trace the entry and exit points and the vehicle details for any given ticket.
- The **`DisplayBoard`** and **`ParkingSpot`** should have an association relationship. The DisplayBoard is responsible for showing the availability/status of multiple ParkingSpot objects—it maintains a reference (typically a list or map) to all spots it displays.

<p align="center">
  <img src="https://github.com/user-attachments/assets/52e2fd82-8731-4989-8393-36e08ad8c0bb" alt="image" width="60%" height="60%">
</p>

### Composition
Composition is a strong form of association that implies ownership and a whole-part relationship. When a composite object is destroyed, its components are destroyed as well. In other words, the composed objects do not exist independently of their parent.

In our parking lot system, composition relationships are seen in:
- The **`ParkingLot`** class is composed of its key components, including all instances of **`Entrance`**, **`Exit`**, **`ParkingSpot`**, **`DisplayBoard`**, **`ParkingRate`**, and all current **`ParkingTicket`** objects. The parking lot is responsible for the creation, management, and destruction of these components, which do not exist outside the context of the parking lot.
- Each **`ParkingTicket`** is composed of a **`Payment`** object. The payment is created and managed by the ticket, representing the financial transaction for that specific parking session. The payment does not exist independently outside the ticket.
<p align="center">
  <img src="https://github.com/user-attachments/assets/1c03d794-5d5d-4ac1-b4b0-172ad1b7ecd6" alt="image" width="60%" height="60%">
</p>

### Inheritance
Inheritance, also known as generalization, is a relationship where one class (the child or subclass) inherits behavior and attributes from another class (the parent or superclass). This allows for code reuse and logical grouping of shared functionality, while enabling polymorphic behavior.

In the parking lot system, inheritance relationships are structured as follows:
- The abstract **`Vehicle`** class serves as the general blueprint for different types of vehicles, with **`Car`**, **`Truck`**, **`Van`**, and **`Motorcycle`** as its concrete subclasses. Each subclass can extend or override the behavior defined in Vehicle.
- Similarly, the abstract **`ParkingSpot`** class defines the core properties and behaviors for a parking spot. The specific spot types — **`AccessibleSpot`**, **`CompactSpot`**, **`LargeSpot`**, and **`MotorcycleSpot`** — are implemented as subclasses, each potentially providing specialized logic for assigning vehicles.
- The **`Payment`** abstract class provides the basic structure for payment operations, while **`Cash`** and **`CreditCard`** classes implement the details for each payment method.




