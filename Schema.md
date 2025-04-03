Проекты (Project)
-----------------
- ID (PK, int, autoincrement)
- Name (varchar(255), not null)
- StartDate (datetime, not null)
- EndDate (datetime, not null)
- BasePlan (decimal(18,2), not null)
- ShiftedPlan (decimal(18,2), not null)
- Fact (decimal(18,2), not null)
- AssignedForemanID (FK → Users.ID, int, not null)

Месячные планы (MontlyPlan)
---------------------------
- ID (PK, int, autoincrement)
- ProjectID (FK → Project.ID, int, not null)
- Name (varchar(255), not null)
- StartDate (datetime, not null)
- EndDate (datetime, not null)
- BasePlan (decimal(18,2), not null)
- ShiftedPlan (decimal(18,2), not null)
- Fact (decimal(18,2), not null)

Дневные планы (DailyPlan)
-------------------------
- ID (PK, int, autoincrement)
- MontlyPlanID (FK → MontlyPlan.ID, int, not null)
- Date (datetime, not null)
- BasePlan (decimal(18,2), not null)
- ShiftedPlan (decimal(18,2), not null)
- Fact (decimal(18,2), not null)

Работы (Work)
-------------
- ID (PK, int, autoincrement)
- Name (varchar(255), not null)
- BasePlan (decimal(18,2), not null)
- ShiftedPlan (decimal(18,2), not null)
- Fact (decimal(18,2), not null)
- AssignedBuilderID (FK → Users.ID, int, not null)
- ImageUrl (varchar(255), not null)

Пользователи (User)
-------------------
- ID (PK, int, autoincrement)
- FirstName (varchar(100), not null)
- LastName (varchar(100), not null)
- Patronymic (varchar(100))
- Login (varchar(50), not null, unique)
- Password (varchar(255), not null)
- Role (int, not null)

Связи работ с планами
---------------------
- Project_Work (many-to-many)
  - ProjectID (FK → Project.ID, int, not null)
  - WorkID (FK → Work.ID, int, not null)
  - Primary key (ProjectID, WorkID)

- MontlyPlan_Work (many-to-many)
  - MontlyPlanID (FK → MontlyPlan.ID, int, not null)
  - WorkID (FK → Work.ID, int, not null)
  - Primary key (MontlyPlanID, WorkID)

- DailyPlan_Work (many-to-many)
  - DailyPlanID (FK → DailyPlan.ID, int, not null)
  - WorkID (FK → Work.ID, int, not null)
  - Primary key (DailyPlanID, WorkID)