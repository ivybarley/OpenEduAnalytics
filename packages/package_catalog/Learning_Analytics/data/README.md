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
|**dim_School** | SchoolID     | String | School ID (Primary Key) |
|  | SchoolName     | String | Name of school  |
|  | Country     | String | Country  |
|  | Latitude     | String | Latitude  |
|  | Longitude     | String | Longitude  |
|**dim_Course** | CourseID     | String | Course ID (Primary Key)  |
|  |  CourseName    | String | Name of course  |
|  |  CourseGradeLevel    | String | Grade level of course  |
|**dim_Section** | SectionID     | String| Section ID (Primary Key) |
|  |  SectionName   |String | Name of the section |
|  | SectionStartDate     | Date |  Section start date |
|  | SectionEndDate    | Date | Section end date   |
|  | CalendarCycle     | String | Calendar cycle  |
|**dim_Instructor** | InstructorID     | String | Instructor ID (Primary Key)  |
|  |  GivenName    | String | First name of instructor  |
|  |   MiddleName   | String | Middle name of instructor  |
|  |   Surname   | String | Surname of instructor  |
|**dim_Student** |  StudentID   |String | Student ID (Primary Key)|
|  | GivenName     |String |First name of student |
|  | MiddleName     |String |Middle name of student|
|  | Surname   |String    |Surname of student |   
|  | UPN   |String    |User principal name |    
|  | DoB     |Date |Date of birth |
|  | Address    |String |Address of student  |
|**dim_Meeting** | MeetingID     |String |Meeting ID (Primary Key) |
|  | MeetingType    | String | Type of meeting |
|  | StartTime    |DateTime |Meeting start date and time |
|  | EndTime    |DateTime |Meeting end date and time |
|  | MeetingDuration     | Integer | Duration of meeting  |
|**dim_AssignmentStatus** |  AssignmentStatusID    | String | Assignment status ID (Primary Key)  |
|  | AssignmentStatus     | String | Assignment status  |
|**dim_Assignment** |  AssignmentID    | String |  Assignment ID (Primary Key) |
|  | AssignmentDate     | DateTime | Date and time assignment was given  |
|  | DueDate     | DateTime | Date and time assignment is due  |
|**dim_SignalType** | SignalTypeID     | String |  Signal type ID (Primary Key) |
|  | SignalCategory     | String |  Signal category |
|  |  SignalType    | String | Signal type  |
|**fact_Enrollment** |  EnrollmentID    | String | Enrollment ID (Primary Key)  |
|  | SchoolID     | String | School ID  |
|  |  CourseID    | String |  Course ID |
|  |  SectionID   | String |  Section ID |
|  |  InstructorID    | String | Instructor ID   |
|  |  StudentID    | String | Student ID  |
|  |   EntryDate   | Date | Date of entry  |
|  |  ExitDate    | Date | Date of exit  |
|**fact_MeetingAttendance** |  MeetingAttendanceID    | String | Meeting attendance ID (Primary Key)  |
|  | SchoolID     | String | School ID  |
|  |  CourseID    | String |  Course ID |
|  |  SectionID   | String |  Section ID |
|  |  InstructorID    | String | Instructor ID   |
|  |  StudentID    | String | Student ID   |
|  |  MeetingID    | String | Meeting ID  |
|  |  JoinTime    | DateTime | Date and time of joining meeting  |
|  |  LeaveTime    | DateTime | Date and time of leaving meeting   |
|  |  AttendanceTime_sec    | Integer | Time in attendance (in seconds)  |
|**fact_Assignment** |  AssignmentDetailID    | String| Assignment detail ID (Primary Key) |
|  | AssignmentID     | String |   |
|  | SchoolID     | String | School ID  |
|  |  CourseID    | String |  Course ID |
|  |  SectionID   | String |  Section ID |
|  |  InstructorID    | String | Instructor ID   |
|  |  StudentID    | String | Student ID   |
|  |  AssignmentStatusID    | String | Assignment status ID  |
|  |  AssignedDate    | DateTime |  Date and time assignment was given |
|  |  DueDate    | DateTime |  Date and time assignment is due |
|  |  Grade    | Integer | Student grade  |
|**fact_Activity** |  ActivityID    |String |Activity ID (Primary Key) |
|  | SchoolID     | String | School ID  |
|  |  CourseID    | String |  Course ID |
|  |  SectionID   | String |  Section ID |
|  |  InstructorID    | String | Instructor ID   |
|  |  StudentID    | String | Student ID   |
|  | SignalTypeID    |String | Signal Type ID |
|  | ActivityDate    | DateTime | Date of activity  |
|  | StartTime     | DateTime | Date and time the activity started  |
