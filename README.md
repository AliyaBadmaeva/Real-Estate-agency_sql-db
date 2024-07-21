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

<p align="center">
  <img width="524" height="536" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Users.jpg">
</p>

The type of relationship between the tables “Real Estate Objects” and “Object Parameters” is “one-to-one”; the table “Object Parameters” is a reference book for the table “Real Estate Objects”. Each object has its own specific parameters. The “Object Parameters id” domain of the “Real Estate Objects” table is a foreign key that establishes a relationship between tables and refers to the primary key “Object Parameters id” of the “Object Parameters” table.

<p align="center">
  <img width="502" height="812" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Object_parameters.jpg">
</p>

In the same way, the type of relationship between the “Real Estate Objects” and “Object Address” tables is “one-to-one”; the “Object Address” table is a reference for the “Real Estate Objects” table. Each object can have one address. The “Object Address id” domain of the “Real Estate Objects” table is a foreign key that establishes a relationship between tables and refers to the primary key “Object Address id” of the “Object Address” table.

<p align="center">
  <img width="266" height="808" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Object_addresses.jpg">
</p>

In addition, the type of relationship between the “Real Estate Objects” and “Documents for Sale” tables is “one-to-one”; the “Documents for Sale” table is a reference for the “Real Estate Objects” table. Each object can have one package of documents. The “Object id” domain of the “Documents for Sale” table is a foreign key that establishes a relationship between the tables and refers to the primary key “Object id” of the “Real Estate Objects” table.

<p align="center">
  <img width="500" height="786" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Documents_for_sale.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Photo” tables is “one-to-many”. There can be only one apartment in one photo, while one apartment can have many photos, so a foreign key has been added to the “Photo” table - the “Object id” domain, which refers to the “Object id” of the “Real Estate Objects” table. At the same time, the “Path to Photo” domain is a link that indicates the path to the photo on the computer; each link must be unique, because different photos cannot have the same link.

<p align="center">
  <img width="468" height="418" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Photo.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Sales” tables is “one-to-one”. The "Object id" domain of the Sales table is a foreign key that establishes a relationship between tables and refers to the "Object id" primary key of the "Real Estate Objects" table.

<p align="center">
  <img width="266" height="808" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Sales.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Requests for Viewing” tables is “one-to-many”. For one application, you can view only one apartment, while one apartment can have many applications, so a foreign key has been added to the “Requests for Viewing” table - the “Object id” domain, which refers to the “Object id” of the “Real Estate Objects” table. At the same time, the “Path to Photo ” domain is a link that indicates the path to the photo on the computer; each link must be unique, because different photos cannot have the same link.

<p align="center">
  <img width="492" height="810" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Requests_for_Viewings.jpg">
</p>

The type of relationship between the “Real Estate Objects” and “Users” tables is “many-to-many”. One property may have several owners, and several properties may have one owner. To connect the two tables using the “many-to-many” type of relationship, a third table “Object Owners” was created, which contains the domains “Object id” and “Owner id”, which refer to the fields of the same name in the tables “Real estate objects” and “Users” . In this case, not every user is an owner, but only the one for whom the “User Type” is selected in the Domain – “Owner”.

<p align="center">
  <img width="413" height="580" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/REO_Object_Owner_Users.jpg">
</p>

The type of relationship between the “Users” and “Requests for Viewings” tables is “one-to-many”. One potential buyer can apply to view several apartments, and there can only be one potential buyer per application. A foreign key has been added to the “Requests for Viewings” table – the domain “Potencial buyer id”, which refers to the “User id” of the “Users” table. However, not every user is a buyer, but only the one for whom the “User Type” is selected in the table “Users” -> “Buyer”. Additionally, the two tables are also related by the "Agent id" domain in the "Requests for viewings" table, which is a foreign key linking to the "User id" domain. In this case, the agent is only the one for which in the Domain the “User Type” in the table “Users” is selected “Agent”..

<p align="center">
  <img width="226" height="643" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/Users_Requests_for_Viewing.jpg">
</p>

The type of relationship between the “Users” and “Sales” tables is “one-to-many”. One buyer can buy several properties; on the part of the agency, this is a sale, while one sale can mean only one buyer. The "Buyer id" domain of the Sales table is a foreign key and references the "User id" domain of the "Users" table. However, not every user is a buyer, but only the one for whom in the Domain “User Type” of the table “Users” is selected “Buyer” type.

<p align="center">
  <img width="441" height="644" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/Users_Sales.jpg">
</p>

The type of connection between the “Users” and “Passport Data” tables is “one-to-one”; the “Passport Data” table is a reference book for the “Users” table. Each user has his own passport data. The “Passport Data id” domain of the “Users” table is a foreign key that establishes a relationship between tables and refers to the primary key “Passport Data id” of the “Passport Data” table. In this case, the domain “Passport Number” is unique.

<p align="center">
  <img width="460" height="635" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/Users_Passport_Data.jpg">
</p>

The type of relationship between the “Users” and “Contact info” tables is “one-to-one”; the “Contact Info” table is a reference book for the “Users” table. Each user has their own contact information. The "Contact info id" domain of the "Users" table is a foreign key that establishes a relationship between tables and references the "Contact info id" primary key of the "Contact info" table.

<p align="center">
  <img width="428" height="259" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/Users_Contact_info.jpg">
</p>

The type of relationship between the “Users” and “Contracts with Agents” tables is “one-to-one”; the “Contracts with Agents” table is a reference book for the “Users” table. Each agent has its own specific information about him. The "Agent id" domain of the "Contracts with Agents" table is a foreign key that establishes a relationship between tables and refers to the "User id" primary key of the "Users" table. In this case, not every user is an agent, but only the one for which in the Domain “User Type” of the table "Users" is selected “Agent” type of user.

<p align="center">
  <img width="456" height="575" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/Users_Contracts_with_Agents.jpg">
</p>

The type of relationship between the “Users” and “Contract with Agency” tables is “one-to-one”. The “Client id” domain of the “Contract with Agency” table is a foreign key that establishes a relationship between tables and refers to the primary key “User id” of the “Users” table. It must be taken into account that in this case we mean only users for whom in the domain “User type” is selected as “Buyer” or “Owner”.

<p align="center">
  <img width="321" height="803" src="https://github.com//AliyaBadmaeva/Real-Estate-agency_sql-db/blob/main/Pictures/Users_Contract_with_Agency.jpg">
</p>


