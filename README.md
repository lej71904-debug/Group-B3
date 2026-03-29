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

The model centers around the Event entity, which represents a specific live music show occurring at a venue on a particular date and time. Each event includes attributes such as the event date, advertised start time, age policy for that night, and whether the event is ticketed. Every event is hosted at a single venue and is managed by two staff members: one assigned as the event coordinator and another assigned as a backup coordinator.

The Venue entity stores information about locations that host events, including the venue name, address, phone number, capacity, age policy, and partner status with LMC. Venues may have relationships with other venues in the LMC network, such as shared ownership or equipment partnerships. Because a venue can be affiliated with many other venues and affiliations involve two venues, we created the VenueAffiliation associative entity. This table records the two venues involved, the type of affiliation, and the start and end dates of the relationship so that historical affiliations can be tracked.

Another key entity in the model is Artist, which represents bands or solo performers that play at events. Because each event may feature multiple artists and each artist can perform at many events, a many-to-many relationship exists between Artist and Event. This relationship is resolved through the ArtistBooking associative entity. The ArtistBooking table records which artists are performing at which events, the format of the performance, and the artist’s slot order (such as opener or headliner).

The model also tracks customers and ticket purchases. The Customer entity stores information about individuals who purchase tickets, including their name, email, and phone number. Customers may purchase multiple tickets for different events, so there is a one-to-many relationship between Customer and Ticket. The Ticket entity records information about each ticket purchase, including the ticket price, ticket type, purchase date, and the event associated with the ticket.

LMC also works with vendors who provide services or products at events, such as merchandise stands or food vendors. Vendors are represented by the Vendor entity, which stores information such as vendor name, contact information, and product type. Because vendors can participate in multiple events and events can include multiple vendors, a many-to-many relationship exists between Event and Vendor. This relationship is implemented through the EventVendors associative entity, which also records the booth location assigned to each vendor at an event.

Another important component of the model is the management of production equipment and other resources used during events. ResourceType represents categories of resources (for example sound systems, lighting kits, or microphones), and includes pricing rates for both partner and non-partner venues. ResourceItem represents individual physical items belonging to each resource type, each with a unique inventory ID and condition rating. Resources are assigned to events through the ResourceAllocation associative entity, which records the event, the specific resource item used, and the planned load-in and load-out times as well as the actual return time.

Finally, the Staff entity stores information about LMC employees who help coordinate events. Staff members can manage multiple events, which is why the Event table includes references to the coordinator and backup coordinator.

Together, these entities and relationships allow the database to accurately track venues, artists, events, ticket sales, vendors, and resource allocations involved in LMC’s live music operations.



## Data Dictionary:

## Queries:

## Database Information:
Name of the database: mb_B3
