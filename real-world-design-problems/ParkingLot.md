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

---

## [Class diagram of the parking lot system](#class-diagram-of-the-parking-lot-system)

In this section, we outline the multiplicity (cardinality) relationships between the main classes in our parking lot system.  

| **Source**      | **Target**      | **Multiplicity** | **Reason**                                                                                  |
|------------------|-----------------|------------------|----------------------------------------------------------------------------------------------|
| ParkingLot       | Entrance        | 1 -- 1..*        | A parking lot must have at least one entrance, and can have multiple for efficient flow.     |
| ParkingLot       | Exit            | 1 -- 1..*        | A parking lot must have at least one exit, and can have multiple for smooth operation.       |
| ParkingLot       | ParkingSpot     | 1 -- 1..*        | Every parking lot manages multiple parking spots.                                           |
| ParkingLot       | ParkingTicket   | 1 -- 0..*        | The lot manages zero or more tickets at any given time.                                     |
| ParkingLot       | DisplayBoard    | 1 -- 0..*        | There may be zero or more display boards (e.g., per floor or entrance).                     |
| ParkingLot       | ParkingRate     | 1 -- 1           | One parking rate policy per parking lot (single rate object for whole lot).                 |
| ParkingSpot      | Vehicle         | 0..1 -- 1        | Each parking spot can have zero or one vehicle at a time (may be empty or occupied).        |
| Vehicle          | ParkingTicket   | 1 -- 1           | A vehicle can have at most one ticket (only when parked).                                   |
| ParkingTicket    | Payment         | 1 -- 1           | Each ticket is paid for with one payment transaction.                                       |
| DisplayBoard     | ParkingSpot     | 1 -- 0..*        | Each display board shows status of zero or more parking spots.                              |

<img width="1881" height="890" alt="image" src="https://github.com/user-attachments/assets/52112b62-20a8-404a-9ba0-7ffe69bb27f5" />

---

## [Design pattern](#design-pattern)
Our parking lot system employs several standard object-oriented design patterns to enhance its flexibility and maintainability:
- **Singleton pattern:** The ParkingLot class is implemented as a Singleton. This ensures that only one instance of the parking lot system exists throughout the application's lifecycle, centralizing the management of all lot resources.
- **Factory and Abstract Factory patterns:** The creation of different types of parking spots, vehicles, or payments can leverage the Factory and Abstract Factory patterns. These patterns make it easy to introduce new types of spots, vehicles, or payment methods in the future, simply by extending the factory logic, without changing the core business logic or system structure.

---

## [Additional requirements](#additional-requirements)
Let’s see some examples of additional requirements:

### **Parking floor:** 
The parking lot should have multiple floors where customers can park their cars. The class diagram provided below shows the relationship of **`ParkingFloor`** with other classes:
<p align="center">
  <img src="https://github.com/user-attachments/assets/a7fcd904-a064-4a5f-8222-a89c59bd6956" alt="image" width="70%" height="70%">
</p>

### Electric: 
The parking lot should have some parking spots specified for electric cars. These spots should have an electric panel through which customers can pay and charge their vehicles. The class diagram provided below shows the relationship of **`Electric`** and **`ElectricPanel`** with other classes:
<p align="center">
  <img src="https://github.com/user-attachments/assets/65d30913-56b3-4f9a-8535-71a563ca83d5" alt="image" width="75%" height="75%">
</p>

---

## [Code](#code)

<details>
<summary>Java</summary>

```java


```java
// TicketStatus.java
public enum TicketStatus { ISSUED, IN_USE, PAID, VALIDATED, CANCELED, REFUNDED }

// AccountStatus.java
public enum AccountStatus { ACTIVE, CLOSED, CANCELED, BLACKLISTED, NONE }

// PaymentStatus.java
public enum PaymentStatus { COMPLETED, FAILED, PENDING, UNPAID, REFUNDED }

// Person.java
public class Person {
    private String name;
    private String address;
    private String phone;
    private String email;
}

// Address.java
public class Address {
    private int zipCode;
    private String street;
    private String city;
    private String state;
    private String country;
}

// ParkingSpot.java
public abstract class ParkingSpot {
    protected int id;
    protected boolean isFree = true;
    protected Vehicle vehicle;

    public ParkingSpot(int id) { this.id = id; }
    public boolean isFree() { return isFree; }
    public abstract boolean assignVehicle(Vehicle v);
    public boolean removeVehicle() {
        if (!isFree && vehicle != null) {
            System.out.println("Slot " + id + " freed (was " + vehicle.getLicenseNo() + ")");
            vehicle = null; isFree = true;
            return true;
        }
        return false;
    }
    public int getId() { return id; }
}

// Handicapped.java
public class Handicapped extends ParkingSpot {
    public Handicapped(int id) { super(id); }
    public boolean assignVehicle(Vehicle v) {
        if (isFree) {
            System.out.println("Allocated Handicapped slot " + id + " to " + v.getLicenseNo());
            this.vehicle = v; isFree = false; return true;
        }
        return false;
    }
}

// Compact.java
public class Compact extends ParkingSpot {
    public Compact(int id) { super(id); }
    public boolean assignVehicle(Vehicle v) {
        if (isFree) {
            System.out.println("Allocated Compact slot " + id + " to " + v.getLicenseNo());
            this.vehicle = v; isFree = false; return true;
        }
        return false;
    }
}

// Large.java
public class Large extends ParkingSpot {
    public Large(int id) { super(id); }
    public boolean assignVehicle(Vehicle v) {
        if (isFree) {
            System.out.println("Allocated Large slot " + id + " to " + v.getLicenseNo());
            this.vehicle = v; isFree = false; return true;
        }
        return false;
    }
}

// MotorcycleSpot.java
public class MotorcycleSpot extends ParkingSpot {
    public MotorcycleSpot(int id) { super(id); }
    public boolean assignVehicle(Vehicle v) {
        if (isFree) {
            System.out.println("Allocated Motorcycle slot " + id + " to " + v.getLicenseNo());
            this.vehicle = v; isFree = false; return true;
        }
        return false;
    }
}

// Vehicle.java
public abstract class Vehicle {
    private String licenseNo;
    private ParkingTicket ticket;
    public Vehicle(String lic) { this.licenseNo = lic; }
    public String getLicenseNo() { return licenseNo; }
    public void assignTicket(ParkingTicket t) { this.ticket = t; }
    public ParkingTicket getTicket() { return ticket; }
}

// Car.java
public class Car extends Vehicle { public Car(String lic){super(lic);} }

// Van.java
public class Van extends Vehicle { public Van(String lic){super(lic);} }

// Truck.java
public class Truck extends Vehicle { public Truck(String lic){super(lic);} }

// Motorcycle.java
public class Motorcycle extends Vehicle { public Motorcycle(String lic){super(lic);} }

// Account.java
public abstract class Account {
    private String userName;
    private String password;
    private Person person;
    private AccountStatus status;
    public abstract boolean resetPassword();
}

// Admin.java
public class Admin extends Account {
    public boolean addParkingSpot(ParkingSpot spot) { return true; }
    public boolean addDisplayBoard(DisplayBoard board) { return true; }
    public boolean addEntrance(Entrance entrance) { return true; }
    public boolean addExit(Exit exit) { return true; }
    public boolean resetPassword() { return true; }
}

// DisplayBoard.java
import java.util.*;

public class DisplayBoard {
    private int id;
    private Map<String, Integer> freeCount = new HashMap<>();
    public DisplayBoard(int id) { this.id = id; }
    public void update(Collection<ParkingSpot> spots) {
        freeCount.clear();
        for (ParkingSpot s : spots) {
            if (s.isFree()) {
                String type = s.getClass().getSimpleName();
                freeCount.put(type, freeCount.getOrDefault(type, 0) + 1);
            }
        }
    }
    public void showFreeSlot() {
        System.out.println("\nFree slots by type:");
        System.out.printf("%-15s %s%n", "Type", "Count");
        for (String type : freeCount.keySet())
            System.out.printf("%-15s %d%n", type, freeCount.get(type));
    }
}

// ParkingRate.java
public class ParkingRate {
    public double calculate(double hours, Vehicle v, ParkingSpot s) {
        int hrs = (int)Math.ceil(hours);
        double fee = 0;
        if (hrs >= 1) fee += 4;
        if (hrs >= 2) fee += 3.5;
        if (hrs >= 3) fee += 3.5;
        if (hrs > 3) fee += (hrs - 3) * 2.5;
        return fee;
    }
}

// Entrance.java
public class Entrance {
    private int id;
    public Entrance(int id) { this.id = id; }
    public ParkingTicket getTicket(Vehicle v) {
        return ParkingLot.getInstance().parkVehicle(v);
    }
}

// Exit.java
import java.util.*;

public class Exit {
    private int id;
    public Exit(int id) { this.id = id; }
    public void validateTicket(ParkingTicket t) {
        Date now = new Date();
        t.setExitTime(now);
        double hrs = (now.getTime() - t.getEntryTime().getTime()) / 3600000.0;
        double fee = ParkingLot.getInstance().rate.calculate(hrs, t.getVehicle(), ParkingLot.getInstance().getSpot(t.getSlotNo()));
        t.setAmount(fee);
        System.out.printf("Ticket %d | Parked: %.2f hrs | Fee: $%.2f\n", t.getTicketNo(), hrs, fee);
        Payment p = (fee > 10) ? new CreditCard(fee) : new Cash(fee);
        p.initiateTransaction();
        ParkingLot.getInstance().freeSlot(t.getSlotNo());
        t.setStatus(TicketStatus.PAID);
    }
}

// ParkingTicket.java
import java.util.*;

public class ParkingTicket {
    private static int ticketSeed = 1000;
    private int ticketNo;
    private int slotNo;
    private Vehicle vehicle;
    private Date entryTime, exitTime;
    private double amount;
    private TicketStatus status;
    private Payment payment;
    public ParkingTicket(int slotNo, Vehicle v) {
        this.ticketNo = ticketSeed++;
        this.slotNo = slotNo;
        this.vehicle = v;
        this.entryTime = new Date();
        this.status = TicketStatus.ISSUED;
        v.assignTicket(this);
        System.out.println("Ticket issued: " + ticketNo);
    }

    public int getTicketNo() { return ticketNo; }
    public int getSlotNo() { return slotNo; }
    public Vehicle getVehicle() { return vehicle; }
    public Date getEntryTime() { return entryTime; }
    public Date getExitTime() { return exitTime; }
    public void setExitTime(Date dt) { this.exitTime = dt; }
    public void setAmount(double amt) { this.amount = amt; }
    public double getAmount() { return amount; }
    public void setStatus(TicketStatus s) { this.status = s; }
    public TicketStatus getStatus() { return status; }
}

// Payment.java
import java.util.*;

public abstract class Payment {
    protected double amount;
    protected PaymentStatus status;
    protected Date timestamp;
    public Payment(double amt) { this.amount = amt; this.status = PaymentStatus.PENDING; this.timestamp = new Date(); }
    public abstract boolean initiateTransaction();
}

// Cash.java
public class Cash extends Payment {
    public Cash(double amt) { super(amt); }
    public boolean initiateTransaction() {
        status = PaymentStatus.COMPLETED;
        System.out.println("Cash payment of $" + amount + " completed.");
        return true;
    }
}

// CreditCard.java
public class CreditCard extends Payment {
    public CreditCard(double amt) { super(amt); }
    public boolean initiateTransaction() {
        status = PaymentStatus.COMPLETED;
        System.out.println("Credit card payment of $" + amount + " completed.");
        return true;
    }
}

// ParkingLot.java
import java.util.*;

public class ParkingLot {
    private static ParkingLot instance = null;
    public ParkingRate rate = new ParkingRate();
    private Map<Integer, ParkingSpot> spots = new LinkedHashMap<>();
    private Map<Integer, ParkingTicket> tickets = new HashMap<>();
    private List<DisplayBoard> boards = new ArrayList<>();

    private ParkingLot() {}

    public static ParkingLot getInstance() {
        if (instance == null) instance = new ParkingLot();
        return instance;
    }

    public void addSpot(ParkingSpot s) { spots.put(s.getId(), s); }
    public void addDisplayBoard(DisplayBoard b) { boards.add(b); }
    public ParkingSpot getSpot(int id) { return spots.get(id); }
    public void freeSlot(int id) {
        ParkingSpot s = spots.get(id);
        if (s != null) s.removeVehicle();
    }

    public Collection<ParkingSpot> getAllSpots() { return spots.values(); }
    public ParkingTicket parkVehicle(Vehicle v) {
        for (ParkingSpot s : spots.values()) {
            if (s.isFree() && canFit(v, s)) {
                s.assignVehicle(v);
                ParkingTicket t = new ParkingTicket(s.getId(), v);
                tickets.put(t.getTicketNo(), t);
                return t;
            }
        }
        System.out.println("Sorry, parking lot is full. New cars cannot be parked.");
        return null;
    }

    private boolean canFit(Vehicle v, ParkingSpot s) {
        if (v instanceof Motorcycle && s instanceof MotorcycleSpot) return true;
        if ((v instanceof Truck || v instanceof Van) && s instanceof Large) return true;
        if (v instanceof Car && (s instanceof Compact || s instanceof Handicapped)) return true;
        return false;
    }
}

// Driver.java
public class Driver {
    public static void main(String[] args) throws InterruptedException {
        // -------------- SYSTEM INITIALIZATION --------------
        System.out.println("\n====================== PARKING LOT SYSTEM DEMO ======================\n");

        ParkingLot lot = ParkingLot.getInstance();
        lot.addSpot(new Handicapped(1));
        lot.addSpot(new Compact(2));
        lot.addSpot(new Large(3));
        lot.addSpot(new MotorcycleSpot(4));

        DisplayBoard board = new DisplayBoard(1);
        lot.addDisplayBoard(board);

        Entrance entrance = new Entrance(1);
        Exit exit = new Exit(1);

        // ----------------- SCENARIO 1: CUSTOMER ENTERS, PARKS -----------------
        System.out.println("\n→→→ SCENARIO 1: Customer enters and parks a car\n");

        Vehicle car = new Car("KA-01-HH-1234");
        System.out.println("-> Car " + car.getLicenseNo() + " arrives at entrance");
        ParkingTicket ticket1 = entrance.getTicket(car);

        System.out.println("-> Updating display board after parking:");
        board.update(lot.getAllSpots());
        board.showFreeSlot();

        // ----------------- SCENARIO 2: CUSTOMER EXITS AND PAYS -----------------
        System.out.println("\n→→→ SCENARIO 2: Customer exits and pays\n");

        System.out.println("-> Car " + car.getLicenseNo() + " proceeds to exit panel");
        Thread.sleep(1500); // Simulate parking duration (1.5 sec)
        exit.validateTicket(ticket1);

        System.out.println("-> Updating display board after exit:");
        board.update(lot.getAllSpots());
        board.showFreeSlot();

        // --------- SCENARIO 3: FILLING LOT AND REJECTING ENTRY IF FULL ---------
        System.out.println("\n→→→ SCENARIO 3: Multiple customers attempt to enter; lot may become full\n");

        // Vehicles arriving
        Vehicle van = new Van("KA-01-HH-9999");
        Vehicle motorcycle = new Motorcycle("KA-02-XX-3333");
        Vehicle truck = new Truck("KA-04-AA-9998");
        Vehicle car2 = new Car("DL-09-YY-1234");

        System.out.println("-> Van " + van.getLicenseNo() + " arrives at entrance");
        ParkingTicket ticket2 = entrance.getTicket(van);

        System.out.println("-> Motorcycle " + motorcycle.getLicenseNo() + " arrives at entrance");
        ParkingTicket ticket3 = entrance.getTicket(motorcycle);

        System.out.println("-> Truck " + truck.getLicenseNo() + " arrives at entrance");
        ParkingTicket ticket4 = entrance.getTicket(truck);

        System.out.println("-> Car " + car2.getLicenseNo() + " arrives at entrance");
        ParkingTicket ticket5 = entrance.getTicket(car2);

        System.out.println("-> Updating display board after several parkings:");
        board.update(lot.getAllSpots());
        board.showFreeSlot();

        // Try to park another car (lot may now be full)
        Vehicle car3 = new Car("UP-01-CC-1001");
        System.out.println("-> Car " + car3.getLicenseNo() + " attempts to park (should be denied if lot is full):");
        ParkingTicket ticket6 = entrance.getTicket(car3);

        board.update(lot.getAllSpots());
        board.showFreeSlot();

        System.out.println("\n====================== END OF DEMONSTRATION ======================\n");
    }
}


```

```
</details>

---

<details>
<summary>C++</summary>

```cpp
cout << "Hello from C++" << endl;
```
</details>


---

<details>
<summary>Javascript</summary>

```javascript
console.log("Hello from JavaScript");
```
</details>

---

<details>
<summary>Python</summary>

```python
print("Hello from Python")
```
</details>

---


