---
{"dg-publish":true,"permalink":"/cybr-assignment-the-system/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Aircraft Service App Scenario

- App for android tablets
- To create and maintain aircraft maintenance records
- App is called their 'Service Application'

- Many organisations consider their aircraft record to be confidential
	- Though made available to regulatory agencies
	- Don't want their competitors or general public to know details
		- Like maintenance policies/procedures
		- Or details about individual aircraft

Periodically updates are made to checklist/maintenance policies
- usually happens in response to an accident
- To prevent similar thing from happening again

## The Service Application

### Records for a Plane Include:

- Model & serial numbers of:
	- Airframe
	- Each engine
	- Each propeller
	- Each rotor
	- etc
- **When** each part was installed, inspected or serviced
- And the person who certified the work was done properly
	- Person has to have the proper certification for doing that particular tasks

### Typical Use

1. Maintenance crew checks out one or more tablets at beginning of shift
2. Service application  will display a list of tasks that need to be done.
3. Time taken for maintenance can vary, so they will do as much as they can, then people from the next shift will take out
4. When doing a service task, service application will show the maintenance records for that plane, instruction manuals for that task, and the correct checklists
5. When a worker completes a task, they must take some action (like pressing button on screen on tablet) to check that its completed'
	- Sometimes tasks will require more info (like serial number of part)
6. Crew members can take photos (using tablet camera) and attach to service records
7. When task completed, the person responsible for the task (who must be properly certified) has to sign off that the task was done correctly
8. Sometimes doing a task can result in the creation of a new task
	- Eg An inspection task may determine a part needs replacing (The service application will support this)
9. When shift is over, crew will return the tablets they used


Organisations main database of aircraft record will be updated as service is done.

#### Orgs Data Center

Will host:
- A database containing all the service record for the aircraft
- The Service Application will have to deal with records that are created by legacy systems
- While the Service Application is being used, some people will still be using the old system
- Master database of all service manual and checklist

### The Tablets

- Wifi enabled
- Wifi will be available in the organisations offices
- While on the airport field, wifi availability isn't guaranteed
- So the Service App will periodically connect to the API server to synchronise its local databases with service records/manual/checklists held in data center
- A tablet can't hold ALL the service records, will only have the ones that are needed.

