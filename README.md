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
1. Shows all artists including their ID, name, and contact phone number, ordered alphabetically by artist name.

Query 1 allows users to easily view and organize all artists in the system along with their contact information. Sorting alphabetically makes it easier to locate a specific artist and maintain organized records. This is useful for administrative tasks such as contacting artists or managing artist-related data.

2. Lists all venues with their ID, name, address, and capacity.

Query 2 provides a complete overview of all venues in the system along with key details about each location. This allows users to understand venue sizes and locations, which is helpful when planning events or comparing different venues for scheduling purposes.

3. Shows all events along with the name of the venue where each event is being held.

Query 3 allows users to see where each event is taking place by linking events with their respective venues. Since the database only stores the event ID (and not a name), this query focuses on connecting each event to its venue. This is useful for organizing event logistics and ensuring events are assigned to the correct locations.

4. Displays all tickets that cost more than $50, ordered from highest to lowest price.

Query 4 helps identify higher-priced tickets, which may represent premium or high-demand events. Sorting by price in descending order makes it easy to quickly see the most expensive tickets, allowing managers to analyze pricing strategies or identify high-revenue opportunities.

5. Shows the average ticket price for each venue, but only for venues whose capacity is below the overall average venue capacity, sorted by average ticket price in descending order.

Query 5 allows users to analyze how smaller venues (below average capacity) price their tickets on average. This can help identify whether smaller venues charge higher or lower prices compared to others. Sorting by average ticket price makes it easier to compare venues and evaluate pricing strategies across different venue sizes.

6. Displays the total ticket revenue generated by each event, ordered from highest to lowest revenue.

Query 6 helps identify which events are generating the most revenue. This is useful for evaluating event performance and determining which events are the most successful financially. Sorting the results from highest to lowest revenue makes it easy to prioritize top-performing events.

7. Shows each customer along with the total number of tickets they have purchased, including only customers who have purchased at least one ticket.

Query 7 provides insight into customer purchasing activity by showing how many tickets each customer has bought. Even though each customer may only have one ticket in this database, this query demonstrates how customer engagement could be analyzed in a real-world scenario. This information can help identify active customers and support marketing or loyalty efforts.

8. Displays each artist along with the total number of events they are performing at, ordered from highest to lowest.

Query 8 allows users to see which artists are performing most frequently. This can help identify popular or highly active artists within the system. Ordering the results by number of events makes it easy to determine which artists are most involved and may require more scheduling attention or resources.

9. Shows events that have ticket prices above the overall average ticket price.

Query 9 helps identify events that are priced higher than average, which may indicate premium events or higher demand. This can be useful for analyzing pricing strategies and understanding which events are positioned as higher-value offerings.

10. Categorizes each ticket as Low, Medium, or High based on its price.

Query 10 allows users to group tickets into price categories, making it easier to analyze pricing distribution. This can help managers quickly understand how tickets are priced overall and identify trends, such as how many tickets fall into each price range. This type of categorization is useful for pricing strategy and reporting.

## Database Information:
Name of the database: mb_B3
