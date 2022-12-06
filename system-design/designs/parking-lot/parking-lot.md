# Design a Parking Lot 
## Requirements
  - The parking lot should have multiple entry/exit points
  - Customers can collect parking ticket from the entry point
  - The system should not allow more vehicles then the capacity of the parking lot. If the parking lot is full, show an error message
  - The system should support 3 types of parking spots - small, medium, large
  
## Use cases
  - Add/Remove/Edit Parking Spot
  - Create new parking ticket
  - Check if parking lot is full

## High Level Classes
  - ParkingLot
    * id, name, address
    * isFull()
  - ParkingSpot
    * id, number, location, parkingspottype, isFree
    * isSpotFree(), addNewSpot()
  - ParkingSpotType
    * type, maxcount, availablecount
  - ParkingTicket
    * ticketNumber, issuedAt, vehicleNumber, status
  - EntryGate
    * id, name, location
    * createNewTicket() 
