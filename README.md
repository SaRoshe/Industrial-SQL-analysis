# Industrial-SQL-analysis

### Project Overview
This is a data analysis of a manufacturing tracking system, which:
Monitors waste and categorizes it.
Tracks operational stops and their causes.
Logs production orders and operations.
Associates machines and sites with production and waste data.

### Data Sources
Data sources are 10 tables.
- Orders: This table consists of the orders of the production and is one of the main tables.
- Operation: This table consists of the description of each order.
- Machine: This table consists of the data of the machines are used in each order's production.
- Site: This table consits of the data of the sites which operations are happening in.
- Stop: This table consists of the stop rules of the orders. 
- StopCategory: This table consists of the category of the diffrent stop rules in the operation process.
- StopCause: This table consists of the reasons for the stop rules.
- Waste: This table consists of the waste of each production's waste.
- WasteCategory: This table consists of the category of the diffrent waste that are produced in the operation process.
- WasteCause: This table consists of the reasons for the waste which are produced.

### Entities and Attributes

WasteCategory
Attributes:
- WasteCategoryID (Primary Key)
- WasteCategoryDescription

WasteCause
Attributes:
WasteCauseID (Primary Key)
WasteCauseDescription
WasteCategoryID (Foreign Key referencing WasteCategory)

Waste
Attributes:
OrderID (Foreign Key referencing Orders)
WasteCauseID (Foreign Key referencing WasteCause)
WasteAmount

Orders
Attributes:
OrderID (Primary Key)
MachineID (Foreign Key referencing Machine)
Start
End

Operation
Attributes:
OrderID (Foreign Key referencing Orders)
OperationID (Primary Key)
ProductionAmount

Stop
Attributes:
OrderID (Foreign Key referencing Orders)
StopID (Primary Key)
StopStart
StopEnd
StopCauseID (Foreign Key referencing StopCause)

StopCause
Attributes:
StopCauseID (Primary Key)
StopCauseDescription
StopCategoryID (Foreign Key referencing StopCategory)

StopCategory
Attributes:
StopCategoryID (Primary Key)
StopCategoryDescription

Machine
Attributes:
MachineID (Primary Key)
SiteID (Foreign Key referencing Site)
ProductLineDeviceNameEn

Site
Attributes:
SiteID (Primary Key)
ProductSiteNameEn


### Relationships

WasteCategory to WasteCause
One-to-Many (WasteCategoryID is referenced by WasteCause).

WasteCause to Waste
One-to-Many (WasteCauseID is referenced by Waste).

Orders to Waste
One-to-Many (OrderID is referenced by Waste).

Orders to Stop
One-to-Many (OrderID is referenced by Stop).

StopCause to Stop
One-to-Many (StopCauseID is referenced by Stop).

StopCategory to StopCause
One-to-Many (StopCategoryID is referenced by StopCause).

Orders to Operation
One-to-Many (OrderID is referenced by Operation).

Machine to Orders
One-to-Many (MachineID is referenced by Orders).

Site to Machine
One-to-Many (SiteID is referenced by Machine).

