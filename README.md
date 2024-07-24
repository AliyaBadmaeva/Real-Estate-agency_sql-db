# Database project for a real estate agency.

The input information of the “Real Estate Agency” database is data on the entities “Real Estate Objects”, “Users”, “Passport Data”, “Contact Info”, “Contracts with Agents”, “Contract with Agency”, “Documents for Sale”, "Object address", "Sales" (transactions), "Requests for viewings", "Object parameters", "Photo".

The output information can be considered reports (data) generated at the request of the real estate agent, as well as the results of various database queries.

## Database design

After analyzing the subject area, the following tables were identified:

1. The table **Real Estate objects** has the following fields: Object_id, Type_of_the_property, Type, Object_address_id, Object_Parameter_id, Agent_id, Transaction_type, Cost_without_extra_charge, Final_Cost, Encumbrances.

2. The table **Object parameters** has the following fields: Object_parametrs_id, Construction_year, Floor, Total_floors, Material_of_house, Number_of_rooms, Living_area_in_sq, Total_building_area_sq, Balcony_available, Bathroom_type, Number_of_Bathrooms, Bathtub, Furniture, Renovation, Closet_and_storage, Concierge.

3. The table **Object address** has the following fields: Object_address_id, Locality, Name_of_the_Locality, Street_name, Building_number, Intercome_code.

4. The table **Documents for Sale** has the following fields: Document_Package_id, Property_for_Sale_id, Information_on_family_composition, Notarised_power_of_attorney, Written_consent_of_the_spouse, Title_of_ownership, Title_of_ownership_number, Technical_certificate, Statement_of_personal_account, Comment.

5. The table **Users** has the following fields: User_id, User_type, Passport_Data_id, Contract_info_id, Creation_date.

6. The table **Contact info** has the following fields: Contact_info_id, Phone_number, Additional_phone, email.

7. The table **Passport data** has the following fields: Passport_data_id, Surname, Name, Gender, Passpor_Number, Issued_by, Date_of_issue, Registration_address.

8. The table **Contracts with agents** has the following fields: Contract_id, Agent_id, Contact_type, Contract_number, Position, Salary_per_transaction, Income_tax,Is_active, Employment_date.

9. The table **Contract with agency** has the following fields: ID_of_contract_with_Agency, Client_id, Contract_type, Contract_number, Contract_date, Validity_date_in_months, Service_cost, Paid, Payment_deadline.

10. The table **Sales** has the following fields: Sales_id, Object_id, Buyer_id, Transaction_type, Transaction_date, Contract_number, Cost_of_the_object, Prepayment_Date, Prepayment_amount, Transaction_completed, Transaction_closing_date

11. The table **Requests for viewings** has the following fields: Request_id, Object_id, Potential_Buyer_id, Agent_id, View_date.

12. The table **Object owners** has the following fields: Object_id, Owner_id.

13. The table **Photo** has the following fields: Photo_id, Object_id, Path_to_photo.

The **database model** is presented in the Real_estate_agency.mwb file (mwb - > is extension of MySQL Workbench file). In this file you can see the relationships between tables, primary keys and foreign keys that link the tables.

### Relationships between tables

The type of relationship between the “Real Estate Objects” and “Users” tables is “one-to-many”, implying “User Type” -> “Agent”. An apartment can only have one agent who sells it. In this case, one agent can sell several apartments. The "Agent id" domain of the "Real Estate Objects" table is a foreign key and refers to the "User id" domain of the "Users" table. In this case, not every user is an agent, but only the one for whom the “User Type” is selected in the Domain – “Agent”.

![Image of REO_Users](https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Users.jpg)

The type of relationship between the tables “Real Estate Objects” and “Object Parameters” is “one-to-one”; the table “Object Parameters” is a reference book for the table “Real Estate Objects”. Each object has its own specific parameters. The “Object Parameters id” domain of the “Real Estate Objects” table is a foreign key that establishes a relationship between tables and refers to the primary key “Object Parameters id” of the “Object Parameters” table.

![Image of REO_Object_parameters](https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Object_parameters.jpg)

In the same way, the type of relationship between the “Real Estate Objects” and “Object Address” tables is “one-to-one”; the “Object Address” table is a reference for the “Real Estate Objects” table. Each object can have one address. The “Object Address id” domain of the “Real Estate Objects” table is a foreign key that establishes a relationship between tables and refers to the primary key “Object Address id” of the “Object Address” table.

![Image of REO_Object_addresses](https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Object_addresses.jpg)

In addition, the type of relationship between the “Real Estate Objects” and “Documents for Sale” tables is “one-to-one”; the “Documents for Sale” table is a reference for the “Real Estate Objects” table. Each object can have one package of documents. The “Object id” domain of the “Documents for Sale” table is a foreign key that establishes a relationship between the tables and refers to the primary key “Object id” of the “Real Estate Objects” table.

<p align="center">
  <img width="500" height="786" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Documents_for_sale.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Photo” tables is “one-to-many”. There can be only one apartment in one photo, while one apartment can have many photos, so a foreign key has been added to the “Photo” table - the “Object id” domain, which refers to the “Object id” of the “Real Estate Objects” table. At the same time, the “Path to Photo” domain is a link that indicates the path to the photo on the computer; each link must be unique, because different photos cannot have the same link.

<p align="center">
  <img width="468" height="418" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Photo.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Sales” tables is “one-to-one”. The "Object id" domain of the Sales table is a foreign key that establishes a relationship between tables and refers to the "Object id" primary key of the "Real Estate Objects" table.

<p align="center">
  <img width="266" height="808" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Sales.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Requests for Viewing” tables is “one-to-many”. For one application, you can view only one apartment, while one apartment can have many applications, so a foreign key has been added to the “Requests for Viewing” table - the “Object id” domain, which refers to the “Object id” of the “Real Estate Objects” table. At the same time, the “Path to Photo ” domain is a link that indicates the path to the photo on the computer; each link must be unique, because different photos cannot have the same link.

<p align="center">
  <img width="492" height="810" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Requests_for_Viewings.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Users” tables is “many-to-many”. One property may have several owners, and several properties may have one owner. To connect the two tables using the “many-to-many” type of relationship, a third table “Object Owners” was created, which contains the domains “Object id” and “Owner id”, which refer to the fields of the same name in the tables “Real estate objects” and “Users” . In this case, not every user is an owner, but only the one for whom the “User Type” is selected in the Domain – “Owner”.

<p align="center">
  <img width="413" height="580" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/REO_Object_Owner_Users.jpg">
</p>

The type of relationship between the “Users” and “Requests for Viewings” tables is “one-to-many”. One potential buyer can apply to view several apartments, and there can only be one potential buyer per application. A foreign key has been added to the “Requests for Viewings” table – the domain “Potencial buyer id”, which refers to the “User id” of the “Users” table. However, not every user is a buyer, but only the one for whom the “User Type” is selected in the table “Users” -> “Buyer”. Additionally, the two tables are also related by the "Agent id" domain in the "Requests for viewings" table, which is a foreign key linking to the "User id" domain. In this case, the agent is only the one for which in the Domain the “User Type” in the table “Users” is selected “Agent”..

<p align="center">
  <img width="226" height="643" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/Users_Requests_for_Viewing.jpg">
</p>

The type of relationship between the “Users” and “Sales” tables is “one-to-many”. One buyer can buy several properties; on the part of the agency, this is a sale, while one sale can mean only one buyer. The "Buyer id" domain of the Sales table is a foreign key and references the "User id" domain of the "Users" table. However, not every user is a buyer, but only the one for whom in the Domain “User Type” of the table “Users” is selected “Buyer” type.

<p align="center">
  <img width="441" height="644" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/Users_Sales.jpg">
</p>

The type of connection between the “Users” and “Passport Data” tables is “one-to-one”; the “Passport Data” table is a reference book for the “Users” table. Each user has his own passport data. The “Passport Data id” domain of the “Users” table is a foreign key that establishes a relationship between tables and refers to the primary key “Passport Data id” of the “Passport Data” table. In this case, the domain “Passport Number” is unique.

<p align="center">
  <img width="460" height="635" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/Users_Passport_Data.jpg">
</p>

The type of relationship between the “Users” and “Contact info” tables is “one-to-one”; the “Contact Info” table is a reference book for the “Users” table. Each user has their own contact information. The "Contact info id" domain of the "Users" table is a foreign key that establishes a relationship between tables and references the "Contact info id" primary key of the "Contact info" table.

<p align="center">
  <img width="428" height="259" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/Users_Contact_info.jpg">
</p>

The type of relationship between the “Users” and “Contracts with Agents” tables is “one-to-one”; the “Contracts with Agents” table is a reference book for the “Users” table. Each agent has its own specific information about him. The "Agent id" domain of the "Contracts with Agents" table is a foreign key that establishes a relationship between tables and refers to the "User id" primary key of the "Users" table. In this case, not every user is an agent, but only the one for which in the Domain “User Type” of the table "Users" is selected “Agent” type of user.

<p align="center">
  <img width="456" height="575" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/Users_Contracts_with_Agents.jpg">
</p>

The type of relationship between the “Users” and “Contract with Agency” tables is “one-to-one”. The “Client id” domain of the “Contract with Agency” table is a foreign key that establishes a relationship between tables and refers to the primary key “User id” of the “Users” table. It must be taken into account that in this case we mean only users for whom in the domain “User type” is selected as “Buyer” or “Owner”.

<p align="center">
  <img width="321" height="803" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/assets/Pictures/Users_Contract_with_Agency.jpg">
</p>

## Filling out the tables

An example of filling out tables with information. The names and details of the people are fictitious.

For the table "Contact_info":

```
INSERT INTO real_estate_agency.contact_info (Contact_info_id, Phone_number, Additional_phone, email) VALUES
           (1, 89054670242, NULL, 'gringo90@mail.ru'),
           (2, 89046878104, NULL, 'arizona78_0@yandex.ru'),
           (3, 89149090942, 89062998021, ' '),
           (4, 89304699913, NULL, ' '),
           (5, 89178092411, 89061090943, 'aliqvor76@rambler.ru'),
           (6, 89012554790, NULL, ' '),
           (7, 89273509094, 89154009274, 'astronomy76@mail.ru'),
           (8, 89171572314, 89066721340, ' '),
           (9, 89156490023, NULL, 'sonya33@yandex.ru'),
           (10, 89034678910, 89155368090, ' ');
```
For the table "passport_data":
```
INSERT INTO real_estate_agency.passport_data (Passport_data_id, Surname, Name, Gender, Passpor_Number, Issued_by, Date_of_issue, Registration_address) VALUES
           (1, 'Petrov', 'Anatoliy', 'm', 15044, 'Federal Migration Service of Russia for Moscow, Arbatsky district', '2020-01-23', 'Moscow, st. Stary Arbat, 25, apt. 100'),
           (2, 'Smirnov', 'Konstantin', 'm', 25050, 'Federal Migration Service of Russia for Moscow, Novogireevo district', '2015-05-20', 'Moscow, st. Novogireevskaya, 15, apt. 101'),
           (3, 'Snegirev', 'Sergey', 'm', 25000, 'Federal Migration Service of Russia in Moscow, Perovo district', '2008-02-19', 'Moscow, Federative Avenue, 9, bldg. 2, apt. 108'),
           (4, 'Antonov', 'Michail', 'm', 34000, 'Federal Migration Service of Russia in Moscow, Tverskoy district', '2010-08-25', 'Moscow, st. Tverskaya, 21, bldg. 3, apt. 5'),
           (5, 'Yuzhnaya', 'Olga', 'f', 30902, 'Federal Migration Service of Russia for the Tomsk region in Tomsk', '2001-09-12', 'Tomsk region, Tomsk, st. Krasnoarmeyskaya, 118, apt. 54'),
           (6, 'Simonov', 'Oleg', 'm', 30942, 'Federal Migration Service of Russia in the Astrakhan region in Astrakhan', '2015-06-10', 'Astrakhan region, Astrakhan, st. Yablochkova, 26, apt. 82'),
           (7, 'Khabirov', 'Radiy', 'm', 10921, 'Federal Migration Service of Russia for the Republic of Bashkortostan in Ufa', '2022-05-08', 'Republic of Bashkortostan, Ufa, st. 50 Let Oktyabrya, 100, apt. 5'),
           (8, 'Kononov', 'Arkadiy', 'm', 20983, 'Federal Migration Service of Russia for Moscow, Ostankino district', '1999-02-25', 'Moscow, st. Academician Korolev, 30, apt. 43'),
           (9, 'Malysheva', 'Tatiyana', 'f', 15409, 'Federal Migration Service of Russia in Moscow, Babushkinsky district', '2002-12-10', 'Moscow, st. Letchika Babushkina, 13, bldg. 1, apt. 14'),
           (10, 'Markov', 'Anton', 'm', 28402, 'Federal Migration Service of Russia in Moscow, Severnoye Medvedkovo district', '2023-03-31', 'Moscow, st. Grekova, 2, apt. 28');
```
For the table "users":
```
INSERT INTO real_estate_agency.users (User_id, User_type, Passport_Data_id, Contact_info_id, Creation_date) VALUES
           (1, 'Agent', 2, 5, '2022-01-17'),
           (2, 'Owner', 1, 2, '2022-01-17'),
           (3, 'Owner', 4, 4, '2022-01-17'),
           (4, 'Owner', 3, 7, '2022-01-17'),
           (5, 'Agent', 6, 3, '2022-01-17'),
           (6, 'Owner', 5, 6, '2022-01-17'),
           (7, 'Buyer', 7, 1, '2022-01-17'),
           (8, 'Buyer', 9, 10, '2022-01-17'),
           (9, 'Owner', 10, 8, '2022-01-17'),
           (10, 'Agent', 8, 9, '2022-01-17');
```
For the table "object_address":

```
 INSERT INTO real_estate_agency.object_address (Object_address_id, Locality, Name_of_the_Locality, Street_name, Building_number, Apartment_number, Intercom_code) VALUES
           (1, 'City', 'Moscow', 'Yeniseiskaya', 13, 24, ' '),
           (2, 'City', 'Moscow', 'Tverskaya', 15, 2, '2#1234'),
           (3, 'City', 'Moscow', 'Staryy Arbat', 1, 10, '10B1022'),
           (4, 'City', 'Moscow', 'Tikhomirova', 21, 181, '181#8310'),
           (5, 'City', 'Moscow', '1st Voikovskaya', 17, 36, '36#0023');
```

For the table "object_parameters":

```
INSERT INTO real_estate_agency.object_parameters (Object_Parameters_id, Construction_year, Floor, Total_floors, Material_of_house, Number_of_rooms,
 Living_area_in_sq, Total_building_area_sq, Balcony_available, Bathroom_type, Number_of_Bathrooms, Bathtub, Furniture, Renovation, Closet_and_storage, Concierge) VALUES
           (1, 1966, 1, 7, 'Warm ceramics', 2, '42.3', '55.4', 'Balcony', 'Adjacent', 1, 'Bathtub', 'No', 'Cosmetic', 'No', 'No'),
           (2, 1980, 3, 4, 'Stone', 1, '20.4', '42.6', 'No', 'Separate', 1, 'Bathtub', 'No', 'No renovation', 'No', 'Yes'),
           (3, 1972, 5, 6, 'Wooden', 1, '25.1', '34.2', 'Balcony', 'Separate', 1, 'Shower_cabin', 'Yes', 'Designer', 'No', 'Yes'),
           (4, 2015, 10, 16, 'Frame', 3, '42.5', '58.9', 'Loggia', 'Adjacent', 1, 'Bathtub', 'Yes', 'Cosmetic', 'Closet', 'No'),
           (5, 2022, 4, 18, 'Monolithic', 2, '40.1', '46.2', 'No', 'Adjacent', 1, 'Shower', 'No', 'European-quality renovation', 'No', 'No');
```

For the table "real_estate_objects":

```
INSERT INTO real_estate_agency.real_estate_objects (Object_id, Type_of_the_property, Type, Object_address_id, Object_Parameter_id, Agect_id, Transaction_type, Cost_Without_Extra_Charge, Final_Cost, Encumbrances) VALUES
           (1, 'Apartment', 'For sale', 1, 1, 1, 'Mortgage', 10500000, 10800000, ' '),
           (2, 'Studio', 'For sale', 2, 2, 5, 'Free', 8500000, 8800000, ' '),
           (3, 'Apartment', 'For sale', 3, 4, 10, 'Free', 11000000, 11300000, ' '),
           (4, 'Apartment', 'For sale', 4, 5, 1, 'Alternative', 12000000, 12300000, ' '),
           (5, 'Studio', 'For sale', 5, 3, 1, 'Mortgage', 13100000, 13400000, ' ');
``` 

For the table "object_owners":

``` 
INSERT INTO real_estate_agency.object_owners (Object_id, Owner_id) VALUES
           (1, 6),
           (2, 2),
           (3, 3),
           (4, 9),
           (5, 4);
``` 

For the table "object_owners":

``` 
INSERT INTO real_estate_agency.documents_for_sale (Document_Package_id, Property_For_Sale_id, Information_on_family_composition, Notarised_power_of_attorney, Written_consent_of_the_spouse, Title_of_ownership, Title_of_ownership_number, Technical_certificate, Statement_of_personal_account, Comment) VALUES
        (1, 2, 'Yes', 'Not required', 'Not required', 'Purchase and Sale Agreement', 12984090, 'No', 'No', 'The deal is possible no earlier than 08.2024'),
        (2, 5, 'Not required', 'Not required', 'No', 'Extract from the Unified State Register of Real Estate', 798208930, 'No', 'No', 'The missing documents will be completed after 05/01/2025'),
        (3, 1, 'Yes', 'No', 'Not required', 'Certificate of Inheritance', 104850, 'Yes', 'Yes', ' '),
        (4, 4, 'Yes', 'Not required', 'Not required', 'Donation Agreement', 10450288572, 'No', 'No', ' '),
        (5, 3, 'Yes', 'Not required', 'No', 'Certificate of Inheritance', 8295729204, 'No', 'No', 'Husband is abroad, will arrive in June 2024');
``` 

For the table "requests_for_viewings":

``` 
INSERT INTO real_estate_agency.requests_for_viewings (Request_id, Object_id, Potential_Buyer_id, Agent_id, View_date) VALUES
           (1, 1, 7, 1, '2024-08-02 10:00:00'),
           (2, 2, 8, 5, '2024-08-04 17:30:00'),
           (3, 3, 8, 10, '2024-08-05 20:00:00'),
           (4, 5, 8, 1, '2024-08-08 13:00:00'),
           (5, 3, 7, 10, '2024-08-10 10:00:00');
``` 

For the table "photo":

``` 
INSERT INTO real_estate_agency.photo (Photo_id, Object_id, Path_to_photo) VALUES
           (1, 1, 'C:\Work\photo\DSCN1021.jpg'),
           (2, 1, 'C:\Work\photo\DSCN0930.jpg'),
           (3, 1, 'C:\Work\photo\DSCN238795.jpg'),
           (4, 1, 'C:\Work\photo\hiq90100.jpg'),
           (5, 2, 'C:\Work\photo\0000321.jpg'),
           (6, 2, 'C:\Work\photo\276645.jpg'),
           (7, 2, 'C:\Work\photo\DSCN5186.jpg'),
           (8, 3, 'C:\Work\photoо\DSCN099298.jpg'),
           (9, 3, 'C:\Work\photoо\DSCN27158.jpg'),
           (10, 4, 'C:\Work\photo\DSCN12905.jpg'),
           (11, 4, 'C:\Work\photo\DSCN2421.jpg'),
           (12, 4, 'C:\Work\photo\DSCN2430.jpg'),
           (13, 5, 'C:\Work\photo\DSCN2445.jpg'),
           (14, 5, 'C:\Work\photo\2100.jpg'),
           (15, 5, 'C:\Work\photo\Dwhi321.jpg');
``` 

For the table "contract_with_agency":

``` 
INSERT INTO real_estate_agency.contract_with_agency (ID_of_contract_with_Agency, Client_id, Contract_type, Contract_number, Contract_date, Validity_date_in_months, Service_cost, Paid, Payment_deadline) VALUES
           (1, 2, 'Search for owner', 101, '2024-07-17', 12, 15000, 15000, '2024-08-18'),
           (2, 3, 'Search for owner', 102, '2024-07-17', 12, 60000, 60000, '2024-08-18'),
           (3, 4, 'Search for owner', 103, '2024-07-17', 12, 30000, 30000, '2024-08-18'),
           (4, 6, 'Search for owner', 104, '2024-07-17', 12, 15000, 15000, '2024-08-18'),
           (5, 7, 'Search for buyer', 105, '2024-07-17', 12, 15000, 15000, '2024-08-18'),
           (6, 8, 'Search for buyer', 106, '2024-07-18', 12, 45000, 45000, '2024-08-19'),
           (7, 9, 'Search for owner', 107, '2024-07-18', 12, 15000, 15000, '2024-08-19');
``` 

For the table "contract_with_agents":

``` 
INSERT INTO real_estate_agency.contracts_with_agents (Contract_id, Agent_id, Contact_type, Contract_number, Position, Salary_per_transaction, Income_tax, Is_active, Employment_date) VALUES
           (1, 1, 'Permanent', 1001, 'Sales manager', 100000, 13, 'Yes', '2024-01-17'),
           (2, 5, 'Temporary', 1002, 'Sales manager', 100000, 13, 'Yes', '2024-01-18'),
           (3, 10, 'Temporary', 1003, 'Sales manager', 110000, 13, 'Yes', '2024-01-18');
``` 

## SQL-queries
1. Query to select all data from two table fields:

``` 
SELECT * FROM real_estate_agency.contracts_with_agents 
WHERE Position='Sales manager' AND Contract_number=1003;
```

2. Query to select all non-repeating data from one table field:

``` 
SELECT DISTINCT Contract_type FROM real_estate_agency.contract_with_agency;
``` 

3. A query to select all fields and records of a table, grouped by the value of one field, using a group condition (sections GROUP BY, HAVING) and with column headers specified in the query

``` 
SELECT `ID_of_contract_with_Agency`, `Client_id`, `Service_cost` FROM real_estate_agency.contract_with_agency 
GROUP BY `ID_of_contract_with_Agency` 
HAVING MAX(`Paid`) >= 30000;
```

4. Selecting several (not all) table fields, sorted in descending order

```
SELECT `Object_id`, `View_date` FROM real_estate_agency.requests_for_viewings ORDER BY `View_date` DESC;
```

5. Selecting an arbitrary number of table fields with the addition of a field that is the result of an arithmetic expression involving table field values:

```
SELECT `Object_id`, `Type_of_the_property`, `Transaction_type`, `Final_Cost`, (`Final_Cost` * 0.9) AS `Discount price` 
FROM real_estate_agency.real_estate_objects;
```

6. A query to select all records by an arbitrary number of table fields using the AVG aggregation function and the condition for selecting records specified in the WHERE section

```
SELECT `Transaction_type`, ROUND(AVG(`Final_Cost`),1) AS `Averange_Cost` 
FROM real_estate_agency.real_estate_objects
WHERE `Type` = 'For Sale'
GROUP BY `Transaction_type`;
```




