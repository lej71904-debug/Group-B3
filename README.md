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
A venue can host many events over time, but each event takes place at only one venue. This relationship simply shows where events are held and lets us track all events tied to a specific venue.

Venues can also be connected to other venues through partnerships or affiliations. Since one venue can be affiliated with multiple other venues (and vice versa), this is a many-to-many relationship handled through the VenueAffiliation table, which also stores details like the type of relationship and the time period.

Each event has staff assigned as a coordinator and a backup coordinator. A staff member can work on many events, but each event only has one person in each of those roles. This helps keep track of who is responsible for running the event.

Events and artists have a many-to-many relationship because events can feature multiple artists, and artists can perform at many events. This is managed through the ArtistBooking table, which also includes extra details like performance order and format.

A customer can purchase multiple tickets, but each ticket belongs to only one customer. This makes it easy to track who bought each ticket.

Each event can have many tickets sold for it, but each ticket is tied to one specific event. This allows us to track attendance and sales for each event.

Vendors and events also have a many-to-many relationship. A vendor can participate in multiple events, and each event can have multiple vendors. The EventVendors table is used to connect them and store details like booth location.

Resource types and resource items have a one-to-many relationship. One resource type (like a category of equipment) can include many individual items, but each item belongs to only one type.

Events and resource items have a many-to-many relationship because an event can use multiple resources, and each resource item can be used at different events over time. This is handled through the ResourceAllocation table, which also tracks timing details like when items are loaded in and returned.

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
<img width="731" height="490" alt="Queries" src="https://github.com/user-attachments/assets/d7ba50b7-bb2e-4ea3-9cf3-1ca7e95744ae" />

1. Lists all artists including their ID, contact phone number, and the number of events they are booked for, ordered alphabetically by artist name.
<img width="906" height="632" alt="Query1" src="https://github.com/user-attachments/assets/7e064139-eb88-4124-b280-36d7cbb45f74" />

Query 1 allows users to see each artist’s ID, contact info, and total event bookings. A LEFT JOIN with the ArtistBooking table ensures that artists with no bookings are included, and sorting alphabetically by name helps locate artists quickly.

2. Lists all venues including their ID, name, address, capacity, and the number of events held at each, ordered alphabetically by venue name.
<img width="942" height="638" alt="Query2" src="https://github.com/user-attachments/assets/6465b55c-4ef0-44a2-85a4-c28799d67e24" />

Query 2 provides a full view of venues, including how many events are scheduled at each location. A LEFT JOIN with the Event table ensures venues without events are still listed, and alphabetical sorting makes the results easy to reference.

3. Lists all events including their ID, date, type, and venue name, filtered to only include events of specific types, ordered by event date.
<img width="922" height="598" alt="Query3" src="https://github.com/user-attachments/assets/d12c5f31-fdec-4dbe-a038-452770af487d" />

Query 3 shows each event along with its venue, including ID, date, type, and venue name. A JOIN with the Venue table retrieves venue names, and a REGEXP filter highlights specific event types, such as “Concert” or “Show,” while ordering by date helps track upcoming events.

4. Shows all tickets over $50 along with the first and last name of the customer who purchased each ticket, ordered by ticket price descending.
<img width="868" height="472" alt="Query4" src="https://github.com/user-attachments/assets/5c5ccbf2-e1a8-43e1-8708-9ce325108cec" />

Query 4 links tickets to the customers who purchased them and filters for higher-priced tickets. Sorting by ticket price in descending order helps identify premium ticket buyers and analyze revenue opportunities.

5. Shows the average ticket price for each venue whose capacity is below the overall average, ordered by average ticket price descending.
<img width="753" height="381" alt="Query5" src="https://github.com/user-attachments/assets/a5a2e7c9-6481-4c92-8595-d43211eaac38" />

Query 5 allows users to analyze pricing trends for smaller venues by calculating the average ticket price. A subquery identifies venues below the average capacity, and ordering by average price helps compare venues efficiently. 

6. Displays the total ticket revenue generated by each event, ordered from highest to lowest revenue.
<img width="767" height="632" alt="Query6" src="https://github.com/user-attachments/assets/cdf980a3-c2b5-40ca-ac83-f9f37e370599" />

Query 6 calculates total revenue per event by summing ticket prices and grouping by event. This helps identify the highest-earning events and supports revenue tracking and analysis.

7. Shows each event and the total number of tickets sold, ordered from highest to lowest.
<img width="802" height="622" alt="Query7" src="https://github.com/user-attachments/assets/956e1719-86c7-4847-a56d-023187d3bc50" />

Query 7 counts the tickets sold per event to measure popularity and demand. Sorting in descending order quickly highlights the top-performing events.

8. Shows each artist and the number of events they are booked to perform at, ordered from highest to lowest.
<img width="847" height="637" alt="Query8" src="https://github.com/user-attachments/assets/6796c15e-047e-4e59-8817-ff34762cdc25" />

Query 8 uses the ArtistBooking table to count events per artist, showing how frequently each performer is scheduled. Sorting descending identifies the most active or in-demand artists.

9. Shows each event along with the names of the staff coordinator and backup coordinator.
<img width="781" height="628" alt="Query9" src="https://github.com/user-attachments/assets/293a0d28-34bb-407a-ac26-06c500ae9f5c" />

Query 9 joins events with staff to display the main and backup coordinators. This helps track staff assignments and ensures accountability for event management.

10. Shows each event along with the types of resources allocated and the number of items for each type.
<img width="790" height="632" alt="Query10" src="https://github.com/user-attachments/assets/d5ee4c31-a037-4cdd-a8a4-35f8af0974ef" />

Query 10 combines Event, ResourceAllocation, ResourceItem, and ResourceType to display resource usage per event. Grouping by event and resource type provides a clear breakdown for planning and logistics, while ordering highlights the most frequently used resources.

## Database Information:
Name of the database: mb_B3
