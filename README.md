# MIST4610 Project 1 Group B3

## Team Name: 
47114 Group B3

## Team Members:
1. Landon Johnson
2. Yash Kirtane
3. Chris Ennis
4. Charan Nuthalapati
5. Lawrence Carpenter

## Problem Description:
The objective of this project is to design and implement a relational database that models the operations of The Live Music Circuit (LMC). LMC is responsible for coordinating live music events, managing venue partnerships, scheduling artists, and allocating production resources needed for shows.

The central entity in the model is the Event, which represents a specific live performance occurring at a venue on a given date and time. Each event is associated with a venue, includes one or more artists performing, and is managed by designated staff members. Events may also involve vendors selling products and customers purchasing tickets.

The database must capture key relationships between the different entities involved in organizing and running these events. These include relationships between venues and their affiliations with other venues, artists and their bookings for events, customers and their ticket purchases, and vendors participating in events. Additionally, the system must track production resources and equipment that LMC allocates to events, including scheduling details such as load-in and load-out times.

By building this relational database, we can store structured data about LMC’s operations, populate the system with sample data, and run queries that provide valuable insights. These insights may include information about event scheduling, ticket sales, vendor participation, artist bookings, and resource usage. Ultimately, the database allows LMC to manage its operations more efficiently and make informed decisions regarding its live music events.

## Data Model:
Our data model represents the operations of The Live Music Circuit (LMC), a company that coordinates live music performances, venue partnerships, and production resources for shows in and around Athens, Georgia.

The model centers around the Event entity, which represents a specific live music show, community event, or test night occurring at a venue on a particular date and time. Each event includes attributes such as the event date, advertised start time, age policy for that night, and whether the event is ticketed. Every event is hosted at a single venue and is managed by two staff members: one assigned as the event coordinator and another assigned as a backup coordinator.

The Venue entity stores information about locations that host events, including the venue name, address, phone number, capacity, age policy, and partner status with LMC. Venues may have relationships with other venues in the LMC network, such as shared ownership or equipment partnerships. Because a venue can be affiliated with many other venues and affiliations involve two venues, we created the VenueAffiliation associative entity. This table records the two venues involved, the type of affiliation, and the start and end dates of the relationship so that historical affiliations can be tracked.

Another key entity in the model is Artist, which represents bands or solo performers that play at events. Because each event may feature multiple artists and each artist can perform at many events, a many-to-many relationship exists between Artist and Event. This relationship is resolved through the ArtistBooking associative entity. The ArtistBooking table records which artists are performing at which events, the format of the performance, and the artist’s slot order (such as opener or headliner).

The model also tracks customers and ticket purchases. The Customer entity stores information about individuals who purchase tickets, including their name, email, and phone number. Customers may purchase multiple tickets for different events, so there is a one-to-many relationship between Customer and Ticket. The Ticket entity records information about each ticket purchase, including the ticket price, ticket type, purchase date, and the event associated with the ticket.

LMC also works with vendors who provide services or products at events, such as merchandise stands or food vendors. Vendors are represented by the Vendor entity, which stores information such as vendor name, contact information, and product type. Because vendors can participate in multiple events and events can include multiple vendors, a many-to-many relationship exists between Event and Vendor. This relationship is implemented through the EventVendors associative entity, which also records the booth location assigned to each vendor at an event.

Another important component of the model is the management of production equipment and other resources used during events. ResourceType represents categories of resources (for example sound systems, lighting kits, or microphones), and includes pricing rates for both partner and non-partner venues. ResourceItem represents individual physical items belonging to each resource type, each with a unique inventory ID and condition rating. Resources are assigned to events through the ResourceAllocation associative entity, which records the event, the specific resource item used, and the planned load-in and load-out times as well as the actual return time.

Finally, the Staff entity stores information about LMC employees who help coordinate events. Staff members can manage multiple events, which is why the Event table includes references to the coordinator and backup coordinator.

Together, these entities and relationships allow the database to accurately track venues, artists, events, ticket sales, vendors, and resource allocations involved in LMC’s live music operations.

<img width="1305" height="1237" alt="FinalDataModel" src="https://github.com/user-attachments/assets/2c7648a7-0f65-4d97-a985-cc4afb6f2a50" />

## Data Dictionary:
<img width="768" height="592" alt="Venue" src="https://github.com/user-attachments/assets/916eb66d-38b4-4455-a55d-8804374a68f8" />
<img width="760" height="546" alt="VenueAffilitation" src="https://github.com/user-attachments/assets/824b54c3-7e1f-49cb-8731-633525c40e25" />
<img width="768" height="678" alt="Event" src="https://github.com/user-attachments/assets/8aeacf47-b373-40c8-ac5e-c51790583e86" />
<img width="761" height="513" alt="Staff" src="https://github.com/user-attachments/assets/6a6980a8-e37a-4beb-9740-be82eb371d7f" />
<img width="767" height="411" alt="Artist" src="https://github.com/user-attachments/assets/b23e2d7c-a00d-4007-8824-bbb2e362b150" />
<img width="757" height="457" alt="ArtistBooking" src="https://github.com/user-attachments/assets/c22c03af-f296-4094-b35b-f8d1522d9d6f" />
<img width="752" height="447" alt="Customer" src="https://github.com/user-attachments/assets/1de77bf4-1d07-4d4d-a084-091b501898b8" />
<img width="767" height="577" alt="Ticket" src="https://github.com/user-attachments/assets/b7549939-07ac-4f3c-b61e-82165b078606" />
<img width="781" height="456" alt="Vendor" src="https://github.com/user-attachments/assets/87f58200-80e7-4a8b-b63a-82a8804ebdc1" />
<img width="740" height="390" alt="EventVendors" src="https://github.com/user-attachments/assets/5ce3a3ea-0ece-4a35-9bb5-b264c4f67bac" />
<img width="768" height="442" alt="ResourceType" src="https://github.com/user-attachments/assets/2e78d97d-2b5f-4aac-b0a5-494bda866602" />
<img width="747" height="568" alt="ResourceAllocation" src="https://github.com/user-attachments/assets/462ee5ad-50d8-49aa-812a-b334c94f22e1" />
<img width="751" height="355" alt="ResourceItem" src="https://github.com/user-attachments/assets/79e67303-ecab-45b8-8a1b-8ca649b22d25" />


## Queries:

## Database Information:
Name of the database: mb_B3
