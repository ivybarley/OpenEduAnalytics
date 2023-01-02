# Data
> Feel free to generate your own test data that will suit the new package you are creating. When generating new test data, it is important to make sure that it aligns with existing data or new data you plan to create so it becomes easier to join the tables and create relationships for Power BI visualization. For example, using the same students and same schools. To make this process seamless, we recommend integrating OEA standardized schemas. Common education data standards like Caliper, Ed-Fi and SIF allow for data solutions to be built on a common analytical foundation and for a ‘plug and play’ approach to combining data from multiple sources.  [Learn more about how to integrate OEA schemas in your new module](https://github.com/microsoft/OpenEduAnalytics/tree/main/schemas).

Below is the data dictionary for this Learning Analytics package.

|Table Name   |Column Name        |Column Type  |Column Description  |
|-----------|-------------------|-------------------|-------------|
|**dim_Date** | Date     |Date |Date (Primary Key) |
| | Year     |Integer |Year |
| | Month     |Integer |Month |
| | Month of School Year     | Integer |Month of school year |
| | Week of Year     |Integer |Week of the year |
|**dim_School** | SchoolID     | |   |
|  | SchoolName     | |   |
|  | Country     | |   |
|  | Latitude     | |   |
|  | Longitude     | |   |
|**dim_Course** |      | |   |
|  |      | |   |
|  |      | |   |
|**dim_Section** | SectionID     | String| Section ID (Primary Key) |
|  |  SectionName   |String | Name of the section |
|  | SectionStartDate     | Date |   |
|  | SectionEndDate    | Date |    |
|  | CalendarCycle     | |   |
|**dim_Instructor** |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|**dim_Student** |  StudentId_external_pseudonym    |String |Hashed external student ID (from the Insights AAD User table) |
|  | Surname     |String |Surname of student |
|| GivenName     |String |First name of student|
|            | MiddleName   |String    |Middle name of student |   
|            | PersonRole   |String    |Role of person |    
|  | StudentGrade     |String |Grade level of student |
|  | SchoolName    |String |Name of the school the student attends  |
|**dim_Meeting** | meetingId     |String |Meeting ID  |
|  | meetingStartDateTime    |DateTime |DateTime |
|  | meetingEndDateTime    |DateTime |Meeting end date and time (from Graph data) |
|  | SectionId    |String |Section ID |
|  |      | |   |
|**dim_AssignmentStatus** |      | |   |
|  |      | |   |
|**dim_Assignment** |      | |   |
|  |      | |   |
|  |      | |   |
|**dim_SignalType** |      | |   |
|  |      | |   |
|  |      | |   |
|**fact_Enrollment** |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|**fact_MeetingAttendance** |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|**fact_Assignment** |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|  |      | |   |
|**fact_Activity** |  SignalType    |String |Type of signal for a student in a section |
|  | StartTime     |DateTime |Signal action time |
|  | SignalId   |String |Unique ID per student signal |
|  | AppName    |String |Application used: Assignments, SharePoint Online, etc |
|  | StudentId_external_pseudonym     |String |Hashed external student ID (from the Insights AAD User table) |
|  | MeetingSessionId     |String |Meeting Session ID, unqiue per section per meeting |
|  | Date    |Date |Date of activity |
|  |      | |   |
|  |      | |   |



|**studentattendance_lookup** | Student_id     | String | Student id |
|  | school_year     |Integer |School year |
|  | studentId_internal_pseudonym    |String |Hashed internal student ID (from the Insights Person table) |
|**studentattendance_pseudo** | id     | Integer | ID |
|  | studentId_pseudonym    |String |Hashed student ID |
|  | school_year     |Integer |School year |
|  | school_id     |String |School ID |
| |  attendance_date    | DateTime| Date of attendance |
| |  all_day    | String | Whether the student attended all day |
| |  Period    | Integer| Period |
| |  section_id    | String| Section ID|
| | AttendanceCode     | String| P for present and A for absent |
| | PresenceFlag     | Integer| 1 for present and 0 for absent |
| |  attendance_status    | String| Whether the student attended class |
| | attendance_type     | String | Type of attendance|
| | attendance_sequence     |String |Sequence of attendance |
