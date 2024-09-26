# Requirements Document - Banter Ice Cream (January 28, 2024)

# Revision History

| Name | Date | Reason for Changes | Version |
| ----------- | ----------- | ------------- | ---------- | 
| Amanda Anderson | January 29, 2024 | Create document from template and draft section 1 | 1.0 |
| Dhuruvan Anavaratha Krishnan | January 29, 2024 | Created draft for sections 2.4 and 2.5 | 1.1 |
| Yu Tang | January 29, 2024 | Created draft for sections 4.2 - 4.5 | 1.2 |
| Benjamin Osalira | January 30, 2024 | Created draft for section 3: 3.1, 3.2 and 3.3 | 1.3 |
| Justin Drastil | January 30, 2024 | Created draft for section 4.1 | 1.4 |
| Luca Bolzonello | January 30, 2024 | Edit of section 3.3 | 1.5 |
| Nolan Curtis | January 30, 2024 | Created draft for 2.1 | 1.6 |
| Tim Xu | January 30, 2024 | Created draft for 2.2 and 2.3 | 1.7 |
| Team | January 30, 2024 | Review and edit sections | 1.8 |
| Team | January 31, 2024 | Further review and change formatting | 1.9 |
| Team | February 2, 2024 | Final Review | 2.0 |
| Amanda Anderson | February 8, 2024 | Add template for sections 5-10 | 3.0 |
| Team | February 10-13, 2024 | Update document according to feedback | 3.1 |
| Amanda Anderson | February 13, 2024 | Update template for sections 5, 6 | 4.0 |
| Team | February 18, 2024 | Add content to sections 5, 6, and 8 | 4.1 |
| Amanda Anderson | March 5, 2024 | Format sections 5, 9 | 5.0 |
| Team | March 10, 2024 | Add content to sections 5, 7, 9 | 5.1 |

# 1. **Overview** <a name="overview"></a>

This document will explore an opportunity to centralize Banter Ice Cream’s internal management. First, we will discuss Banter’s business requirements and illustrate the goal of the project. Second, the document will discuss the major features, scope, and limitations of the project. Third, more context for the project will be provided such as user classes, operating environment, and constraints. Fourth, will expand on each system feature to include description, priority, functional requirements, and use cases. Fifth, will define data requirements. Sixth, will describe external interface requirements including user interfaces, hardware interfaces, software interfaces, and communication interfaces. Seventh, will discuss software quality attributes that are prioritized in the system. Eighth, will include further analysis models. Finally, there is an appendix for additional details.

These sections are outlined in the following Table of Contents.

## **Table of Contents**
1. [Overview](#overview)
2. [Business Requirements](#requirements)
   1. [Background](#background)
   2. [Business Opportunity](#opportunity)
   3. [Business Objectives](#objective)
   4. [Success Metrics](#success)
   5. [Product Vision Statement](#vision)
3. [Scope and Limitations](#scope)
   1. [Major Features](#features)
   2. [Project Scope](#project-scope)
   3. [Limitations and Exclusions](#limitations)
4. [Context Description](#context)
   1. [User Classes and Characteristics](#user-classes)
   2. [Operating Environment](#operating-environment)
   3. [Design and Implementation Constraints](#constraints)
   4. [Assumptions and Dependencies](#assumptions)
   5. [Glossary of Terms](#glossary)
   6. [References](#references)
5. [System Features](#system-features)
   1. [Scheduling and Time Tracking](#feature-1)
      - [Description and Priority](#f1-description)
      - [Functional Requirements](#f1-functional)
      - [Use Cases](#f1-usecases)
      - [Storyboards](#f1-storyboards)
      - [Sequence Diagram for Create Schedule](#f1-sequence)
      - [Swimlane for Create Schedule](#f1-swimlane)
      - [State Diagram for Shift Swap](#f1-state)
   3. [Communication and Announcement](#feature-2)
      - [Description and Priority](#f2-description)
      - [Functional Requirements](#f2-functional)
      - [Use Cases](#f2-usecases)
      - [Storyboards](#f2-storyboards)
      - [Dialog Map for Send Message](#f2-dialogmap)
   5. [Recipe Management](#feature-3)
      - [Description and Priority](#f3-description)
      - [Functional Requirements](#f3-functional)
      - [Use Cases](#f3-usecases)
      - [Storyboards](#f3-storyboards)
      - [Sequence Diagram for Storyboard 3](#f3-sequence)
      - [Swimlane for View Recipe](#f3-swimlane)
   7. [Onboarding Materials](#feature-4)
      - [Description and Priority](#f4-description)
      - [Functional Requirements](#f4-functional)
      - [Use Cases](#f4-usecases)
      - [Storyboards](#f4-storyboards)
   9. [Account Management](#feature-5)
      - [Description and Priority](#f5-description)
      - [Functional Requirements](#f5-functional)
      - [Use Cases](#f5-usecases)
      - [Storyboards](#f5-storyboards)
      - [Dialog Map for Edit Account](#f5-dialogmap)
6. [Data Requirements](#data-requirements)
   1. [Logical Data Models](#data-model)
   2. [Data Dictionary](#data-dictionary)
   3. [Reports](#data-report)
   4. [Data Integrity](#data-integrity)
7. [External Interface Requirements](#external-interfaces)
   1. [User Interfaces](#user-interfaces)
   2. [Hardware Interfaces](#hardware-interfaces)
   3. [Software Interfaces](#software-interfaces)
   4. [Communication Interfaces](#communication-interfaces)
8. [Software Quality Attributes](#quality-attributes)
9. [Analysis Models](#analysis-models)
   1. [Data Flow Diagram Level 0](#data-flow0)
   2. [Data Flow Diagram Level 1](#data-flow1)
   3. [Data Flow Diagrams Level 2](#data-flow2)
   4. [Data Flow Diagrams Level 3](#data-flow3)
10. [Appendix](#appendix)
  
# 2. Business Requirements <a name="requirements"></a>

## i. **Background** <a name="background"></a>
The client, Banter Ice Cream, wants an improvement of the software that they are using for scheduling, communication, and payroll management. Banter's current scheduling system, Homebase, is used at least once per week to check shift schedules, swap shifts, and record time worked. The problem with this current software is it lacks certain features resulting in employees having difficulty switching shifts. A feature missing is the ability for staff to view the available schedules of other employees to find open shifts. Another feature missing results in difficulties in payroll integration with Homebase. Currently the application does not summarize hours which requires the Bookkeeper to manually calculate regular, holiday, overtime, sick days, and vacation days for each employee. Basecamp is a separate system utilized by Banter Ice Cream to send staff wide announcements and news regarding the company. Having a separate piece of software to receive announcements results in Basecamp being checked infrequently, leading employees to miss messages about new ice cream flavours and ice cream deliveries between locations. Employees missing ice cream flavour announcements lowers customer satisfaction as the provided information about current ice flavours is not accurate. Employees missing messages about scheduled deliveries lowers efficiency as the employees are not prepared to unload the deliveries. The client wants a solution that will make managing finances, swapping shifts, communicating with staff, and onboarding staff easier to accomplish by having one combined app. This conglomeration of their systems will help onboard new staff as less platforms are required to be learned by employees, in addition to all onboarding material being more easily found by all employees.


## ii. **Business Opportunity** <a name="opportunity"></a>
The new system will be a single platform that combines the functionality of Homebase and Basecamp. Using one platform will improve employee engagement because they will only need to check one application for updates. Using one platform will also reduce onboarding time as new employees only need to learn one system. The new system will improve on the scheduling functionality of Homebase, including features for shift management, swapping shifts, clocking in and out, and calculating hours worked. The scheduling system will reduce scheduling errors due to incorrectly swapped shifts and will reduce payroll errors by summarizing hours according to the client's requests. The new system will also include the communication functionality of Basecamp. The communication system will improve employee knowledge of company updates and increase instances where employees are prepared for planned ice cream deliveries. The new system will also store information about Banter Ice Cream, including onboarding materials and ice cream recipes, so they are available to each employee with access. Both onboarding materials and recipe management will improve employee knowledge of Banter Ice Cream and improve onboarding experience. Improved employee knowledge, improved communication, improved onboarding, and reduced scheduling errors will result in a better customer experience and improved customer satisfaction. Overall, the new system shall result in more engaged employees, more satisfied customers, fewer payroll errors, and easier onboarding for new employees.


## iii. **Business Objectives** <a name="objective"></a>

Banter Ice Cream's new system will facilitate business growth through better internal management practices using the new system. The following objectives will all contribute to increased business growth. The methods for measuring these objectives are described in the Success Metrics section.
* Improve employee engagement by 50%.
* Improve customer satisfaction by 25%.
* Reduce time associated with payroll by 25%.
* Reduce manual errors associated with payroll by 50%.
* Reduce time associated with onboarding new employees by 25%.

The listed objectives shall be achieved within three months of release.


## iv. **Success Metrics** <a name="success"></a>

The following metrics will be used to measure the success of the system.

**Announcement Visibility**
      
- Within 3 months of release, staff's interactions with the announcements are increased by 50%. This will be measured by the number of replies, reactions, and further questions to the Manager.
      
**Customer Satisfaction**
      
- In 3 months of release, the Google reviews average score would increase by 0.5 stars in its scale of 1 to 5.
- By 6 months, the Google reviews average score would increase by 1.0 star. 

**Bookkeeping Efficiency**
   
- In 3 months of the system's release, Bookkeepers will spend 25% less time during each payroll period.
- After 6 months of release, manual errors associated with payroll would reduce by 50%.

**Onboarding New Employees**

- Within 3 months of release, new staff should take 25% less time to familiarize themselves with the system during onboarding.


## v. **Product Vision Statement** <a name="vision"></a>
The new system intends to improve communication between staff at Banter Ice Cream. This will be accomplished by reducing scheduling confusion, minimizing time spent manually calculating hours, and ensuring relevant information is passed to employees. This will be done by combining the systems that are currently used, Homebase and Basecamp, with additional features to improve the client's integration with Quickbooks. The goal of this product is to increase employee engagement with the system, streamline the creation of staff schedules, improve finance management, and improve customer satisfaction by providing accurate and up to date information.

# 3. Scope and Limitations <a name="scope"></a>

## i. **Major Features** <a name="features"></a>

To ensure Banter Ice Cream's system effectively meets the operational needs and improves internal management, the following features will be included.

**Scheduling System:**
   - Create, modify, and manage shifts through a scheduling interface.
   - Employees can swap shifts, subject to managerial approval, to accommodate personal needs while ensuring operational requirements are met.
   - Calendar views for employees and Managers to provide a clear overview of work schedules.
     
**Clock-In and Clock-Out System:**
   - Clock in at the start and clock out at the end of shifts, enabling precise tracking of work hours for all hourly employees.
   - Automatically tracks employee hours, including regular, overtime, sick days, and holidays.
   - Automatically calculate earnings, including overtime.
 
**Recipe Management System:**
   - A recipe management module that allows Managers to create, edit, and archive recipes, including full details and allergen information.
   - Front of House Staff will have access to view recipes and allergen information but not the detailed ingredients, ensuring they are informed for customer queries without access to proprietary recipe details.
   - Kitchen Staff will have access to full recipe details, including ingredient lists, preparation instructions, and allergen information, to ensure accurate preparation.
   - Historical recipe records, enabling tracking of changes over time and access to previous versions for reference or reintroduction.
  
**Communication and Announcement System:**
   - Embedding capabilities for images, videos, and PDFs in announcements and messages to enrich communication.
   - Ability to send and receive company-wide announcements and communicate about shifts changes.   
      
**Role-Based Access:**
   - Different access levels for Managers, Bookkeepers, Delivery Drivers, Front of House Staff, and Kitchen Staff, as defined in User Classes and Characteristics section of this Requirements Document.
   - Safeguard sensitive information through controlled access, ensuring privacy and security across the system.
   - Tailored interfaces and features depending on the user’s role within the company.   

**Onboarding Material Access:**
   - Grant employees access to a library of onboarding materials, such as instructional videos, directly within the system. 
   - Ability to upload onboarding materials.
  

## ii. **Project Scope** <a name="project-scope"></a>

The software being developed is a comprehensive employee management and communication system designed specifically for Banter Ice Cream. Its purpose is to consolidate existing systems Homebase and Basecamp into one centralized platform that integrates with Quickbooks, improving internal communication, scheduling efficiency, and payroll management. The anticipated benefits include better-informed employees, streamlined shift management, reduced manual errors in payroll, and an overall increase in operational efficiency. This directly aligns with the client's objectives of enhancing customer satisfaction, improving employee engagement, and facilitating business growth through better internal management practices.


## iii. **Limitations and Exclusions** <a name="limitations"></a>

**Quickbooks Integration - (Limitation)**
- Direct integration with Quickbooks was determined to be a lower priority. Therefore, we will limit this feature to implementing a summary of hours worked by each employee. The Bookkeeper can manually process this summary.

**Desktop View - (Exclusion)**
- The clients have indicated that they only want a mobile application view for the system and that the desktop view is not desired.

**Notifications - (Exclusion)**
- It has been determined with clients that notifications are not a high priority for the system.

**Inventory Management System - (Exclusion)**
- Inventory Management was mentioned as a desired feature, but it does not fit in with the rest of the system requested.

**Automated Data Migration - (Exclusion)**
- Automated Data Migration to the new system may be a difficult feature to implement. It is more practical to do manually since it’s a one-time action that only needs to happen once during onboarding to the new system.


# 4 Context Description <a name="context"></a>

## i. **User Classes and Characteristics** <a name="user-classes"></a>

When creating a centralized platform for Banter Ice Cream, understanding the diverse user classes is crucial to craft an efficient and user-centric platform that seamlessly integrates with Banter Ice Cream's operational needs.
      
**Front of House / Kitchen Managers:**
* **Characteristics:**
   * High frequency of use (daily or weekly)
   * Responsible for scheduling, training, announcements, and managing staff
   * Has a supervisory role
   * Moderate to high technical expertise
* **Requirements:**
   * Advanced scheduling functionalities (creation, editing, approval, etc)
   * Ability to create, view and edit each recipe in the recipe management feature
   * Access to training modules and documents
   * New employee account creation
   * Announcement creation and management
   * Communication channels for group or individual messaging
* **Importance:** Favored user class since there role is critical for staff management and communication

**Bookkeeper:**
* **Characteristics:**
   * Moderate frequency use (mostly during payroll periods)
   * Focus on accounting, payroll, and tracking work hours
   * High technical expertise in accounting software
* **Requirements:**
   * Clock-in/Clock-out features
   * Hours for each employee need to be summarized with overtime, holiday, etc
   * Access to employees banking information
   * Access to training modules and documents
* **Importance:** Critical for financial management (favored class during specific periods)

**Delivery Drivers:**
* **Characteristics:**
   * Use during sporadic weekly shifts
   * Main focus on clocking in/out and communication
   * May have different levels of technical expertise
* **Requirements:**
   * Clock-in/Clock-out features
   * Need to be able to view shift schedule
   * Communication channel for shift-related updates
   * Real-time schedule accessibility
   * Access to training modules and documents
* **Importance:** Frequent users which have direct impact on customer satisfaction (favored user class)
  
**Front of House Staff:**
* **Characteristics:**
   * Daily use during shifts
   * Main focus on clocking in/out, receiving updates, and managing shifts
   * May have different levels of technical expertise
* **Requirements:**
   * Clock-in/Clock-out features
   * Access to allergens from each recipe in the recipe management feature
   * Access to training modules and documents
   * Interface for shift management (Viewing, Shift Change, etc.)
   * Communication channels for shift coverage and updates
* **Importance:** Frequent users with direct impact on customer satisfaction (favored user class)

**Kitchen Staff:**
* **Characteristics:**
   * Daily use during shifts
   * Main focus on clocking in/out, receiving updates, and managing shifts
   * May have different levels of technical expertise
* **Requirements:**
   * Clock-in/Clock-out features
   * Full viewing access to each recipe in the recipe management feature
   * Access to training modules and documents
   * Interface for shift management (Viewing, Shift Change, etc.)
   * Communication channels for shift coverage and updates
* **Importance:** Frequent users with direct impact on customer satisfaction (favored user class)

**Favored User Classes:**
* **Priority Users:** Front of House / Kitchen Managers, Bookkeeper, Front of House Staff, Kitchen Staff
* **Transactional Users:** Delivery Drivers


## ii. **Operating Environment** <a name="operating-environment"></a>

The operating environment for the system is a mobile application that is compatible with both Android and iOS systems. A mobile application was chosen to allow Front of House Staff, Kitchen Staff, and Delivery Driver frequent access to the system to increase employee engagement. Each Front of House Staff, Kitchen Staff, and Delivery Driver will need to clock in and clock out during their shift. They will also need to access announcements, shift schedules, and messages.

A desktop viewable application will not be considered for the first release of the system.

## iii. **Design and Implementation Constraints** <a name="constraints"></a>

The system must adhere to the following design and implementation constraints.

**Security of Banking Information**
- Each employee can view and update their own banking information. 
- Banking information for each employee is kept private from all other employees, except Bookkeepers. 
- Bookkeepers are able to use banking information to pay employees.
- Abides by provincial and federal privacy laws.

**Number of Employees**
- The system must be able to handle 30 users accessing the system simultaneously.
- Over the system lifetime the system must not limit the number of employees.
- The system must be able to store user data about at least 70 employees.


## iv. **Assumptions and Dependencies** <a name="assumptions"></a>

The following assumptions and dependencies affect the requirements in this document.
- We assume that all employees working at Banter Ice Cream have smartphones that are capable of connecting to the internet. 
- We assume that we are able to interface with Quickbooks.


## v. **Glossary of Terms** <a name="glossary"></a>

| **Word**  | **Definition** |
| ------------- | ------------- |
|  Banter | Banter Ice Cream, an ice cream shop with two locations; in Abbotsford, BC and Chilliwack, BC. [1]|
|  Client | Banter Ice Cream |
|  Business Hours | The hours that Banter Ice Cream is open. Monday-Thursday 1-9pm, Friday 1-10pm, Saturday 12-10pm, and Sunday 12-9pm (inclusive). [1]|
|  New Employee | An employee of Banter Ice Cream that has worked at Banter for less than two weeks. |
|  Employee | An employee of Banter Ice Cream with any role listed in User Classes and Characteristics section. Equivalently, Staff or User.|
|  Staff | See Employee. |
|  User | See Employee. |
|  Manager | Front of House / Kitchen Managers as defined in User Classes and Characteristics. |

## vi. **References** <a name="references"></a>

[1] “Find Us,” Banter Ice Cream, https://www.bantericecream.com/find-us (accessed Feb. 18, 2024). 

# 5 System Features <a name="system-features"></a>
 
## i. Scheduling and Time Tracking <a name="feature-1"></a>

Scheduling and Time Tracking

### a. Description and Priority <a name="f1-description"></a>

The scheduling feature has a high priority. This is a system employees will use multiple times during their shift as well as outside of work hours to check their schedule and clock in and out. The feature allows Front of House Staff, Kitchen Staff, Delivery Drivers, and Bookkeepers to the view posted schedule, request shift swaps, and indicate availability. Managers must be able to view, create, edit, and delete schedule information. Managers and Bookkeepers should be able to see a summarized list of worked hours for each employee. 

### b. Functional Requirements <a name="f1-functional"></a>

SCH-1: The system must allow a Manager to create shifts for employees.
- **Rationale**: Ensures that Managers can effectively plan and allocate human resources to meet the operational needs of Banter Ice Cream.
- **AT-SCH-1-1**: As a Manager, create a shift in the scheduler. Verify the shift appears in the system and is visible to assigned employees.

SCH-2: The system must allow shifts to be made 2-4 weeks in advance.
- **Rationale**: Provides adequate planning horizon for both management and staff, allowing for personal and professional scheduling needs to be met.
- **AT-SCH-2-1**: As a Manager, attempt to create a shift more than 4 weeks in advance. Verify the system does not allow this.
- **AT-SCH-2-2**: Create a shift 2-4 weeks in advance and verify it is successfully added.

SCH-3: The system must allow a Manager to delete shifts from the schedule.
- **Rationale**: Facilitates operational flexibility by allowing Managers to adjust staffing needs as they change.
- **AT-SCH-3-1**: As a Manager, delete an existing shift. Verify the shift is removed from the schedule.

SCH-4: The system must allow a Manager to edit the schedule.
- **Rationale**: Ensures the ability to make necessary adjustments to the schedule for reasons such as employee availability changes or operational demand changes.
- **AT-SCH-4-1**: As a Manager, edit an existing shift's time. Verify the change is reflected in the schedule.

SCH-5: The system must ensure shift details become read-only once the shift is over.
- **Rationale**: Preserves the integrity of historical scheduling data, which can be important for payroll and performance evaluation purposes.
- **AT-SCH-5-1**: Attempt to edit a shift that has already occurred. Verify the system does not allow the modification.

SCH-6: The system must schedule employees only during their indicated available times.
- **Rationale**: Respects employee availability preferences, contributing to job satisfaction and work-life balance.
- **AT-SCH-6-1**: Attempt to schedule an employee during their unavailable time. Verify the system prevents this action.

SCH-7: The system must allow a Manager and a Bookkeeper to view correct information about the summary of employees' tracked hours.
- **Rationale**: Provides necessary visibility into worked hours for payroll processing and management oversight.
- **AT-SCH-7-1**: As a Manager or Bookkeeper, view tracked hours for an employee. Verify the information displayed is accurate and up-to-date.

SCH-8: The system must have a clocking in option to allow employees to have their hours automatically recorded using their account details.
- **Rationale**: Simplifies the process of tracking work hours, ensuring accuracy and reducing the administrative burden on employees.
- **AT-SCH-8-1**: As an employee, clock in at the start of a shift. Verify that the system records the clock-in time under the employee's account.

SCH-9: The system must have a clocking out option to allow employees to stop their hours from being recorded using their account details.
- **Rationale**: Allows for precise tracking of work hours and ensures employees are compensated for the actual time worked.
- **AT-SCH-9-1**: As an employee, clock out at the end of a shift. Verify that the system records the clock-out time and accurately reflects the hours worked for that shift.

SCH-10: When a shift swap request is approved the schedule must update for each employee.
- **Rationale**: Ensures the schedule accurately reflects current staffing after shift swaps, maintaining operational integrity.
- **AT-SCH-10-1**: Initiate and approve a shift swap request. Verify that the schedule updates to reflect the new shift assignments for both involved employees.

SCH-11: The system must allow an employee to request shift swaps with other employees.
- **Rationale**: Provides flexibility for employees to manage their schedules while still meeting operational needs.
- **AT-SCH-11-1**: As an employee, request a shift swap with another employee. Verify that the request can be submitted through the system.

SCH-12: The system must allow a Manager to approve requested shift swaps from employees.
- **Rationale**: Gives Managers control over shift assignments to ensure operational needs are met.
- **AT-SCH-12-1**: As a Manager, receive a shift swap request and approve it. Verify that the system updates the schedule accordingly.

SCH-13: The system must allow a Manager to deny requested shift swaps from employees.
- **Rationale**: Ensures that Managers can maintain staffing levels that meet operational requirements.
- **AT-SCH-13-1**: As a Manager, receive a shift swap request and deny it. Verify that the system notifies the requesting employees and does not change the schedule.

SCH-14: The system must ensure all shift swaps maintain single shift assignments for employees without overlapping schedules.
- **Rationale**: Prevents scheduling conflicts that could leave shifts understaffed or employees overburdened.
- **AT-SCH-14-1**: Attempt to approve a shift swap that would result in double booking an employee. Verify the system prevents the swap.

SCH-15: The system's view schedule option must display correct information including all shift swaps, deleted shifts, edited shifts, and holidays.
- **Rationale**: Ensures that employees and Managers have accurate and up-to-date information for planning and operational purposes.
- **AT-SCH-15-1**: After several scheduling changes, including swaps, deletions, and edits, view the schedule. Verify that all changes are accurately reflected.

### c. Use cases associated with the feature or functional requirement <a name="f1-usecases"></a>

![SchedulingUseCase_WithDailyCase](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/3a008778-7cc8-4360-a8ce-fcb7a24862f4)

Within the scheduling system there are 3 primary actors. Front of House Staff, Kitchen Staff, and Delivery Drivers have the same interactions with the Scheduling System so they were combined into one actor. The scheduling system should allow all users (each user class defined in User Classes and Characteristics) to know when they are working, allow a Manager to create and edit schedules, and allow a Bookkeeper to access the tracked hours used to pay employees. All use cases are written assuming the user is logged in.

| ID and Name | UC-1: Create Schedule |
| ----------- | ----------- |
| Created By: | Nolan |
| Date Created: | 02/15/24 |
| Primary Actor: | Front of House and Kitchen Manager |
| Description | The actor assigns each shift to employees for the next two weeks. |
| Trigger: | Actor opens create schedule functionality of software. |
| Preconditions: |<ul><li>PRE-1: Actor is logged in to system.</li></ul> <ul><li>PRE-2: There is at least one employee in the system who is available to take shifts.</li></ul>|
| Postconditions: |<ul><li>POST-1: Each assigned shift is associated with an employee.</li></ul>|
| Normal Flow: |<ol>**1.0 Create Schedule**<li>Actor selects an employee(see Exception 1.4)</li><li>Actor assigns one or more shifts to the selected employee within the employee's listed availability(see Exception 1.1, 1.2, 1.3).</li><li>Actor continues, selecting one employee at a time until all shifts are assigned.</li><li>Actor saves the schedule.</li><li> Actor exits schedule creation functionality of app.</li></ol> |
| Alternate Flows: |  |
| Exceptions: |<ol>**1.1 Create Schedule Employee Availability Conflict**<li>Actor selects an employee.</li><li> If the employee does not have listed availability, no shifts are assigned to them. </li><li>Actor moves on to step 3 of primary flow.</li></ol><ol>**1.2 Create Schedule Employee Hour Conflict**<li>Actor selects an employee.</li><li> If the employee is working a maximum number of hours, no additional shifts are assigned to them. </li><li>Actor moves on to step 3 of primary flow.</li></ol><ol>**1.3 Create Schedule No Assigned Shifts For Employee**<li>Actor selects an employee.</li><li> Actor does not assign any shifts to the selected employee.</li><li>Actor moves on to step 3 of primary flow.</li></ol><ol>**1.4 Create Schedule Previous Selected Employee**<li>Actor selects an employee that was previously selected.</li><li> Actor assigns an additional one or more shifts to the selected employee.</li><li>Actor moves on to step 3 of primary flow.</li></ol>|
| Assumptions: | User is logged in |
| Priority: | High |
| Frequency of Use: | Every two weeks |
| Business Rules: | There are a maximum number of hours that each person is allowed to work, both per day and per week. |
| Other Information: |  |

**User Story 1: Approve Swap**

As a Manager I want to approve shift swap requests so that upon employee request shifts are swapped between the two employees.

**Acceptance Criteria:**

Given a Manager has approved a shift swap request then the shift being swapped for each employee must be switched.

**User Story 2: Create Schedule**

As a Manager I want to create a schedule for a 2 week period at one store location so that each employee knows when they are working.

**Acceptance Criteria:**

Given the schedule is made, when the schedule is viewed by employees, then the schedule shall be shown to the employee with correct information such as employees working, shifts, hours, and location.

**User Story 3: Edit Schedule**

As a Manager I want to edit an already made schedule to update, remove or add shifts so that the schedule is correct with any new information.

**Acceptance Criteria:**

Given the schedule is updated, when employees view the schedule, then the updated schedule should be shown with all alterations. The changes made to the schedule must also be consistent with changes made by the Manager.

**User Story 4: Indicate Availability**

As an employee when I indicate availability, I want to notify the Manager of the periods that I am available to work so that I am scheduled to work when I am available.

**Acceptance Criteria:**

Given availability is indicated, when the schedule is posted the availability which was indicated should be the only time with scheduled shifts.

**User Story 5: View Tracked Hours**

As a Bookkeeper or Manager, I want to view the worked hours for each employee so that I can accurately pay them for their worked hours.

**Acceptance Criteria:**

When tracked hours for an employee are viewed then a summary of all worked hours including overtime and statutory holidays and vacations should be displayed.

**User Story 6: Clock In**

As a Front of House Staff, Kitchen Staff, Bookkeeper, or Delivery Driver I want to clock in at work so that the hours I work are accurately recorded in the system.

**Acceptance Criteria:**

Given I have clocked in, when my tracked hours are viewed then the hours I have worked should be accurately recorded for that day.

**User Story 7: Clock Out**

As a Front of House Staff, Kitchen Staff, Bookkeeper, or Delivery Driver I want to clock out so that the hours I work are accurately recorded in the system.

**Acceptance Criteria:**

Given I have clocked out, when my tracked hours are viewed then the hours I have worked should accurately be accurately recorded for that day.

**User Story 8: Request Swap Shift**

As an employee I want to request a shift swap with another employee with the same role and upon acceptance create a shift swap request which needs to be approved.

**Acceptance Criteria:**

Given an employee has requested a shift swap with another employee, when another employee has accepted, then a shift swap request should be posted awaiting approval.

**User Story 9: View Schedule**

As a Staff member I want to view the posted schedule for the current work weeks as well as the next 2 weeks so that I can view the correct information of what shift I am working.

**Acceptance Criteria:**

Given an employee selects to view the schedule they should be shown the up to date schedule with correct information for the current shift period as well as the next. 

**User Story 10: View Personal Weekly Schedules**

As an employee I want to be able to view my personal schedule in a weekly format so that I can view schedule information for the selected week to learn what shifts I am working and to help me make shift swap decisions.

**Acceptance Criteria:**

Given an employee selects to view the schedule and the weekly personal view, they should be shown the up to date schedule in a weekly format with correct personal information for their shift period.

**User Story 11: View Personal Monthly Schedules**

As an employee I want to be able to view my personal schedule in a monthly format so that I can view schedule information for the selected month to learn what shifts I am working and to help me make shift swap decisions.

**Acceptance Criteria:**

Given an employee selects to view the schedule and the monthly personal view, they should be shown the up to date schedule in a monthly format with correct personal information for their shift period.

**User Story 12: View Personal Daily Schedules**

As an employee I want to be able to view my personal schedule in a daily format so that I can view schedule information for the selected day to learn what shifts I am working and to help me make shift swap decisions.

**Acceptance Criteria:**

Given an employee selects to view the schedule and the daily personal view, they should be shown the up to date schedule in a daily format with correct personal information for their shift period.

**User Story 13: View All Employees' Weekly Schedules**

As an employee I want to be able to view the schedule of all employees. I want to be able to view the schedule in a weekly format so that I can view schedule information for the upcoming week to learn what shifts my co-workers are working and to help me make shift swap decisions.

**Acceptance Criteria:**

Given an employee selects to view the schedule and the weekly all employee view, they should be shown the up to date schedule in a weekly format with correct information of all employees for all shift periods.

**User Story 14: View All Employees' Monthly Schedules**

As an employee I want to be able to view the schedule of all employees. I want to be able to view the schedule in a monthly format so that I can view schedule information for the upcoming month to learn what shifts my co-workers are working and to help me make shift swap decisions.

**Acceptance Criteria:**

Given an employee selects to view the schedule and the monthly all employee view, they should be shown the up to date schedule in a monthly format with correct information of all employees for all shift periods.

**User Story 15: View All Employees' Daily Schedules**

As an employee I want to be able to view the schedule of all employees. I want to be able to view the schedule in a daily format so that I can view schedule information for the upcoming day to learn what shifts my co-workers are working and to help me make shift swap decisions.

**Acceptance Criteria:**

Given an employee selects to view the schedule and the daily all employee view, they should be shown the up to date schedule in a daily format with correct information of all employees for all shift periods.

### d. Storyboards <a name="f1-storyboards"></a>
  
#### Staff Home Screen  
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/homescreen1staff.png" width="1000">  
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/homescreen2staff.png" width="600">  

#### Bookkeeper Home Screen  
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/homescreenbookkeeper.png" width="400">  

#### Manager Home Screen
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/homescreenmanager.png" width="400">  

#### Create Schedule 
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/createschedule1.png" width="600">    
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/createschedule2.png" width="600">  

#### Edit Schedule 
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/editschedule1.png" width="600">    
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/editschedule2.png" width="600">  

#### Shift Swap  
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/shiftswap1.png" width="600">    
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/shiftswap2.png" width="600">  

#### Availability  
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/availability1.png" width="600">  
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/availability2.png" width="400">  

#### Clock In/Out 
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/homescreenclockin.png" width="800">  

#### Track Hours  
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/homescreentrackedhours.png" width="600">  




### e. Sequence Diagram for Create Schedule <a name="f1-sequence"></a>
<img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/Schedulingiteration3diagrams/schedulingsequencediagram.png" width="1000">  

This sequence diagram shows the process of a Manager interacting with the system to create a schedule. The Manager starts by selecting the schedule menu icon which leads to the scheduling page. The Manager then selects the create schedule button and is shown a list of all employees which they can select. Upon selecting the employee they would like to book shifts for, they are shown the employees availability and select an available time period for that employee. This process of selecting employees and selecting shifts is repeated until the schedule is made. The Manager has the option to save and exit the create schedule menu to return to later or save and publish so any user can view the schedule.

### f. Swimlane Diagram for Create Schedule <a name="f1-swimlane"></a>

Swimlane - Create Schedule: 

![Swimlane - Create Schedule](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/145606952/3c148963-e306-40af-af11-3582a5b247da)


The swimlane diagram represents the workflow for a scheduling system, detailing the interactions between a Manager and the system when creating and publishing schedules.

Manager Selects Employee: The Manager initiates the process by selecting an employee to schedule.

More employees need to be scheduled: Checks whether any employees are not scheduled for a shift. If all employees are scheduled, the Manager saves the schedule. If not, the system would display shift availability of the next employee. 

Display Shift Availability: The system displays the available shifts for the selected employee.

Select New Shift: The Manager selects a new shift for the employee to schedule them in.

Check for Shift Conflict: The system checks if there are any conflicts with the selected shift for the employee, such as overlapping shifts or exceeding maximum hours. If a conflict exists, the Manager is directed back to select a different shift. If no conflict exists, the Manager proceeds to the next step.

Save Schedule: The Manager saves the schedule, with the option to save and leave or save and publish.

Publish Schedule: The Manager publishes the schedule, making it available to employees.

This workflow ensures that the Manager can efficiently create and publish schedules while ensuring that conflicts are identified and resolved before finalizing the schedule. 



### g. State Diagram for Swap Shifts <a name="f1-state"></a>
![State Diagram Shift Swap 2](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/bc908563-37d7-4d0f-a815-abb005007082)


An employee refers to users who are authorized to request shift swaps, which are all user classes. An employee starts a shift swap request, and the request will remain in "In Preparation" state until the employee submits or cancels the request. The request contains information about which two shifts are requested to be swapped, and information about the employee they wish to swap the shift with. If the employee cancels the request without submitting, the request enters "Cancelled" state. If the employee submits the request, the request enters "Initiated" state. In the "Initiated" state a second employee, that was requested to swap shifts in the shift swap request, can choose to either accept or deny the request. If the second employee denies, the request enters "Cancelled" state. If the second employee accepts, the shift swap request enters "Submitted" state. In the "Submitted" state, a Manager (Front of House/Kitchen Manager user class) can either approve or deny the shift swap request. If a Manager denies the request, the request enters "Cancelled" state. If a Manager approves the request, the shift swap request enters "Confirmed" state. While transitioning to the "Confirmed" state, the system will swap the employees assigned to the shifts identified in the approved request.


## ii. Communication and Announcement <a name="feature-2"></a>

Communication and Announcement feature allows sending and receiving messages and company-wide announcements.

### a. Description and Priority <a name="f2-description"></a>

The Communication and Announcement feature is a high priority feature in the system for the following reasons. All employees must receive notifications of new announcements, and be able to view the announcements and be aware of any and all major changes in the company. It is also important that all employees can send and receive messages to any employee member or employee messaging group. 

### b. Functional Requirements <a name="f2-functional"></a>

COM-1: The system must allow embedding capabilities for images, videos, and PDFs in announcements and messages to enhance communication.
- **Rationale:** Visual aids and documents can significantly enhance the clarity and effectiveness of communication, making information more engaging and easier to understand.
- **AT-COM-1-1:** Test embedding an image, a video, and a PDF in a message. Verify they display correctly in the message.
- **AT-COM-1-2:** View the message on different device types to ensure media compatibility.

COM-2: The system must provide the ability for a Manager to create and publish announcements to all employees.
- **Rationale:** Centralized dissemination of information ensures that all employees are timely informed of important organizational news.
- **AT-COM-2-1:** As a Manager, create and publish an announcement. Verify it is accessible to all employees immediately after publishing.

COM-3: The system must provide the ability for a Manager to create and publish announcements specific to a user class or location.
- **Rationale:** Allows for targeted communication, ensuring that only relevant employees are notified, which can reduce information overload and increase relevancy.
- **AT-COM-3-1:** Publish an announcement targeted at a specific user class. Confirm only that class can view the announcement.

COM-4: The system must provide the ability for a Manager to edit announcements.
- **Rationale:** Ensures that any inaccuracies or updates can be corrected or added, keeping information current and accurate.
- **AT-COM-4-1:** As a Manager, select an existing announcement, make changes, and save. Verify the changes are reflected in the announcement.

COM-5: The system must provide the ability for a Manager to remove announcements.
- **Rationale:** Ability to remove outdated or incorrect information helps maintain the integrity of organizational communications.
- **AT-COM-5-1:** As a Manager, delete an announcement. Confirm it is no longer accessible or visible to employees.

COM-6: The system must provide the ability for all employees to view announcements.
- **Rationale:** Ensures equitable access to information for all employees, fostering an informed and cohesive workforce.
- **AT-COM-6-1:** Log in as different employees and verify that announcements are accessible and viewable.

COM-7: The system must provide the ability for a Manager to view announcements with more details, such as the number of viewers, the viewers information, and the reactions of viewers.
- **Rationale:** Gives Managers insights into the engagement and reach of their communications, allowing for more informed communication strategies.
- **AT-COM-7-1:** As a Manager, view detailed analytics of an announcement. Verify the accuracy of viewer and reaction data.

COM-8: The system must provide the ability for all employees to react to the published announcements.
- **Rationale:** Interaction with announcements can increase engagement and provide feedback to Managers about the workforce's concerns and interests.
- **AT-COM-8-1:** As an employee, view an announcement and use a reaction feature (like, thumbs up, etc.). Verify the reaction is recorded and visible.

COM-9: The system must provide the ability for all employees to communicate with other employees.
- **Rationale:** Facilitates direct communication among employees, promoting collaboration and team cohesion.
- **AT-COM-9-1:** Send a message to another employee and confirm it is received and can be responded to.

COM-10: The system must safeguard sensitive information such as chat logs and announcement management, so that only Manager has permission to manage announcements, and each employee, including the Manager, only has access to messages involving them.
- **Rationale:** Ensures privacy and security of communications, complying with data protection laws and internal policies.
- **AT-COM-10-1:** Attempt to access another employee's messages or manage announcements as a non-Manager. Verify access is denied.
- **AT-COM-10-2:** Conduct a permissions audit to confirm that access controls are correctly implemented.

### c. Use cases associated with the feature or functional requirement <a name="f2-usecases"></a>

![CommunicationUseCase](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/dffc8c25-f125-48b5-a1e6-d6ac25e31955)


Within the Communication and Announcement feature there are two primary actors, "Manager", and "Front of House Staff, Kitchen Staff, Delivery Drivers, and Bookkeepers". Manager has the ability to create, edit, and send company-wide announcements, while Front of House Staff, Kitchen Staff, Delivery Drivers, and Bookkeepers can view these announcements and react to them. Front of House Staff, Kitchen Staff, Delivery Drivers, Bookkeepers, and Managers can send messages to individuals or groups, view received messages, and edit messages they have sent. The system must allow embedding capabilities for images, videos, and PDFs in announcements and messages, provide role-based access control, safeguard sensitive information, and tailor interfaces and features based on user roles, ensuring effective communication and announcement management within the company. 

**User Story 1: Send message**

As an employee, I want to be able to send a message to another employee or a group of employees, so that I can communicate information effectively. 

**Acceptance Criteria:** 

The system must allow all employees, including Manager, to be able to send messages to one or more individuals from the list of employees. 

**User Story 2: View message**

As an employee, I want to be able to view the messages that are sent to me or to the message group that I am part of, so that I can stay informed about communication among other employees within the company.  

**Acceptance Criteria:** 

The system must allow all employees, including Manager, to view received messages.

**User Story 3: Edit message**

As an employee, I want to be able to edit a message that I have previously sent, so that I can make clarifications or update the message as necessary. 

**Acceptance Criteria:** 

The system must allow all employees to be able to edit messages that they had sent before. 

**User Story 5: React announcements** 

As an employee, I want to be able to react to each announcement, so that I can share my opinion or acknowledge the content. 

**Acceptance Criteria:** 

The system must allow all employees to be able to react to announcements with emojis. 

**User Story 6: View announcements** 

As an employee, I want to be able to view all announcements, so that I can stay updated on the important changes and news within the company. 

**Acceptance Criteria:** 

The system must allow all employees to be able to view all announcements. Must be able to find the most recent announcement within 2 seconds. 

**User Story 7: View announcement information**

As a Manager, I want to be able to view detailed information of each and every announcement, so that I can see information such as the information about how many people have viewed the announcements and who have viewed the announcements. 

**Acceptance Criteria:** 

The system must allow the Manager to be able to view all of the announcement's related information such as the creation date, information about who has viewed the announcement. 

**User Story 8: Send announcements**

As a Manager, I want to be able to send announcements to all employees, so that I can share important information effectively to all employees in the company. 

**Acceptance Criteria:** 

The system must allow the Manager, to create and send announcements using text, images, videos, or PDF. 

**User Story 9: Edit announcements** 

As a Manager, I want to be able to edit or update announcements that I have already sent, so that I can update information where necessary. 

**Acceptance Criteria:** 

The system must allow a Manager to be able to access and edit announcements that have been sent. 

### d. Storyboards <a name="f2-storyboards"></a>


#### Group Chat 
![Storyboard - Group Chat](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/145606952/cc2b29d7-a664-429e-a48e-9650f3e4f874)


#### Private Chat
![Storyboard - Private Chat](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/145606952/c9e41a44-390e-42e6-9deb-9df4644fe2a7)


#### New Announcement
![Storyboard - New Announcement](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/145606952/50fa2928-0f37-4edc-807a-73352bd89786)


#### Edit Announcement
![Storyboard - Edit Announcement](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/145606952/8fc4be8f-c146-4ef2-9ebb-3b7190531c3d)






### e. Dialog Map for Send Message <a name="f2-dialogmap"></a>
![Dialog Map Send Message 6](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/8b15c081-aed9-4b4e-b9b7-7d07de680ef8)

When an authorized user is interested in sending a message, they begin by navigating to the messages section of the system. This results in a "View Messages Page" that shows a list of past individual or group recipients. The view is continually updating with any new messages. If the user wants to exit this section of the app at this point, they can "Exit Messages Section". From the "Messages Page", the user can select a past recipient (either individual or group) to see the message history with the selected recipient(s). The user is able to exit this page by navigating back to the previous page. From the "Message History", the user can begin typing a new message or editing a message they previously sent, which allows them to see a "Draft Message".  Alternatively, from the "Messages Page", the user can select the plus icon to create a new message which will show an "Empty Message History". The user can select the recipient(s) for the new message. If the system receives a message with an identical list of selected recipient(s) as the empty message, the user is shown that message in the history. The user can write a "New Message" once the recipient(s) are selected for the empty message history resulting in a Draft Message. The "Draft Message" view can be exited by clearing changes, and the system will return to the "Message History" view that was displayed before beginning to write or edit a message. The user can add files to a "Draft Message" through an "Add File Option". Once file(s) are selected they are attached to the message. Once the user sends a "Draft Message", the user views the message in a "Message History" with the recipient(s).

## iii. Recipe Management <a name="feature-3"></a>

### a. Description and Priority <a name="f3-description"></a>
The Recipe Management feature has a high priority in the application. A Manager, Kitchen Staff, or Front of House Staff must be able to view active or inactive recipes. Manager and Kitchen Staff must be able to view the full recipe including the ingredient list, preparation instructions, and allergens. Front of House Staff must only be able to view the allergens in a recipe. The Manager is the only one who is able to create, edit, archive and unarchive recipes. Expect a high frequency of use, Kitchen Staff and Front of House Staff will use this feature daily when making the ice cream and serving customers as the Front of House Staff are required to inform customers of any allergens in the ice cream. 

### b. Functional Requirements <a name="f3-functional"></a>

RMS-1: Kitchen Staff, Front of House Staff and Managers must be able to view active and inactive recipes. 
- **Rationale:** This ensures that all employees involved in food preparation and service (Kitchen Staff, Front of House Staff, and Managers) can access recipe information, regardless of the recipe's status (active or inactive), ensuring operational continuity and transparency.
- **AT-RMS-1-1:** Log in as Kitchen Staff. Verify access to view both active and inactive recipes.
- **AT-RMS-1-2:** Log in as Front of House Staff. Verify access to view both active and inactive recipes.
- **AT-RMS-1-3:** Log in as Manager. Verify access to view both active and inactive recipes.

RMS-2: Managers and Kitchen Staff must be able to view the full recipe including ingredients list, preparation instructions, and allergens.
- **Rationale:** This ensures that those directly involved in food preparation (Managers and Kitchen Staff) have access to all necessary information to carry out their tasks safely and efficiently.
- **AT-RMS-2-1:** Log in as Manager. Open a recipe and verify that it displays the full recipe details, including ingredients, preparation instructions, and allergens.
- **AT-RMS-2-2:** Log in as Kitchen Staff. Open a recipe and verify that it displays the full recipe details, including ingredients, preparation instructions, and allergens.

RMS-3: Front of House Staff must be only able to view the allergens of a recipe.
- **Rationale:** This ensures that Front of House Staff, who interact directly with customers, have access to crucial allergen information to address customer inquiries and ensure their safety.
- **AT-RMS-3-1:** Log in as Front of House Staff. Open a recipe and verify that it displays only the allergen information while hiding the rest of the recipe details.

RMS-4: Manager must be able to create new recipes with details such as name, ingredients, preparation instructions and allergen information.
- **Rationale:** Allows Managers to contribute to the recipe database, facilitating menu updates and new ice cream flavor introductions.
- **AT-RMS-4-1:** Log in as Manager. Navigate to the recipe creation page. Enter all required details (name, ingredients, preparation instructions, and allergen information) and save. Verify that the new recipe appears in the recipe list.

RMS-5: Manager must be able to edit existing recipes, including changing details, adding or removing ingredients, and updating allergen information.
- **Rationale:** This allows Managers to maintain the accuracy and relevance of recipes as ingredients change or preparation methods are updated.
- **AT-RMS-5-1:** Log in as Manager. Open an existing recipe. Edit any detail (name, ingredients, preparation instructions, or allergen information) and save changes. Verify that the changes are reflected in the recipe details.

RMS-6: Manager must be able to archive a recipe, changing its status to inactive, and be able to unarchive a recipe, changing its status to active.
- **Rationale:** This feature enables Managers to manage the recipe database effectively, archiving recipes that are no longer in use while retaining them for reference if needed.
- **AT-RMS-6-1:** Log in as Manager. Archive a recipe and verify that it is moved to the inactive recipes list.
- **AT-RMS-6-2:** Log in as Manager. Unarchive a previously archived recipe and verify that it is moved back to the active recipes list.

RMS-7: The system must be able to display different recipe views based on the access of the user's role.
- **Rationale:** This ensures that each user sees only the relevant information based on their role, enhancing usability and security.

&emsp;&emsp;RMS-7.1: The system must have a detailed recipe view which contains name, list of ingredients, preparation instructions, and allergens.

&emsp;&emsp;RMS-7.2: The system must have a limited recipe view which only contains the name, and allergens.

- **AT-RMS-7-1:** Log in as Manager. Open a recipe and verify that it displays the detailed view containing name, ingredients, preparation instructions, and allergens.
- **AT-RMS-7-2:** Log in as Kitchen Staff. Open a recipe and verify that it displays the limited view containing only the name and allergens.
- **AT-RMS-7-3:** Log in as Front of House Staff. Open a recipe and verify that it displays the limited view containing only the name and allergens.

RMS-8: The system must be able to archive recipes, removing it from the list of active recipes and adding it to the list of inactive recipes.
- **Rationale:** This enables efficient management of recipe inventory, ensuring that only relevant and current recipes are readily accessible.
- **AT-RMS-8-1:** Log in as Manager. Archive a recipe and verify that it is removed from the list of active recipes.

RMS-9: The system must be able to unarchive recipes, removing it from the list of inactive recipes and adding it to the list of active recipes.
- **Rationale:** This allows Managers to restore previously archived recipes if they become relevant again.
- **AT-RMS-9-1:** Log in as Manager. Unarchive a previously archived recipe and verify that it is added back to the list of active recipes.

RMS-10: The system must display a prompt the user to save when they exit editing mode if they didn't already save.
- **Rationale:** This prevents accidental loss of data by reminding users to save their changes before exiting editing mode.
- **AT-RMS-10-1:** Make changes to a recipe. Attempt to exit editing mode without saving. Verify that a prompt appears, reminding the user to save changes.

RMS-11: The system must display a prompt to the user to save when they exit creation mode if they didn't already save.
- **Rationale:** Similar to RMS-10, this ensures data integrity by reminding users to save new recipes before exiting creation mode.
- **AT-RMS-11-1:** Create a new recipe. Attempt to exit creation mode without saving. Verify that a prompt appears, reminding the user to save the new recipe.

RMS-12: The system must provide an edit option for each recipe.
- **Rationale:** This offers users the flexibility to update recipe details as needed, contributing to the overall usability of the system.
- **AT-RMS-12-1:** Log in as Manager. Open a recipe and verify that an edit option is available.

RMS-13: The system must implement a save option to confirm changes. 
- **Rationale:** Providing a save option ensures that users have control over when changes are finalized, enhancing usability and preventing accidental data loss.
- **AT-RMS-13-1:** Make changes to a recipe. Click the save option. Verify that changes are saved and reflected in the recipe details.

RMS-14: The system must allow the Manager to exit editing mode.
- **Rationale:** This allows Managers to complete their editing tasks efficiently, improving user experience.
- **AT-RMS-14-1:** Log in as Manager. Edit a recipe. Click the exit option. Verify that editing mode is exited without saving changes if no changes were made, or changes are saved if modifications were made.

RMS-15: The system must display an empty template with sections for name, ingredients, preparation instructions, and allergen information when creating a recipe.
- **Rationale:** Providing an organized template simplifies the recipe creation process, ensuring that all necessary information is captured.
- **AT-RMS-15-1:** Log in as Manager. Navigate to the recipe creation page. Verify that an empty template with sections for name, ingredients, preparation instructions, and allergen information is displayed.

RMS-16: The system must allow the Manager to enter text in each section of the recipe during creation mode.
- **Rationale:** Enabling text input ensures that Managers can provide detailed information for each aspect of the recipe.
- **AT-RMS-16-1:** Log in as Manager. Navigate to the recipe creation page. Enter text in each section (name, ingredients, preparation instructions, and allergen information). Verify that text input is allowed in each section.

RMS-17: The system must provide a save option for new recipes.
- **Rationale:** This allows Managers to finalize and save new recipes once all necessary details have been entered.
- **AT-RMS-17-1:** Log in as Manager. Create a new recipe and enter all required details. Click the save option. Verify that the new recipe is saved and appears in the recipe list.

RMS-18: The system must ensure newly created recipes are visible in the list of recipes.
- **Rationale:** Confirming visibility ensures that newly created recipes are readily accessible to users.
- **AT-RMS-18-1:** Log in as Manager. Create a new recipe. Verify that the new recipe appears in the recipe list.

RMS-19: The system must allow a Manager to exit creation mode.
- **Rationale:** This enables Managers to complete recipe creation tasks efficiently, improving user experience.
- **AT-RMS-19-1:** Log in as Manager. Create a new recipe. Click the exit option. Verify that creation mode is exited without saving the new recipe.

RMS-20: The system must allow a Manager to select specific recipes for archiving or unarchiving.
- **Rationale:** Empowers Managers to manage recipe status which enhances system flexibility and usability.
- **AT-RMS-20-1:** Log in as Manager. Select specific recipes and archive them. Verify that selected recipes are moved to the inactive recipes list.
- **AT-RMS-20-2:** Log in as Manager. Select previously archived recipes and unarchive them. Verify that selected recipes are moved back to the active recipes list.

RMS-21: The system must have different access levels for Manager, Kitchen Staff, and Front of House Staff.
- **Rationale:** This ensures that each user role has appropriate access permissions, maintaining data security and integrity.
- **AT-RMS-21-1:** Log in as Manager. Verify access to all features and functionalities.
- **AT-RMS-21-2:** Log in as Kitchen Staff. Verify restricted access to certain features and functionalities.
- **AT-RMS-21-3:** Log in as Front of House Staff. Verify restricted access to certain features and functionalities.

RMS-22: The system must display meaningful error messages to users in case of unsuccessful operations or system errors.
- **Rationale:** Providing informative error messages helps users understand issues and take appropriate actions, improving user experience.
- **AT-RMS-22-1:** Simulate an unsuccessful operation or system error. Verify that a meaningful error message is displayed to the user, explaining the issue and providing guidance on potential resolutions.

### c. Use cases associated with the feature or functional requirement <a name="f3-usecases"></a>

![RMS Usecase Diagram](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/RMS-Usecase-Diagram-V4.png)

Within the recipe management system there are 3 primary actors, "Managers", "Kitchen Staff", and "Front of House Staff". The recipe management system allows Managers to "Edit Recipe", "Create Recipe", "Archive Recipe", and "View Recipe". The extends from "Archive Recipe" to "Unarchive Recipe" represent an alternate flow. If the recipe has an active status it will be able to be archived, but if the recipe has an inactive status it will be able to be unarchived. The "Front of House Staff" can only "View Limited Recipe" which includes a display of the allergen information. The extends from "View Recipe" to "View Limited Recipe" represents this as an alternate flow of the "View Recipe" use case (see UC-2 Alternate Flow 2.1). The "Managers" and "Kitchen Staff" are the only users that can "View Detailed Recipe" which includes a display of the ingredients list, preparation instructions, and Allergens. The extends from "View Recipe" to "View Detailed Recipe" represents this as the normal flow of the "View Recipe" use case (see UC-2 Normal Flow 2.0).

| ID and Name | UC-2 View Recipe |
| ----------- | ----------- |
| Created By: | Nolan, Justin |
| Date Created: | 02/14/24 |
| Primary Actor: | Kitchen Staff, Managers, Front of House Staff |
| Description | The Actor selects a recipe from the list of all possible recipes. The system displays a view of the recipe based on the actor's level of access. |
| Trigger: | Actor opens recipe menu section of the system. |
| Preconditions: | <ul><li>PRE-1: User is logged in.</li><li>PRE-2: User is authenticated.</li></ul> |
| Postconditions: | <ul><li>POST-1: Recipe is displayed.</li></ul> |
| Normal Flow: | <ol>**2.0 View Detailed Recipe**<li>Kitchen Staff or Manager selects the recipe menu option.</li><li>Select active or inactive recipes to view.</li><li>Select desired recipe from list.</li><li>System displays the detailed recipe view.</li></ol> |
| Alternate Flows: | <ol>**2.1 View Limited Recipe**<li>Front of House Staff selects the recipe menu option.</li><li>Select active or inactive recipes to view.</li><li>Select desired recipe from list.</li><li>System displays the limited recipe view.</li></ol> |
| Exceptions: |  |
| Priority: | High |
| Frequency of Use: | 10 times per day by the Kitchen Staff, 1 time per day by the Manager, 20 times per day by the Front of House Staff. |
| Business Rules: | Must alert all customers of potential allergens. Only authorized ingredients may be in the ice cream. |
| Other Information: | RSM-2, RSM-3, RSM-7 |
| Assumptions: | Recipe already exists in the system. |

**User Story 1: Edit Recipe**

As a Manager, I want exclusive rights to edit existing recipes, so that I can change recipe details, add or remove ingredients, and update allergen information.

**Acceptance Criteria:**

There is an option to edit available on each recipe in the user interface. Upon selecting the option, I can choose the specific section of the recipe I want to edit. I can save the changes after editing and the system confirms the changes have been saved. The system should not save any changes if I exit the editing page, if I try to exit without saving the system should prompt me to save my changes. I can exit the viewing mode at any time.  

**User Story 2: Create Recipe**

As a Manager, I want exclusive rights to create new recipes, so that I can create new recipes with details such as name, ingredients, preparation instructions and allergen information.

**Acceptance Criteria:**

There is an option to create a new recipe in the user interface. After selecting that feature I should see an empty template for a recipe which contains a section for name, ingredients, preparation instructions and allergen information. I should be able to enter text in each section. I should be able to save my work. The new recipe should be viewable on the list of recipes. I should be able to exit creation mode. 

**User Story 3: Archive Recipe**

As a Manager, I want exclusive rights to archive recipes, so that I can change the status of a recipe from active to inactive and change the status from inactive to active. 

**Acceptance Criteria:**

There is an option to archive recipes if the status is active and an option to unarchive recipes if the status is inactive in the user interface. Upon selecting that option I should be able to select which recipes I want to archive or unarchive. The recipe should be added to the inactive recipe list, if the status was active, and the recipe should be removed from the active recipe list. The recipe should be added to the active recipe lists, if the status was inactive, and the recipe should be removed from the inactive recipe list.  

### d. Storyboards <a name="f3-storyboards"></a>

#### Storyboard 1: UC-2 View Recipe Normal Flow

![UC-2 Normal flow](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/Prototype%20Images/ViewRecipe1SB.png)

#### Storyboard 2: UC-2 View Recipe Alternate Flow

![UC-2 Alternate flow](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/Prototype%20Images/ViewRecipe2SB.png)

#### Storyboard 3: Edit, Create, and Archive Recipe

![Create and Edit](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/Prototype%20Images/CreateEditSB.png)

### e. Sequence Diagram for Storyboard 3 <a name="f3-sequence"></a>

![Sequence Diagram SB3](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/diagrams/RMS-Create%3AEdit-SequenceDiagram.png)

This sequence diagram shows the process of a Manager interacting with the system to create, edit and manage recipes. The Manager starts by selecting the recipe menu icon, leading to the list of active recipes. The Manager then selects the create new recipe icon (plus symbol), leading to the display of a blank recipe template. The Manager proceeds to fill in various details such as the name, upload an image, provide a description, set the active status, input ingredients, and provide preparation instructions. After filling in those details, the Manager selects the back arrow, triggering a save verification window. Upon confirmation, the system checks the recipe status and adds the newly created recipe to the top of the active recipe list. The Manager then interacts with the system to view the updated active recipe list and selects the new recipe for detailed information. The sequence concludes with the Manager entering edit mode, adding allergens to the recipe in the allergens section, and saving the changes, resulting in an updated active recipe list.  

### f. Swimlane Diagram for View Recipe <a name="f3-swimlane"></a>

![Swimlane UC-2](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/Prototype%20Images/Swimlane.png)

This swimlane diagram shows how a Manager, Front of House Staff, and Kitchen Staff interacts with the system when viewing a recipe. This diagram relates to UC-2 and covers the normal and alternate flows. All three lanes start the same way by selecting the recipe menu option. The Manager and Kitchen Staff lanes interact with the system in the same way and represent the normal flow of UC-2. After the Manager/Kitchen Staff selects the recipe menu option they then select whether they want to view active or inactive recipes. If active is selected the system displays the active recipe list, otherwise the system displays the inactive recipe list. The Manager/Kitchen Staff then selects the desired recipe to view, resulting in the system displaying the detailed recipe. The Front of House Staff lane interacts with the system lane to represent the alternate flow of UC-2. After the Front of House Staff selects the recipe menu option they then select whether they want to view active or inactive recipes. If active is selected the system displays the active recipe list, otherwise the system displays the inactive recipe list. The Front of House Staff then selects the desired recipe to view, resulting in the system displaying the limited recipe. 

## iv. Onboarding Materials <a name="feature-4"></a>

This feature describes the different levels of access different employees have to onboarding materials such as instructional videos.

### a. Description and Priority <a name="f4-description"></a>

The Onboarding Materials feature has a low priority in the application. An authenticated user must be able to view the onboarding materials, but only Manager have the right to edit the materials such as add or remove materials. Overall we expect a low frequency of use. New employees will need to become familiar with onboarding material and may access material multiple times a day for the first two weeks of employment. However, we expect established employees will only access a material to reference it once each month.

### b. Functional Requirements <a name="f4-functional"></a>
ONB-1: A user must be able to view the onboarding materials assigned to their user class.
- **Rationale:** This ensures all employees have access to the onboarding materials that they need to become familiar with their work, at all times.
- **AT-ONB-1-1:** Log in as Manager, verify access to onboarding materials assigned to Manager.
- **AT-ONB-1-2:** Log in as Front of House Staff, verify access to onboarding materials assigned to Front of House Staff.
- **AT-ONB-1-3:** Log in as Kitchen Staff, verify access to onboarding materials assigned to Kitchen Staff.
- **AT-ONB-1-4:** Log in as Bookkeeper, verify access to onboarding materials assigned to Bookkeeper.
- **AT-ONB-1-5:** Log in as Delivery Driver, verify access to onboarding materials assigned to Delivery Driver.

ONB-2: A Manager must be able to edit the onboarding materials and modify the asssigned user classses.
- **Rationale:** This allows onboarding materials to be easily changed in any way when it needs to be by the Manager.
- **AT-ONB-2-1:** Log in as Manager, verify the ability to edit onboarding materials. Ensure the edits are reflected accurately.
- **AT-ONB-2-2:** Log in as Manager, verify the ability to modify the user classes assigned to onboarding materials. Verify that the access permissions of the onboarding material accurately reflect the changes.

ONB-3: A Manager must be able to create the onboarding materials and assign it to one or more user classes.
- **Rationale:** This allows new onboarding materials to be easily created and assigned within the system by the Manager.
- **AT-ONB-3-1:** Log in as Manager, verify access to create onboarding materials and assign it to one of the user classes including Front of House Staff, Kitchen Staff, Bookkeeper, Delivery Driver, and Manager.
- **AT-ONB-3-2:** Log in as Manager, verify access to create onboarding materials and assign it to a combination of the user classes including Front of House Staff, Kitchen Staff, Bookkeeper, Delivery Driver, and Manager.

ONB-4: A Manager must be able to remove the onboarding materials.
- **Rationale:** This allows easy removal of obsolete onboarding materials by the Manager.
- **AT-ONB-4-1:** Log in as Manager, verify the ability to remove onboarding materials.

ONB-5: A Manager must be able to view all onboarding materials, including material not assigned to their user class.
- **Rationale:** This allows the Manager to have access to all onboarding materials at all time, in case they need to check if the onboarding materials are correct, or need to refer to them.
- **AT-ONB-5-1:** Log in as Manager, verify access to onboarding materials of all user classes, including Front of House Staff, Kitchen Staff, Bookkeeper, Delivery Driver, and Manager.

### c. Use cases associated with the feature or functional requirement <a name="f4-usecases"></a>
![OnboardingUseCase](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/f38b872d-77f0-47f8-962f-7f9665926a49)

Within the framework of the onboarding material use case diagram, there exist two distinct actors. The primary actor, referred to as the "Manager," possesses comprehensive permissions, encompassing the ability to view, edit, create, and remove onboarding materials. The secondary actor is Front of House Staff, Kitchen Staff, Delivery Driver, and Bookkeepers with their access limited solely to viewing onboarding materials.

 **User Story 1: View Onboarding Materials**
 
As an authenticated user, I want to be able to view the onboarding materials at any time, so that I can access the necessary information for onboarding purposes.

**Acceptance Criteria:**

Given that I am an employee, when I view onboarding materials, then I can select the specific onboarding materials I am interested in viewing. The selected onboarding materials are displayed to me.
I can exit the viewing mode when I'm done.


**User Story 2: Edit Onboarding Materials**

As a Manager, I want to have exclusive rights to edit the onboarding materials, so that I can ensure the content is up-to-date and relevant for the employees.

**Acceptance Criteria:**

Given that I am a manager, when I edit onboarding materials, I can select the specific onboarding materials I want to edit. 
After editing, I can save the changes, and the system confirms that the changes have been successfully saved. The saved changes are consistent with the edits I made.
I can exit the editing mode when I'm done.


**User Story 3: Create Onboarding Material**

As a Manager, I want the capability to create new onboarding materials, so that I can provide updated and relevant content for employee onboarding.

**Acceptance Criteria:**

Given that I am a manager, when I create onboarding materials, I can input the necessary details for the new onboarding material, such as title, content, and any relevant metadata.
After entering the information, I can save the new onboarding material, and the system confirms its successful creation. The saved changes are consistent with the onboarding material I created.
I can exit the creation mode when I'm done.

**User Story 4: Remove Onboarding Material**

As a Manager, I want the exclusive authority to remove outdated or irrelevant onboarding materials, so that I can maintain the integrity and relevance of the onboarding content.

**Acceptance Criteria:**

Given that I am a manager, when I remove onboarding materials, I can remove the specific onboarding material I wish to remove.
The system prompts for confirmation before proceeding with the removal to prevent accidental deletions.
Upon confirmation, the removed onboarding material is no longer accessible to users in the system.
I can exit the removal mode when I'm done.

### d. Storyboards <a name="f4-storyboards"></a>
#### View Onboarding Material
![View Onboarding Materials](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/105994651/fc636634-6d67-4c86-bf60-4034debbf21c)

#### Create New Onboarding Material
![Create Onboarding Materials New](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/105994651/87c33aba-f222-4496-984e-0dddf16ec837)

#### Edit Onboarding Material
![Edit Onboarding Materials](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/105994651/0cac1dec-c942-4d47-956a-2b6bd0cf4124)

#### Delete Onboarding Material
![Delete Onboarding Materials](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/105994651/8bf8c19c-76f0-4d67-bdf1-f5e0d1343879)



## v. Account Management <a name="feature-5"></a>

### a. Description and Priority <a name="f5-description"></a>
The Account Management feature has a high priority in the system.  It allows a Manager to manage access to the system by creating and deleting accounts.  A user must be able to edit their important information to ensure it is correct, and must be able to log in and log out of their account.  This feature is expected to be used 100+ times per day due to the high frequency of logging in and logging out.

### b. Functional Requirements <a name="f5-functional"></a>

ACC-1: The system must provide the Manager with the capability to delete user accounts that are no longer active within the company.
- **Rationale:** Deleting inactive user accounts ensures that the system remains organized and only contains relevant user information, enhancing security and reducing clutter.
- **AT-ACC-1-1:** Log in as Manager. Navigate to the user management section. Select an inactive user account and choose the delete option. Verify that the user account is permanently removed from the system.

ACC-2: The system must allow the Manager to create new user accounts by entering their username and role, granting them access to the system.
- **Rationale:** This enables Managers to control access to the system by adding new user accounts as needed, facilitating user management and system security.
- **AT-ACC-2-1:** Log in as Manager. Navigate to the user creation section. Enter the required information (username, role) and save. Verify that the new user account is created and granted access to the system.

ACC-3: The system must allow the Managers to view a user’s role, contact information, and username.
- **Rationale:** Providing Managers with access to user details facilitates effective management of user accounts and roles within the system.
- **AT-ACC-3-1:** Log in as Manager. Navigate to the user management section. Select a user account and verify that their role, contact information, and username are displayed.

ACC-4: The system must allow the Manager to edit a user’s role, and username
- **Rationale:** Allowing Managers to edit user roles and usernames enables flexible user management, accommodating changes in user responsibilities or information.
- **AT-ACC-4-1:** Log in as Manager. Navigate to the user management section. Select a user account and choose the edit option. Modify the user's role and/or username and save changes. Verify that the changes are applied to the user account.

ACC-5: The system must allow users to edit their payment information, contact information, and password.
- **Rationale:** Allowing users to manage their own account information promotes user autonomy and ensures data accuracy.
- **AT-ACC-5-1:** Log in as a user. Navigate to the account settings section. Edit payment information, contact information, and password. Save changes. Verify that the modifications are successfully applied to the user's account.

ACC-6: The system must allow users to log in to their accounts with their username and password.
- **Rationale:** Enabling users to log in with their credentials ensures secure access to the system and personalized user experiences.
- **AT-ACC-6-1:** Navigate to the login page. Enter valid username and password. Click on the login button. Verify that the user is successfully logged in and directed to the system's dashboard.

ACC-7: The system must allow users to log out of their accounts.
- **Rationale:** Providing users with a logout option ensures security by allowing them to end their active sessions securely.
- **AT-ACC-7-1:** While logged in as a user, navigate to the logout option. Click on the logout button. Verify that the user is successfully logged out and redirected to the login page.

ACC-8: The system must allow users to view their account information to ensure its accuracy and completeness.
- **Rationale:** Allowing users to review their account information promotes transparency and empowers them to verify and update their details as needed.
- **AT-ACC-8-1:** Log in as a user. Navigate to the account settings section. Verify that the user's account information, including payment details, contact information, and password, is displayed accurately.

ACC-9: The system must automatically log users out of the application after 1 hour of inactivity.
- **Rationale:** Automatic logout after 1 hour of inactivity enhances security by preventing unauthorized access to user accounts if the device is left unattended.
- **AT-ACC-9-1:** Log in as a user and navigate to a page within the application. Wait for 1 hour without interacting with the application. After 1 hour, attempt to perform an action within the application. Verify that the system has automatically logged the user out, requiring them to log in again to continue using the application.

ACC-10: The system must allow the Bookkeeper to access an employee's payment information.
- **Rationale:** The Bookkeeper plays a critical role in managing payroll and financial records. Granting them access to employee payment information ensures they can perform their duties effectively, ensuring accurate and timely payment processing.
- **AT-ACC-10-1:** Log in as the Bookkeeper. Navigate to the employee management section. Select an employee's profile. Verify that the payment information, including salary, payment method, and any other relevant details, is displayed.

### c. Use cases associated with the feature or functional requirement <a name="f5-usecases"></a>

![accounts](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/5c1e9194-dff4-404a-ab8d-0dbca1d80947)


**User Story 1: Delete Account**

As a Manager I want to delete an account so that I can remove any users that no longer work for my company from the system.

**Acceptance Criteria:**

There is an option for the Manager to "Delete" an account.  This feature must remove a user’s access to the system, yet still retain information about their employment for legal and tax purposes.

**User Story 2: Create Account**

As a Manager I want to create an account so that my newly hired employees have access to the system.

**Acceptance Criteria:**

There is an option for a Manager to create an account. After selecting this the Manager will be prompted to set the employee's role and username. This will then allow the employee to log in and set their password and payment information. 

**User Story 3: View Account Information**

As a Manager I want to view a user's account information so that I can see their role and contact information.

**Acceptance Criteria:**

There is an option for a Manager to view account information for any selected employee. It will show their username, role, and contact information.

**User Story 4: Manage Account**

As a Manager I want to change a user's role or username in order to ensure it stays up to date.

**Acceptance Criteria:**

There is an option for a Manager to manage account for any employee. It will allow them to edit a users username and role.  These changes must be reflected in the "View Account Information" use case, and the "Log In" use case.

**User Story 5: View Account Information**

As a user I want to view my account information so I can ensure it is all correct.

**Acceptance Criteria:**

There is an option for a user to view account informaton for themselves. It will show their username, role, and contact information.

**User Story 6: Edit Account Information**

As a user I want to edit my account information so I can keep my payment information, contact information, and password up to date. These changes must be reflected in the view account information use case, and the log in use case.

**Acceptance Criteria:**

A user must have an option to edit account information for themselves.  This will allow them to change their password, contact information, and payment information. These changes must be reflected in the view account information use case, and the log in use case.

**User Story 7: Log In**

As a user I want to log in to my account so I can use the system.

**Acceptance Criteria:**

When a user opens the app they will have an option to log in to their account.  They will be prompted to enter their account username and password.  If username and password are valid then they will be granted access to the system.

**User Story 8: Log Out**

As a user I want to log out of my account so I can ensure no one else can use my account.

**Acceptance Criteria:**

A user must have the option to log out of their account.  This will remove their access to the system until they log in again. The system must automatically log out a user after 1 hour of inactivity.

**User Story 9: View Payment Information**

As a Bookkeeper I want to view a selected employee's payment information.

**Acceptance Criteria:**

The Bookeeper must have the option to view any employee's payment information. This feature will allow the Bookeeper to view the selected employee's transit number, institution number, account number, and void cheque.


### d. Storyboards <a name="f5-storyboards"></a>

### Create Account
![Account Creation](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-AccountCreation.png)

### Delete Account
![Account Deletion](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-AccountDeletion.png)

### View Account Information
![View Account Information](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-ViewInformation.png)

### Edit Cell Phone Number
![Edit Cell Phone](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-EditCell.png)

### Edit Email
![Edit Email](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-EditEmail.png)

### Edit Role
![Edit Role](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-EditRole.png)

### Manage Payment Information
![Manage Pay](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-ManagePay.png)

### Edit Username
![Edit Username](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-EditUsername.png)

### Login
![Login](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-Login.png)

### Logout

![Logout](https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/Account-Management/diagrams/ACC-Logout.png)


### e. Dialog Map for Edit Account <a name="f5-dialogmap"></a>
![Edit Account drawio](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/105994651/95879fab-28eb-4887-81e4-af17ba0b1683)

In this figure, the process of a user modifying their own account information is depicted. In the first step, the user logs into the system and navigates to the account profile page. Users can then choose what they want to modify, including password configuration, updating contact information, and specifying payment details. Once the user has completed their changes, changes will be saved. Finally the user can exit the account profile section of the application or log out via Exit.



# 6 Data Requirements <a name="data-requirements"></a>

## i. Logical Data Models <a name="data-model"></a>

![Entity Relationship Diagram - Ben6](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/76890860/55803d9e-2210-42c8-a900-ba137dd72789)

![Entity Relationship Diagram - My Diagram (3)](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/76890860/e790f756-8172-44c3-95ff-42bc88e63bb4)

The Entity Relationship Diagram (ERD) and the UML Class Diagram serve as visual tools to represent the data structure and relationships within the Banter Ice Cream System. The purpose of these diagrams is to articulate how various data entities within the system interact and relate to each other, which is essential for understanding the flow of information and the underlying structure of the system’s data.

### Diagrams Explanation

1. **Employee to User Account:**
   - **Relationship Name:** "Operates"
   - **Relationship Type:** One-to-One
   - **Description:** Each Employee operates a single User Account to access the system. It can be read as "A User Account is operated by an Employee" or "An Employee operates a User Account."

2. **Employee to Banking Information:**
   - **Relationship Name:** "Has"
   - **Relationship Type:** One-to-One
   - **Description:** Each Employee has specific Banking Information for payroll purposes. It can be interpreted as "Banking Information is held by an Employee" or "An Employee has Banking Information."

3. **Employee to Shift:**
   - **Relationship Name:** "Assigned To"
   - **Relationship Type:** One-to-Many
   - **Description:** An employee can be assigned to many shifts, but each shift is assigned to one employee. It can be read as "A Shift is assigned to an Employee" or "An Employee is assigned to a Shift."

4. **Employee to Schedule:**
   - **Relationship Name:** "Follows"
   - **Relationship Type:** One-to-One
   - **Description:** Each employee follows one schedule, and each schedule is followed by one employee. It can be interpreted as "A Schedule is followed by an Employee" or "An Employee follows a Schedule."

5. **Schedule to Shift:**
   - **Relationship Name:** "Includes"
   - **Relationship Type:** One-to-Many
   - **Description:** A Schedule includes multiple Shifts. It can be interpreted as "A Schedule includes Shifts" or "Shifts are included in a Schedule."

6. **Employee to Message:**
   - **Relationship Name:** "Creates"
   - **Relationship Type:** One-to-Many
   - **Description:** An Employee creates multiple Messages. It can be read as "A Message is created by an Employee" or "An Employee creates Messages."

7. **Employee to Announcements:**
   - **Relationship Name:** "Authors"
   - **Relationship Type:** One-to-Many
   - **Description:** An employee authors multiple Announcements. It can be interpreted as "An Announcement is authored by an Employee" or "An Employee authors Announcements."

8. **Employee to Recipe:**
   - **Relationship Name:** "Develops"
   - **Relationship Type:** One-to-Many
   - **Description:** An employee develops multiple recipes. It can be read as "A Recipe is developed by an Employee" or "An Employee develops Recipes."

9. **Recipe to Ingredients:**
   - **Relationship Name:** "Consists of"
   - **Relationship Type:** Many-to-Many
   - **Description:** A recipe consists of multiple ingredients, and each Ingredient can be part of multiple Recipes. It can be read as "A Recipe consists of Ingredients" or "Ingredients are part of a Recipe."

10. **Ingredients to Allergens:**
    - **Relationship Name:** "Contains"
    - **Relationship Type:** Many-to-Many
    - **Description:** Ingredients may contain multiple allergens, and each allergen may be found in multiple ingredients. It can be interpreted as "An Ingredient contains Allergens" or "Allergens are contained in an Ingredient."

11. **Announcement to Reaction:**
    - **Relationship Name:** "Generates" or "Receives"
    - **Relationship Type:** One-to-Many
    - **Description:** This relationship indicates that an Announcement generates multiple Reactions or receives multiple Reactions from users. It can be read as "An Announcement generates Reactions" or "Reactions are received by an Announcement."

12. **Announcement to View:**
    - **Relationship Name:** "Attracts" or "Accumulates"
    - **Relationship Type:** One-to-Many
    - **Description:** This relationship shows that an Announcement attracts multiple Views or accumulates multiple Views over time. It can be interpreted as "An Announcement attracts Views" or "Views are accumulated by an Announcement."


## ii. Data Dictionary <a name="data-dictionary"></a>

| Data Element       | Description                                                                                          | Composition or Data Type                                                                                | Length  | Values                                                                                       |
|--------------------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|---------|----------------------------------------------------------------------------------------------|
| Account Number     | Unique number representing a personal bank account                                                   | Integer                                                                                                 | 12      | Positive numbers                                                                             |
| Allergen           | Details of an allergen found in an ingredient in a recipe                                            | Allergen ID <br>+ Allergen Name <br>+ Recipe ID                                                                 | N/A     | N/A                                                                                          |
| Allergen ID        | Unique number representing a personal bank account                                                   | Integer                                                                                                 | 12      | System-generated sequential integer, beginning with 1                                        |
| Allergen Name      | The name of a food that according to government of Canada commonly causes an allergic reaction       | String                                                                                                  | 128     | Any ASCII characters                                                                         |
| Announcement       | A message sent out to all employees of Banter Ice Cream                                              | Announcement ID <br>+ Author <br>+ Content <br>+ 0:5{File} <br>+ 0:n{Reaction} <br>+ 0:n{View} <br>+ Date Posted                | N/A     | N/A                                                                                          |
| Announcement ID    | Unique identifier for an announcement                                                                | Integer                                                                                                 | 12      | System-generated sequential integer, beginning with 1                                        |
| Author             | Key to employee who is responsible for creating the object (Announcement, Message, Recipe, Schedule) | Employee ID                                                                                             | N/A     | N/A                                                                                          |
| Banking Info       | Information about an employee’s bank account, such that the Bookkeeper can pay the employee.         | Bank Info ID <br>+ Employee ID <br>+ Transit Number <br>+ Institution Number <br>+ Account Number                       | N/A     | N/A                                                                                          |
| Bank Info ID       | Unique identifier for stored bank account information                                                | Integer                                                                                                 | 10      | System-generated sequential integer, beginning with 1                                        |
| Contact            | Information used to contact an employee.                                                             | Email <br>+ Phone Number                                                                                    | 320     | Form of local@domain                                                                         |
| Content            | The text contents of a message or announcement object                                                | String                                                                                                  | 10000   | Any ASCII characters                                                                         |
| Date Posted        | The date and time that an announcement is sent to the system                                         | DateTime                                                                                                | 8 bytes | Format YYYY-MM-DD HH:MI:SS                                                                   |
| DateTime           | The date and time that a reaction occurs                                                             | DateTime                                                                                                | 8 bytes | Format YYYY-MM-DD HH:MI:SS                                                                   |
| Direction          | A description of what steps are used to follow a recipe                                              | String                                                                                                  | 1000    | Any ASCII characters                                                                         |
| Email              | An email address                                                                                     | String                                                                                                  | 320     | Form of local@domain                                                                         |
| Emoji ID           | Unique identifier for an emoji using Unicode Standard format                                         | String                                                                                                  | 10      | Form is “U+” followed by 5 alphanumeric characters. For example, U+1F37B                     |
| Employee           | Information about the individual who works at Banter Ice Cream                                       | Employee ID <br>+ Employee Name <br>+ Role <br>+ Contact <br>+ 1:2{Location} <br>+ Banking Info ID <br>+ Username <br>+ Schedule ID | N/A     | N/A                                                                                          |
| Employee ID        | Unique identifier for an employee                                                                    | Integer                                                                                                 | 20      | System-generated sequential integer, beginning with 1                                        |
| Employee Name      | Name used to address an employee of Banter Ice Cream                                                 | String                                                                                                  | 128     | Any ASCII characters                                                                         |
| End Time           | The date and time that a shift ends.                                                                 | DateTime                                                                                                | 8 bytes | Format YYYY-MM-DD HH:MI:SS                                                                   |
| File               | An attached file of an allowed file type (pdf, video, or image)                                      | File                                                                                                    | 20 MB   | File format must be pdf, avi, mov, mp3, mp4, png, jpg, heic                                  |
| Ingredient         | Details of an ingredient used in a recipe                                                            | Ingredient ID <br>+ Name <br>+ Quantity <br>+ Units <br>+ Recipe ID                                                     | N/A     | N/A                                                                                          |
| Ingredient ID      | Unique identifier for an ingredient                                                                  | Integer                                                                                                 | 20      | System-generated sequential integer, beginning with 1                                        |
| Ingredient Name    | A term used to identify an ingredient                                                                | String                                                                                                  | 32      | Any ASCII characters                                                                         |
| Institution Number | A number representing the financial institution responsible for a given bank account                 | Integer                                                                                                 | 3       | Positive number                                                                              |
| isActive           | A true or false value that indicates if a recipe is currently served at a Banter Ice Cream location. | Boolean                                                                                                 | 1       | True, False                                                                                  |
| Location           | Name for a branch of Banter Ice Cream. Currently two possibilities, Abbotsford or Chilliwack.        | String                                                                                                  | 20      | Abbotsford, Chilliwack                                                                       |
| Message            | A message sent to one or employees at Banter Ice Cream.                                              | Message ID <br>+ Author <br>+ 1:n{Recipient} <br>+ Content <br>+ 0:5{File} <br>+ Timestamp                                  | N/A     | N/A                                                                                          |
| Message ID         | Unique identifier for a message                                                                      | Integer                                                                                                 | 20      | System-generated sequential integer, beginning with 1                                        |
| Password           | A secure text that allows access to an account                                                       | String                                                                                                  | 50      | Any ASCII characters                                                                         |
| Phone Number       | A phone number                                                                                       | Integer                                                                                                 | 10      | Positive number                                                                              |
| Transit Number     | A number representing the institution branch responsible for a given bank account                    | Integer                                                                                                 | 5       | Positive number                                                                              |
| Quantity           | The amount of an ingredient used in a recipe                                                         | Integer                                                                                                 | 2       | Positive number                                                                              |
| Reaction           | A non-textual response to an announcement by an employee using an emoji                              | Reaction ID <br>+ Emoji ID <br>+ Employee ID <br>+ DateTime                                                         | N/A     | N/A                                                                                          |
| Reaction ID        | Unique identifier for a reaction                                                                     | Integer                                                                                                 | 20      | System-generated sequential integer, beginning with 1                                        |
| Recipe             | Instructions on how to make an Ice Cream Flavour.                                                    | Recipe Name <br>+ Author <br>+ isActive <br>+ 0:n{Allergen} <br>+ 1:n{Ingredient} <br>+ 1:n{Direction}                      | N/A     | N/A                                                                                          |
| Recipient          | An employee who receives a message                                                                   | Employee ID                                                                                             | N/A     | N/A                                                                                          |
| Role               | The function that is required of a given employee or shift.                                          | String                                                                                                  | 20      | Manager, Front of House Staff, Kitchen Staff, Bookkeeper, Delivery Driver                    |
| Schedule           | The shifts currently assigned to an employee.                                                        | Employee ID  <br>+ 0:n{Shift ID} <br>+ Author                                                                   | N/A     | N/A                                                                                          |
| Shift              | An assigned time for an employee to work at a given Banter Ice Cream branch location.                | Shift ID <br>+ Start Time <br>+ End Time <br>+ Role <br>+ Location                                                      | N/A     | N/A                                                                                          |
| Shift ID           | Unique identifier for a shift                                                                        | Integer                                                                                                 | 20      | System-generated sequential integer, beginning with 1                                        |
| Start Time         | The date time that a shift begins.                                                                   | DateTime                                                                                                | 8 bytes | Format YYYY-MM-DD HH:MI:SS                                                                   |
| Timestamp          | The date and time that the object was created.                                                       | DateTime                                                                                                | 8 bytes | Format YYYY-MM-DD HH:MI:SS                                                                   |
| Units              | The units for a quantity                                                                             | String                                                                                                  | 20      | Standard baking units: cups, tablespoons, teaspoons, milliliters, liters, milligrams, grams  |
| User Account       | An account that an employee using to access the system                                               | Username <br>+ Employee ID <br>+ Password                                                             | N/A     | N/A                                                                                          |
| Username           | Unique identifier for a user in the form of an email                                                 | String                                                                                                  | 320     | Form of local@domain                                                                         |
| View               | An employee who has viewed an announcement                                                           | Employee ID <br>+ Timestamp                                                                                 | N/A     | N/A                                                                                          |

The system shall have data entries as described by the data dictionary. The data dictionary has 5 columns. The first column, data element, provides an identifier for the type of data entry. The second column, description, describes in plain language, what the data entry will represent in the system. The third column, composition or data type, describes what data is included in the data entry. A composition has multiple data elements listed that make up one entry of that data element. Each data element listed is separated using a “+” sign. Some data elements may also have curly braces around them. In front of the curly braces there are numbers to represent the minimum and maximum number of the data element in curly braces that can be associated with each value saved of the data entry type, the form is "minimum number of the data element:maximum number of the data element". The maximum number being "n" indicates that there is an unlimited number of the data element. If the data element is not a composition it is a primitive and it can be described by its data type. The fourth column, length, provides more context for a primitive data element’s data type in the form of a maximum length for the data type. The fifth column, values, provides more context for a primitive data element’s allowed values. 


## iii. Reports <a name="data-report"></a>

The system shall not generate any reports.


## iv. Data Integrity <a name="data-integrity"></a>

**Employee Data and Account**

DAT-1: Adhere to Canadian laws regarding business tax documents. As a result the system must retain supporting documentation for payroll for 6 years, counted from the end of the tax year that the payroll occurred in. The supporting documentation required is employee name, contact information, and wage.
- **Rationale:** Complies with legal requirements for record-keeping, ensuring Banter Ice Cream adheres to applicable laws.
- **AT-DAT-1-1:** Confirm with the system's data management policies that the identified employee information is retained for the required duration.
- **AT-DAT-1-2:** Confirm manually editing past schedule data is not possible. Login as a Manager and try to edit a shift scheduled in the past. Verify this is not possible.
- **AT-DAT-1-3:** Delete an employee's account. Confirm that schedule data for that employee is still saved.

DAT-2: The system must retain each employee's banking information until after the employee's last paycheck is received by the employee.
- **Rationale:** Ensures the employee is able to be paid, but does not keep sensitive data after the employee no longer works for Banter Ice Cream.
- **AT-DAT-2-1:** Delete an employee's account. Confirm that banking data continues to be stored until after their last scheduled shift.

DAT-3: A new employee can gain access to the system after a Manager adds an account for the employee.
- **Rationale:** As new employees are hired the system must be able to accommodate that change. New employees need to be able to gain access to the system to use the system and complete their jobs.
- **AT-DAT-3-1:** Login as a Manager and create a new employee's account. Login as the employee and verify that login succeeds and grants access to the system.

DAT-4: An employee loses access to the system when their account is deleted. 
- **Rationale:** As employees stop working for Banter Ice Cream they no longer need access to the system. 
- **AT-DAT-4-1:** Login as a Manager and delete an employee's account. Try to login as the employee and verify that login fails.

**Scheduling and Tracked Hours**

DAT-5: The system must retain each shift in employee schedule for one year after the scheduled shift date.
- **Rationale:** Past schedules may be used to complete tax forms, so the schedule data will need to be saved until the next tax deadline.
- **AT-DAT-5-1:** Confirm with the system's data management policies that schedule information is retained for the required duration.

DAT-6: The system must retain employee availability for one week after the date of the identified availability.
- **Rationale:** Past availability does not provide help towards scheduling future shifts. Reduce costs for data storage and infrastructure by removing past availability data.
- **AT-DAT-6-1:** Add availability to the system for the current day. Confirm that availability cannot be deleted. Wait one week. Confirm that availability can be deleted.

DAT-7: The system must retain clocked hours for each employee for 6 years, counted from the end of the year the clocked hours occurred in. This requirement is necessary due to Canadian laws regarding business tax documents.
- **Rationale:** Complies with legal requirements for record-keeping, ensuring Banter Ice Cream adheres to applicable laws and has details necessary to answer a detailed audit.
- **AT-DAT-7-1:** Confirm with the system's data management policies that clocked hours are retained for the required duration.

**Communication and Announcements**

DAT-8: The system must retain messages for one year after the message is sent.
- **Rationale:** Employees may want to refer to past messages to confirm information. After one year the past information is unlikely to be useful, and requires extra infrastructure to store.
- **AT-DAT-8-1:** Confirm with the system's data management policies that messages are retained for the required duration.

DAT-9: The system must retain each announcement until the announcement is removed by a Manager.
- **Rationale:** Employees may want to refer to past announcements to confirm information. A Manager may want to delete an announcement if the information is out of date or otherwise inaccurate.
- **AT-DAT-9-1:** Confirm with the system's data management policies that announcements are retained for the required duration.
- **AT-DAT-9-2:** Login as a Manager and delete an announcement. Verify that announcement is deleted.

**Recipe Management**

DAT-10: The system must retain each recipe for the lifetime of the system.
- **Rationale:** Recipes are retained as a record of past recipes. Recipes may be reused in the future or customers may request an ice cream similar to a past recipe.
- **AT-DAT-10-1:** Confirm with the system's data management policies that recipes are retained for the required duration.

**Onboarding Materials**

DAT-11: The system must retain each onboarding material until removed by a Manager.
- **Rationale:** Onboarding material takes effort to create and remains useful for at least several months. A Manager can identify when the onboarding material is no longer useful and remove it.
- **AT-DAT-11-1:** Confirm with the system's data management policies that onboarding materials are retained for the required duration.
- **AT-DAT-11-2:** Login as a Manager and delete one onboarding material. Verify that onboarding material is deleted.


# 7 External Interface Requirements <a name="external-interfaces"></a>

## i. User Interfaces <a name="user-interfaces"></a>

A medium fidelity prototype of the system can be found here: https://www.figma.com/file/Uc9R5x3QO1j0RJcTtubefa/Prototype?type=design&node-id=0-1&mode=design&t=8ogwlELfk2Qu3Zly-0

The prototype is designed to fit the screen of an iPhone 14, so the screen layout has the dimensions 390 x 844. Upon opening the app the user is prompted to enter a username and password. <br/>
The prototype has been designed for a user with a management role. The GUI standards to be followed were based on the Banter Ice Cream website, this includes the green and orange color scheme, font and the header banner. There are 2 versions of the homepage: a management version and a non-management version. Both versions of the homepage have a header at the top of the screen and an icon bar at the bottom. The management version of the homepage includes 3 buttons on the main screen "Announcements", "Onboarding Materials", and "Account Management" (See Image 1). 

<figure>
   <img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/Prototype%20Images/NewMHS.png" width="390" height="844">
   <figcaption>Image 1: Management Home Screen.</figcaption>
</figure>

The homepage for the non-management version of the homepage includes 2 buttons on the main screen "Announcements", and "Onboarding Materials" (See Image 2). The icon bar contains the following icons from left to right calendar, communication, home, recipe menu, and personal account info. This icon bar is displayed on every screen which allows for quick access to each feature at any time. Each page after the main page of each feature contains a back arrow in the top left where a user can go back to a previous page.

<figure>
   <img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/Prototype%20Images/NewGHS.png" width="390" height="844">
   <figcaption>Image 2: Non-Management Home Screen.</figcaption>
</figure>

The user is prompted with an error message (example in Image 3) to reduce mistakes using the application. A couple of cases that result in an error message include a user trying to login without entering both a username and password, and trying to exit without saving when creating or editing a recipe. 

<figure>
   <img src="https://github.com/Uvic-SENG321Spring2024/team8-developer/blob/main/Prototype%20Images/Error%20Message.png" width="390" height="844">
   <figcaption>Image 3: Error Message.</figcaption>
</figure>

## ii. Hardware Interfaces <a name="hardware-interfaces"></a>

### Processing
- **Memory Space:** A minimum of 40 MB of free space will be required to install the application.

### Resolution
- **Adaptable:** The application must be able to adapt to different phone screen resolutions and orientations.

### Hardware Access
- **Internal Storage:** The application will need access to internal storage of files to attach allowed file types to messages, announcements, recipes, and onboarding materials. The internal storage includes any local storage, cloud storage linked to the device, and the device's camera roll. The allowed file types include images, videos, and PDFs. 
- **Internet Connection:** The application will connect to the internet to backup application data and receive updates to data stored in the application. 

## iii. Software Interfaces <a name="software-interfaces"></a>
The Banter Ice Cream system interfaces with several software components to ensure seamless operation, data integrity, and user experience. Below are the key software interfaces and their purposes:
  
### Operating System
- **Operating Systems:** Android and iOS
- **Purpose:** The mobile application is designed to run on these operating systems, utilizing their native features and capabilities for notifications, data storage, and security.
- **Services Used:** local data encryption, and background task execution.

### Database System
- **Database:** MySQL 8.0 or PostgreSQL 13
- **Purpose:** Stores and manages all application data including user accounts, schedules, recipes, announcements, and employee information.
- **Data Exchange:** CRUD (Create, Read, Update, Delete) operations on employee details, schedules, recipes, and announcements.

### Authentication Service
- **Service:** OAuth 2.0 compliant service (e.g., Auth0)
- **Purpose:** Securely authenticate users without storing passwords in the application, allowing for single sign-on (SSO) capabilities and access control based on user roles.
- **Data Exchange:** Token-based authentication and authorization data.

## iv. Communication Interfaces <a name="communication-interfaces"></a>

### Messaging Services
The system will support embedding of images, videos, and PDFs in messages and announcements. 

### Security and Privacy
Communication channels must be secure, with safeguards for sensitive information like chat logs and management of announcements. This entails encryption, controlled access, and compliance with privacy regulations.

### Network Server Communication Protocols
- **Protocol:** HTTPS for all communications between the mobile application and server backend.
- **Purpose:** Ensure the secure transmission of sensitive data between the mobile app and the backend services.
- **Data Items:** API requests and responses, including authentication tokens, user input data, server responses, and error messages.

### Electronic Forms
- **Purpose:** Collect input from users within the app, such as availability, time-off requests, and onboarding materials.
- **Data Handling:** Secure submission to the backend server with validation both on the client-side and server-side.
- **Data Items:** Form fields and values, validation rules, and submission confirmations.

# 8 Software Quality Attributes <a name="quality-attributes"></a>

**Availability**

AVL-1: The system is available 99.99% each day during business hours.
- **Rationale:** The system is used frequently during business hours to track work hours by clocking in and out, make ice cream flavours by viewing the recipes, and arrange deliveries of ice cream between locations using messages. Customer satisfaction relies on fast and accurate usage of the system. 99.99% availability during business hours would result in a maximum downtime of 3.6 seconds of a 10 hour shift, which allows near real-time communication to continue.    
- **AT-AVL-1-1:** Review metrics from hosting application monitoring tools to verify that downtime is less than 0.01% each day.

AVL-2: The system is available 99.0% each day outside of business hours.
- **Rationale:** The system is used outside of business hours to check scheduled shifts, view messages, and view announcements. Customers of Banter Ice Cream are not waiting on the usage of the system. Banter Ice Cream employees are more likely to use the system if it is often accessible, increasing visibility according to business goals. On a day with a 10 hour shift (business hours), 99.0% availability outside business hours would result in a maximum downtime of 8.4 minutes.
- **AT-AVL-2-1:** Review metrics from hosting application monitoring tools to verify that downtime is less than 1% each day.

**Reliability**

REL-1: A backup of all system data is saved every night to minimize data loss. 
- **Rationale:** Minimizing data loss is beneficial because the system is more useful if it can be relied on to store updated and accurate information. Data loss would result in extra time spent adding the data back into the system, which takes employee time away from customers and may result in decreased customer satisfaction due to inaccurate information. 
- **AT-REL-1-1:** Review metrics of stored data to confirm that the most recent copy of data is updated every 24 hours.

**Scalability**

SCA-1: The system should be designed to easily accommodate future growth of employees with up to 200 users within the next 2 years.
- **Rationale:** Banter Ice Cream expects 70 employees during the summer season, so over 2 years that could result in 140 employees being hired. There is a margin of error of 60 employees, to ensure that the system can accommodate more than the expected number of new employees. 
- **AT-SCA-1-1:** Verify that the database has space to store 200 users.
- **AT-SCA-1-2:** Setup a test system with a similar configuration to the live system. Load test to confirm 200 employees can be added to the system.

SCA-2: The system should be designed to easily accommodate new functionalities without significant changes to the system architecture.
- **Rationale:** There were additional functionalities labeled out of scope in the first release of the system that are desired and contribute to Banter's business goals. Changes to include that functionality are expected to continue helping Banter meet their business goals.
- **AT-SCA-2-1:** Generate an architecture model and confirm there is loose or no coupling.
- **AT-SCA-2-2:** Presence of unit and integration tests with a minimum of 75% coverage to ensure new functionality does not break existing functionality. 

SCA-3: The system can accommodate the addition of extra archive storage of recipes over the system lifetime. 
- **Rationale:** Recipes are stored indefinitely as a record of past menus. As no delete functionality exists for recipes, it must be possible to continue adding recipes without removing previous recipes.
- **AT-SCA-3-1:** Confirm with the data storage provider that additional storage can be added. 

**Useability**

USE-1: The system should be user-friendly and allow a new employee to learn to use system features that are relevant to their role within three shifts.
- **Rationale:** A business objective is to reduce onboarding time for a new employee. Learning the system is an important aspect of onboarding an employee. 
- **AT-USE-1-1:** Have a person unfamiliar with Banter's system learn how to use the system. Verify that the time it took to learn is less than the equivalent of three shifts.

USE-2: Shift swapping should be accessible within 3 selections. 
- **Rationale:** Shift swapping is an important aspect of schedule management and 3 selections allows for the employee to find it quickly. 
- **AT-USE-2-1:** Login as an employee and request a shift swap. Verify that it took 3 selections or less to access the shift swap functionality after logging in.

USE-3: Viewing schedules should be accessible within 2 selections. 
- **Rationale:** Viewing schedules allows employees to learn when they are scheduled to work and 2 selections allows for the employee to find it quickly. 
- **AT-USE-3-1:** Login as an employee and view schedule. Verify that it took 2 selections or less to access the view schedule functionality after logging in.

USE-4: Accessing announcements should be accessible within 1 selection. 
- **Rationale:** Easily viewing announcements allows for increased employee engagement and increased employee knowledge. 
- **AT-USE-4-1:** Login as an employee and view announcements. Verify that it took 1 selection or less to access the view schedule functionality after logging in.

USE-5: Viewing recipes should be accessible within 2 selections. 
- **Rationale:** Recipes are necessary for kitchen staff to make planned ice creams, and easy access to the recipe allows the process for making ice cream to be completed quickly. 
- **AT-USE-5-1:** Login as an employee and view a recipe. Verify that it took 2 selections or less to access the view recipe functionality after logging in.

USE-6: Viewing messages should be accessible within 3 selections. 
- **Rationale:** Messages are necessary for organizing operational needs like a planned ice cream delivery between locations, swapping shifts, and discussing anything that occurred on shift. Easy access to the message facilitates better employee connection and engagement.
- **AT-USE-6-1:** Login as an employee and view messages. Verify that it took 3 selections or less to access the view message functionality after logging in.

USE-7: Standard conventions for all user interface elements.
- **Rationale:** Enforcing standard conventions will result in a system that is easier to learn and improves user experience, therefore improving employee engagement.
- **AT-USE-7-1:** Check documentation for agreed standard conventions. Login to the system and verify that each main feature of the system uses the agreed conventions.

**Performance** 

PER-1: The system must be able to handle 30 users simultaneously accessing it without degradation in performance. 
- **Rationale:** During peak times, such as when Banter Ice Cream opens during summer season, the system must be usable by multiple employees who would be using the system simultaneously to clock in, message each other, and begin making recipes. 30 employees is the maximum expected during peak time because Banter Ice Cream has 70 employees in the summer, but do not expect half the employees to access the system simultaneously.
- **AT-PER-1-1:** Load test the system to confirm that 30 users can use the system simultaneously. 

PER-2: Response times for loading pages and executing commands should not exceed 2 seconds under normal operational conditions.
- **Rationale:** Reducing load times improves the experience of employees accessing the system, and customers who are waiting on an employee accessing the system.
- **AT-PER-2-1:** Login to the system and access each page. Track how long it takes each page to load and verify it takes less than 2 seconds.
- **AT-PER-2-2:** Load test system to determine how many users result in load times greater than 2 seconds. Verify that the resulting number of users aligns with expected normal operational conditions.

**Security**

SEC-1: Unauthorized employees are not able to view another employee’s banking information.
- **Rationale:** Reduce potential fraud or stealing by only allowing employees with Bookkeeper access to view banking information. Bookkeepers must have access to pay the employees. 
- **AT-SEC-1-1:** As a Manager, access an employee's account and attempt to view banking information. Verify that banking information is not visible.
- **AT-SEC-1-2:** As a Bookkeeper, access an employee's account and attempt to view banking information. Verify that banking information is visible.
- **AT-SEC-1-3:** As an employee without a Manager or Bookkeeper role, access an employee's account and attempt to view banking information. Verify that banking information is not visible.

SEC-2: Industry standard information security procedures must be used when handling user information. 
- **Rationale:** User information is private and could be used maliciously. Industry standard security procedures will limit access to user information and prevent anyone without a user account from accessing any user information.
- **AT-SEC-2-1:** Conduct a security test to ensure that user information is handled using industry standard practices.

SEC-3: The system shall ensure that no persons outside the organization can access any information stored in the system. 
- **Rationale:**  Information stored in the system is private and could be used maliciously. Preventing anyone outside the organization from accessing the data ensures that information is protected and only people who Banter Ice Cream believe to be trustworthy can access the system.
- **AT-SEC-3-1:** Without logging in to the system, attempt to gain access using security testing procedures. Verify you cannot access the system.

SEC-4: Recipe ingredients and instructions can only be viewed by authorized employees.
- **Rationale:** Banter Ice Cream's recipes are essential to their business, and only employees that need access to ingredients and instructions to complete their job should be able to view them. Employees that have access to ingredients and instructions are Managers and Kitchen Staff.
- **AT-SEC-4-1:** Login as Kitchen Staff and verify that you can view ingredients and instructions of a recipe.
- **AT-SEC-4-2:** Login as Front of House Staff and verify that you cannot view ingredients and instructions of a recipe.

SEC-5: Recipe ingredient allergens can only be viewed by authorized employees.
- **Rationale:** Banter Ice Cream's recipes are essential to their business, and only employees that need access to allergens to complete their job should be able to view them. Allergen information does not provide enough data to replicate a recipe but is needed to provide accurate information to customers and prevent medical emergencies. Employees that have access to allergens are Managers, Kitchen Staff, and Front of House Staff.
- **AT-SEC-4-1:** Login as Kitchen Staff and verify that you can view allergens of a recipe.
- **AT-SEC-4-2:** Login as Front of House Staff and verify that you can view allergens of a recipe.
- **AT-SEC-4-3:** Login as Delivery Driver and verify that you cannot view allergens of a recipe.


# 9 Analysis Models <a name="analysis-models"></a>

## i. Data Flow Diagram Level 0 <a name="data-flow0"></a>

![Ben0levelDFD drawio](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/76890860/c5775ae3-5ae4-4974-a89f-519ce4f849e5)

The above Level 0 Data Flow Diagram depicts the Banter Ice Cream System as a centralized system interacting with four external entities: Staff, Manager, Bookkeeper, and Delivery Driver. 
The "All Users" entity in this Data Flow Diagram represents a collective group that includes every type of user in the system, providing a centralized point for data flows that are common across all user types to reduce redundancy and simplify the diagram's clarity. The system handles a variety of data flows including account updates, shift swap requests, onboarding materials, and clock-in/out data. It represents a high-level view of the system's interactions with its environment, showing how data is exchanged but not the internal workings of the system itself. The arrows indicate the direction of the data flow, meaning the data originates from the entity at the tail of the arrow and moves towards the entity at the head of the arrow. 

## ii. Data Flow Diagram Level 1 <a name="data-flow1"></a>

![BEN1LevelDFD drawio](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/76890860/569c1d75-9639-4630-9264-3f5e263fe1ab)

The above Level 1 Data Flow Diagram expands on the Level 0 by breaking down the system into more detailed processes: Manage User Account, Communicate, Facilitate Onboarding, Manage Schedule, View Tracked Hours, and Manage Recipe. Each of these processes is a part of the Banter Ice Cream System, representing different functionalities. It shows specific interactions between the system and users, such as account creation, schedule management, and recipe updating. The diagram includes a data store for Staff Hours Summary indicating where data is stored within the system. This Data Flow Diagram provides a more detailed understanding of the system's internal processes and their data interactions.

## iii. Data Flow Diagrams Level 2 <a name="data-flow2"></a>

### Manage Schedule Process
![DataFlow_Level2_Schedule-Page-2](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/88aea67f-536d-4827-adcf-483f8dd5a30a)

The user groups Front of House Staff, Kitchen Staff, Delivery Driver, and Bookkeeper are able to access the Clock Hours Subsystem to clock in and out of shifts. The Staff Hours The Front of House / Kitchen Manager user class (referred to in diagram as Manager) can Update Schedule Subsystem with Schedule Assignment and Schedule Updates, and can access Availability. All Users represent any user of the system and can be any user classes defined in User Class and Characteristics. All Users can Update Schedule Subsystem with their Availability, and access Schedule Information. A Manager can use Swap Shift Subsystem to access a Swap Shift Request, and send a Swap Shift Response. All Users can use Swap Shift Subsystem to send Swap Shift Request, and access Swap Shift Response. The Schedule Information from Swap Shift Subsystem and Update Schedule Subsystem are stored in the Schedule Store. The Staff Hours Summary resulting from the Clock Hours Subsystem is stored in the Employee Hours Summary data store.

### View Tracked Hours Process
![DataFlow_Level2_ProcessPayroll_Numbered](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/88d7d7d7-69f4-45cf-a31e-532f25618e13)

A Bookkeeper can view Staff Hours Summary accessed with View Tracked Hours use case. A Front of House / Kitchen Manager (referred to in diagram as Manager) can view Staff Hours Summary accessed with View Tracked Hours use case. The information needed for the Staff Hours Summary is saved in an Employee Hours Summary data store.

### Communicate Process
![DataFlow_Level2_Communicate_Numbered](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/4801165b-9674-4925-b228-5cd9cb25a3d3)

The Front of House / Kitchen Manager user class (referred to in diagram as Manager) can send an announcement with Send Announcement use case, where Announcement includes all information defined in the Data Dictionary. A Manager can use Edit Announcement use case to modify a sent announcement. Announcements are stored in the Announcement Store. A Manager can View Announcement Information to get information about Reactions to a sent announcement. All Users represent any user of the system and can be any user classes defined in User Class and Characteristics. Each user of the system (referred to in diagram as All Users) can View Announcement to see a selected announcement. Each user of the system can complete React Announcement use case to send a Reaction to an announcement. Reactions are also stored in the Announcement Store. Each user of the system can Send Message, where Message includes all information defined in the Data Dictionary. Each user of the system can Edit Message to modify their sent messages. Each user of the system can View Message when the recipients of the message include them. Messages are stored in the Message Store.

### Manage Recipe Process
![DataFlow_Level2_Recipe_Numbered](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/99b28161-3484-4508-bb8f-6e35bfa1e624)

The Front of House / Kitchen Manager user class (referred to in diagram as Manager) can create a recipe through Create Recipe use case. A Manager can edit a recipe through the Edit Recipe use case. Recipe Info resulting from the creation and editing use cases is saved in the Recipe Store. The Recipe Info stored in the Recipe Store can be viewed using the View Recipe use case. Both Front of House Staff and Kitchen Staff (referred to in the diagram as Front of House Staff/Kitchen Staff) are able to View Recipe to see the Recipe Info. A Manager can also View Recipe to see the Recipe Info.

### Manage Onboarding Process
![DataFlow_Level2_Onboarding_Numbered](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/01660f97-f127-4f4e-846c-21a8134a743d)

The Front of House / Kitchen Manager user class (referred to in diagram as Manager) can add new onboarding materials through the Create Onboarding Materials use case. A Manager can modify the onboarding materials through the Edit Onboarding Materials and Remove Onboarding Materials use cases. The Onboarding Materials are stored in the Onboarding Materials Store. The stored Onboarding Materials can be viewed using the View Onboarding Materials use case. All Users represent any user of the system and can be any user classes defined in User Class and Characteristics. Each user of the system (referred to in diagram as All Users) are able to View Onboarding Materials.

### Manage User Account Process
![DataFlow_Level2_UserAccount_Numbered](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/f3ded1cc-bd7a-4d01-932f-af20898741f5)

The Front of House / Kitchen Manager user class (referred to in diagram as Manager) can Create Account for a new user account. A Manager can also Edit Account or Delete Account, resulting in an Account Update. Account Info is stored in the Account Store. A Manager can view stored Account Info of any user in the system using the View Account Information use case. The Account Info does not include bank information, but otherwise includes all account information defined in the Employee data entity in the Data Dictionary. All Users represent any user of the system and can be any user classes defined in User Class and Characteristics. Each user of the system (referred to in diagram as All Users) are able to complete the Edit Personal Account use case for their own account, to add Personal Account Updates. Personal Account Updates includes all account information defined in the Employee data entity in the Data Dictionary, including bank information. Each user of the system can view Account Info about their own account with the View Account Information use case.

## iv. Data Flow Diagrams Level 3 <a name="data-flow3"></a>

### Clock Hours Subsystem
![DataFlow_Level2_Schedule-Page-3](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/ead4efe7-ecb6-4f01-9bcf-19b4b8f95590)

Front of House Staff and Kitchen Staff (referred to in the diagram as Front of House Staff/Kitchen Staff), Delivery Drivers, and Bookkeepers can Clock In and Clock Out. The Clock-In Data and Clock-Out Data resulting from the Clock In and Clock Out use cases is stored in the Employee Hours Summary data store.

### Update Schedule Subsystem
![DataFlow_Level2_Schedule-Page-4](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/967164f7-2dfd-4cb6-8064-9561a099e2e8)

All Users represent any user of the system and can be any user classes defined in User Class and Characteristics. All Users can Indicate Availability. The Availability of each user is stored in the Availability Store. The stored Availability is used by the Create Schedule and Edit Schedule use cases. A Front of House / Kitchen Manager (referred to in diagram as Manager) can Create Schedule. A Manager can Edit Schedule. The Schedule Information resulting from the Create Schedule and Edit Schedule use cases is stored in the Schedule Store and Employee Hours Summary data store. Each user (referred to in diagram as All Users) can view the stored Schedule Information using the View Schedule use case.

### Swap Shift Subsystem
![DataFlow_Level2_Schedule-Page-5](https://github.com/Uvic-SENG321Spring2024/team8-developer/assets/75967325/86a33920-d99d-4426-9ab6-a9b993fb59e1)

All Users represent any user of the system and can be any user classes defined in User Class and Characteristics. All Users are able to Request Shift Swap. A Manager can Send Swap Response based on that Shift Swap Request. Resulting in the user who submitted the request being able to view the response, and updating the Schedule Store with the modified Schedule Information.

# 10 Appendix <a name="appendix"></a>

No appendices for this document.
