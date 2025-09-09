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
##### Primary actors -
  - **Customer:** Parks their vehicle, obtains a parking ticket, pays the parking fee, and exits the parking lot.

##### Secondary actors -
  - **Admin:** Manages system resources, such as parking spots, entry/exit panels, and pricing. Also handles account and system configuration.

### [Use cases](#use-cases)
##### Admin -
  - **Add a parking spot:** To add a new parking spot, specify spot type (accessible, compact, large, motorcycle) and location (e.g., floor, section).
  - **Remove the parking spot:** Remove it from the system if it is no longer available (due to maintenance or repurposing).
  - **Update the parking spot:** This is to update the details of an existing parking spot, such as changing its type or status (e.g., available/unavailable).
  - **Add/modify rate:** To configure or change the pricing rates for durations, vehicles, or parking spot types.
  - **Update the account:** To update the admin or agent account details and manage payment information or permissions.
  - **Login/Logout:** To securely log in or out of the admin or agent account to access system features.
  - **View the account:** To view account details such as payment status, outstanding balances, or account activity history.
