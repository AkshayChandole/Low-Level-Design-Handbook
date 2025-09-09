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

