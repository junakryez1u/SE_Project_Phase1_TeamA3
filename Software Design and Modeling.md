1. Software Architecture

	LOSER submits a lost item through the form on the Homepage (Frontend) 
  Request goes to Backend (Django) 
  Backend checks Database ,validates data and saves the lost item report
  Backend sends result back to Frontend 
  Loser confirms submission → stored in Database 

	FINDER submits a found item through the form on the Homepage (Frontend) 
  Request goes to Backend (Django) 
  Backend checks Database ,checks if a matching lost item exists, saves the found item report
  Backend sends result back to Frontend 
  Finder confirms submission → stored in Database 

	CUSTOMER logs in and searches for a matching item (Frontend) 
  Request goes to Backend (Django) 
  Backend checks Database (queries Items table by item type and location) 
  Backend sends result back to Frontend 
  Customer views matching items → displayed on Frontend

	BUSINESS registers and manages lost item inventory (Frontend) 
  Request goes to Backend (Django) 
  Backend checks Database (checks if email exists, fetches all items linked to that Business) 
  Backend sends result back to Frontend 
  Business updates or resolves an item → updated in Database 




Component Diagram (UML)

![UML](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/UML%20DIAGRAM1.png)


2. Detailed Design
Class Diagram



Sequence Diagrams

![sequence](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/Sequence%20Diagrams.drawio.png)


3. Modeling
Use Case Diagram

![usecase](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/use%20case%20diagram.png)

Activity Diagrams

Flowchart1-submit lost or found items

![Flowchart](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/flowchart1.drawio.png)

Flowchart2-business registration

![Flowchart](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/flowchart2.drawio.png)

State Diagrams
