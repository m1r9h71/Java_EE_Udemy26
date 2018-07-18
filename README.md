# Java_EE_Udemy26
Creating a persistence Unit
#Before this step I set up a datasource by going to 
localhost:4848
This is Glassfish Admin. From there click on JDBC, JDBC Connection Pools and give the pool a name (AirlineDB in this case)
REsource type is javax.sql.DataSource
Database Driver Vender is Derby click NEXT.
Change the Following:
ConnectionAttributes = create=true (or :create=true depending on the version of glassfish)
Description = Database for airline application
User = Airline
DatabaseName = localhost
PortNumber = 1527 (make sure Derby server is running)
Password = make your own but remember it

PING and make sure this is succesful.

Go to JDBC Resources
JNDI Name = jdbc/airlne
PoolName = AirlineDB
Description = [leave blank]
Make sure status is ticked. Click NEXT, make sure jdbc/airline is listed.

Eclipse dataSource Explorer (TAB next to Glassfish Server in Eclipse) Right Click on Database Connections, choose NEW. 
Choose:
Derby
Name = Airline
NEXT (Make sure the driver listed is ok)
Database = airline
Host = localhost
Port no = 1527
User_Name = Airline
TICK Create Database and save password.

#** NOTE: When i came to set up the Datasource Explorer the driver was blank so i had to:
click on the +
Choose Derby Client JDBC Driver
Go to JAR list, REMOVE ALL, ADD, go to the following folder: glassfish/javadb/lib/ then chose derbyClient.jar
Click OK
Go to Properties at the bottom of the screen and fill in the details listed above (Name etc)
PING and make sure it all works. 

For this tutorial I created a new project, right clicked the project, typed facet and clicked Project Facet
ticked JPA clicked Further Config.
Platform: Generic
Type: Glassfish System Library
Connection: NONE
ok and Apply and close.

Inside the JPA Content folder, open the persistence.xml file
Type the following:
     <persistence-unit name="airline">
		  <jta-data-source>jdbc/airline</jta-data-source>
		  <properties>
		  <property name="eclipselink.ddl-generation" value="drop-and-create-tables"/>
		  </properties>
	   </persistence-unit>
  


