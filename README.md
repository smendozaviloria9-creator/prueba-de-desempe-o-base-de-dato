# prueba-de-desempe-o-base-de-dato
# Project: Work Order Management System - TechCare Solutions

**Student:** Sebastian Mendoza  
**Clan:** Cortissoz  

This project contains the relational database design and table creation scripts for the technology maintenance management system of TechCare Solutions. The model has been structured following the Third Normal Form (3NF) rules to eliminate data redundancy and ensure data integrity.

## 📁 Repository Content

*   **Database Structure:** SQL code for creating the master tables, intermediate tables, and the final transactional table.
*   **Relational Design:** Logical configuration of entities and their relationships (1:N cardinalities).

## 🛠️ Data Model (Created Tables)

1.  **riwi_cities:** Unified catalog of cities.
2.  **riwi_clients:** Company clients registry.
3.  **riwi_technicians:** List of authorized technicians.
4.  **riwi_equipment_categories:** Hardware types.
5.  **riwi_service_types:** Types of support provided.
6.  **riwi_branches:** Service locations linked to a specific city.
7.  **riwi_equipment:** Device models linked to a hardware category.
8.  **riwi_work_orders:** Main table connecting all previous data with the service date, hours spent, and cost.

## 🚀 Execution Instructions

To set up the database in your local environment (PostgreSQL / MySQL), follow these steps:

1. Open your preferred database management tool.
2. Create a new database for the project.
3. Copy and run the creation script in the following strict order:
    * First, independent catalogs are created (`riwi_cities`, `riwi_clients`, etc.).
    * Then, tables with simple dependencies (`riwi_branches`, `riwi_equipment`).
    * Finally, the transactional table (`riwi_work_orders`).

## 🔗 Diagram Code (dbdiagram.io)

If you want to view the Entity-Relationship Diagram interactively, you can paste this clean code directly into the **dbdiagram.io** web tool:

```text
Table riwi_cities {
  id int [pk]
  name varchar
}

Table riwi_branches {
  id int [pk]
  name varchar
  city_id int
}

Table riwi_clients {
  id int [pk]
  name varchar
}

Table riwi_technicians {
  id int [pk]
  name varchar
}

Table riwi_equipment_categories {
  id int [pk]
  name varchar
}

Table riwi_equipment {
  id int [pk]
  name varchar
  category_id int
}

Table riwi_service_types {
  id int [pk]
  name varchar
}

Table riwi_work_orders {
  id varchar [pk]
  client_id int
  branch_id int
  technician_id int
  equipment_id int
  service_type_id int
  service_date date
  hours int
  cost numeric
}

Ref: riwi_cities.id < riwi_branches.city_id
Ref: riwi_equipment_categories.id < riwi_equipment.category_id
Ref: riwi_clients.id < riwi_work_orders.client_id
Ref: riwi_branches.id < riwi_work_orders.branch_id
Ref: riwi_technicians.id < riwi_work_orders.technician_id
Ref: riwi_equipment.id < riwi_work_orders.equipment_id
Ref: riwi_service_types.id < riwi_work_orders.service_type_id
