## Disease and Infection Research Database

# SQL project for Hunter's CSCI 435 Database class (FOR A QUICK UNDERSTANDING OF THIS DATABASE, PLEASE VIEW ER AND RELATION DIAGRAM IN REPO)

This is a Disease and Infection Research database. The use case is any research foundation tasked with finding new, researching, and containing potentially dangerous disease and virus. Of course, to do this the foundation would need a way to track everything about employees, departments, sites, and research logs. The foundation may also need to keep track of disease dangers, their safety protocols and more importantly, any breaches made to safety.
	To allow foundations to do this we have come up with the following entities:
1.	Object: The disease or infection to be researched. The attributes of this entity are:

  a.	Object Number: The unique key number of the disease/infection.

  b.	Breach Status: Simply active or not active. Used to quickly query what infections/diseases are breached or not.

  c.	Danger level: To prioritize safety of these entities, we have a danger level for them.

  d.	Description: Name/Type

  e.	Containment

  f.	Difficulty: How difficult is it to contain.

  g.	Special Care: Any special instructions that are needed to for properly containing these entities.

2.	Department: For the different departments for different types of diseases and infections. The attributes for this entity are:

  a.	Dnum: The unique department key number.

  b.	Dname: Name of the department.

  c.	Description: A small description of what the department is responsible for.

  d.	Location: Address of department office.

  e.	Phone Number: Department phone number.

3.	Site: Sites are where single disease/infections are researched. The attributes for this entity are:

  a.	Snum: The unique site key number.

  b.	Location: Address of the site.

  c.	Director: Name of director who manages this site.

  d.	Phone: Phone number of the site.

4.	Mission: This entity is for the assignment of missions for Agents. Generally, missions for agents are going out and looking for new infections/diseases. With this entity we can quickly query what missions are still active, which are closed, what object the missions are trying to find, and what Agents are assigned to them. The attributes for this entity are:

  a.	Mission Number: The unique mission key number.

  b.	Status: Active in the case the mission is not over, and inactive for the case the mission is over.
5.	Employee info: Stores important information for all types of employees. The attributes for this entity are:

  a.	SSN: Unique social security number of employee. Used as key attribute.

  b.	Name: First and Last name of employee.

  c.	Address: Current place of residence of employee.

  d.	DOB: Date of birth of employee. 

  e.	Phone Number: Phone number of employee.

6.	Agent: The on-field employees that work for departments. These agents are assigned missions to find new disease/infection to be researched at sites by researchers. The attributes for this entity are:

  a.	A_ID: The unique agent key number.

  b.	Mobile Task Force Number: The team number they are a part of.

7.	Director: Department managers. Since departments have sites, they are managers of these sites as well. The attributes for this entity are:

  a.	D_ID: The unique director key number.

8.	Researcher: Researches research objects at sites. The attributes for this entity are:

  a.	R_ID: The unique researcher key number.

  b.	Position: The position of the researcher. Some researchers may be of more senior position than others.

9.	Research Log: This weak entity stores researchers logs on object. Logs contain valuable information about the research and development.The attributes for this entity are:

  a.	Log Number: The unique foreign Key number.

  b.	Date: Date of log.

  c.	Equipment: Equipment used to conduct research.

  d.	Result: Result of research done.

10.	Breach Log: This weak entity stores information on security breaches for objects. Logs contain valuable information on breaches, and their affects. The attributes for this entity are:

  a.	Log Number: The unique foreign Key number.

  b.	Date: Date of breach.

  c.	Result: Results of breach. This can include any casualties or number of people infected.

#Of course, entities alone are not enough to create this database. How are these entities related? The following are the relations of our design:

  1.	To start off any one Department can have many Sites. Sites must have a department, but departments may not have any sites. This case is for the possibility of a department that has not found any disease or infect yet.

  2.	Departments are managed by Directors. Directors must manage a Departments, and all departments must have a director. Since departments have Sites, Sites share the same Director that manages their parent Department. 

  3.	Agents work in Departments. One Agent works for one Department. A Department has many Agents. Agents must have a Department and Departments must have Agents.  

  4.	Agents have a mission. A mission has many Agents working towards them, but Agents only work for one Mission at a time. Missions must have Agents, and Agents must work towards a Mission.

  5.	Researchers research objects (infections/diseases) at sites. Objects must have researchers, but researchers may currently not have a site. Objects need many researchers but researches only research one object at a given time.

  6.	Sites must have researchers but a researcher may not have a site. Sites have many researches, but a researcher only works for one site.

  7.	Researchers may have research logs. This means that research logs are a weak entity take its primary key from researcher ID. One researcher may have many research logs.

  8.	Research logs contain Object. Objects may have many research logs, but research logs are about one object. Research logs must contain an object, but objects do not need to contain research objects.

  9.	One Object may have many breach logs. Breach log is a weak entity that receives its primary key from the Object that was breached. Breach logs must contain a objects, but an object may not have a breach log (in case a breach has not occurred). Many Breach Logs are written by the director that manages the Site that houses the Object.
  
  10.	All types of employees (Researcher, Agent, Director) must have an Employee info. Employee info is a generalization made for the specialization of different types of employees. 

