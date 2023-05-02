Download Link: https://assignmentchef.com/product/solved-cnt4714-project-four
<br>
<strong>Title:</strong>  “Project Four: Developing A Three-Tier Distributed Web-Based Application”

<strong>Objectives:</strong>  To incorporate many of the techniques you’ve learned so far this semester into a distributed three-tier web-based application which uses servlets and JSP technology running on a Tomcat container/server to access and maintain a persistent MySQL database using JDBC.




<strong>Description:</strong>  In this assignment you will utilize a suppliers/parts/jobs/shipments database (creation/population script available on the course assignment page) as the back-end database. Frontend access to this database by the client will occur through a single page displayed in the client’s web browser. The schema of the backend database consists of four tables with the following schemas for each table:




suppliers (<u>snum</u>, sname, status, city)  //information about suppliers           parts (<u>pnum</u>, pname, color, weight, city)  //information about parts         jobs (<u>jnum</u>, jname, numworkers, city)  //information about jobs

shipments (<u>snum, pnum, jnum</u>, quantity)  //suppliers ship parts to jobs in specific quantities




The first-tier (client-level front-end) of your application will be a JSP page that allows the client to enter SQL commands into a window (i.e. a form) and submit them to the server application for processing.  The front-end (<strong>and only the front-end</strong>) will utilize JSP technology.   The client front-end will provide the user a simple form in which they will enter a SQL command (any DML, DDL, or DCL command could theoretically be entered by the user, however we will restrict to queries, insert, update, replace, and delete commands).  The front-end will provide only two buttons for the user, an Execute button that will cause the execution of the SQL command they enter, and a Reset button that simply clears any content in the form input area.  The client front-end will run on any web-based browser that you would like to use.  You can elect to have a default query or not, it is entirely your decision.  The application will connect to the backend database as a root user client.




The second-tier servlet, in addition to handling the SQL command interface will also implement the business/application logic.  This logic will increment by 5, the status of a supplier anytime that supplier is involved in the insertion/update of a shipment record in which the quantity is greater than or equal to 100.  Note that any update of quantity &gt;= 100 will affect any supplier involved in a shipment with a quantity &gt;= 100.  The example screen shots illustrate this case.  An insert of a shipment tuple (S5, P6, J7, 400) will cause the status of every supplier who has a shipment with a quantity of 100 or greater to be increased by 5.  In other words, even if a supplier’s shipment is not directly affected by the update, their status will be affected if they have any shipment with quantity &gt;= 100.  <strong>(See page 9 for a bonus problem that implements a modified version of this business rule.)</strong>  The business logic of the second tier will reside in the servlet on the Tomcat web-application server (server-side application).  This means that the business logic is not to be implemented in the DBMS via a trigger.




The third-tier (back-end) is the persistent MySQL database described above and is under control of the MySQL DBMS server.  All you need to do with the database is run the creation/population script.  See the important note below concerning when/how to re-run this script for your final submission.

<strong>References:  </strong>

Notes:  Lecture Notes for MySQL installation and use.  Documentation for MySQL available at: <a href="https://www.mysql.com/">http://www.mysql.com</a><a href="https://www.mysql.com/">.</a> More information on JDBC can be found at: <a href="http://www.oracle.com/technetwork/java/javase/jdbc/index.html">http://www.oracle.com/technetwork/java/javase/jdbc/index.html</a> .  More information on Tomcat can be found at <a href="https://tomcat.apache.org/">http://tomcat.apache.org</a><a href="https://tomcat.apache.org/">.</a>  Lecture Notes for Servlets.    Lecture Notes for JSPs.




<strong>Restrictions: </strong>

Your source file shall begin with comments containing the following information:

<strong>/*  Name:   </strong>

<strong>     Course: CNT 4714 – Fall 2019 – Project Four </strong>

<strong>     Assignment title:  A Three-Tier Distributed Web-Based Application      Date:  November 17, 2019 */ </strong>

<strong>Input Specification:</strong>  The suppliers/part/jobs/shipments database that is created/populated by the script project4dbscript.sql, is the back-end to this application.  All other input comes from the front-end client submitted to the application server based servlet entered as either queries or updates to this database.  The set of commands that you are to execute against this database are included in the project4commands.sql file available on the course homework page.  I do not expect your front-end to execute the script.  You’ll need to execute the commands in this script one at a time in your application (copy and paste!).  I’ve put them into a script file for convenience and so that you can run the script in the MySQL Workbench if you’d like to compare/see the result sets for each

user command.




<strong>Output Specification:  </strong>All output is generated by the servlet and should appear in the user’s browser as a text/html page presented to the user.  <strong>IMPORTANT:</strong> Be sure to re-run the project4 database creation/population script before you begin creating your screen shots for submission.  By doing so you will ensure that the database is in its initial state so that all update operations will produce the values we are expecting to see in your result outputs.




<strong>Deliverables: </strong>

<ul>

 <li>You should submit your entire webapps folder from Tomcat for this program. If you submit the entire folder, then all of the files necessary to execute your web application will be included with the directory structure intact.  Submit this via WebCourses no later than <strong>11:59pm Sunday November 17, 2019</strong>.</li>

 <li>The following 14 screen shots must be submitted along with your webapps folder. (You can include the screenshots in the top-level of your webapps folder if you’d like, just be sure to include a note that you’ve done so.)

  <ol>

   <li>Command 1</li>

   <li>Command 2A</li>

   <li>Command 2B – output may vary here</li>

   <li>Command 2C</li>

   <li>Command 3A – output may vary here</li>

   <li>Command 3B</li>

   <li>Command 3C – output may vary here</li>

   <li>Command 3D</li>

   <li>Command 4</li>

   <li>Command 5A</li>

   <li>Command 5B – output may vary here</li>

   <li>Command 5C</li>

   <li>Command 5D</li>

   <li>Command 6</li>

  </ol></li>

</ul>




<strong>Additional Information:</strong>

Be very careful when setting up the directory structures required for the web applications running under your server (Tomcat 9.0.24 or later).  See the course notes on servlets for the exact directory structure that must be developed.




<strong>Important:</strong>  Please name your webapp: <strong>Project4.  </strong>Let the TAs know if you are doing the bonus problem by attaching a note to your WebCourses submission.




<strong>Schematic Overview of Project Components:</strong>




<strong>Some screen shots illustrating the application. </strong>

<strong> </strong>

Main client screen (initial configuration using a default query string):

Client simply clicks the “Execute Command” button and the SQL command in the form is executed:




Client makes a mistake entering an SQL command:




Inserts and updates may cause changes to the supplier status field (business logic is triggered) as shown below:




Client issues the following insert command:




Alert message when an update to the quantity field in the shipments table has caused an update of a supplier’s status in the supplier table.  Note that in my application, I used this alert message any time the business logic was tested even if it did not trigger any updates.  This means that this message would appear with different values even if no rows are updated.




After executing update command (the previous insert), client runs select * from suppliers.







<strong>BONUS PROBLEM:  15 points </strong>




Instead of allowing any update/insert of a quantity &gt;= 100 to affect any supplier with a shipment involving a quantity &gt;= 100, adjust the business logic portion of your application so that an insert/update of a quantity greater than 100, causes a change to the status of only those suppliers directly affected by the update.  For example, using the case shown above, when inserting the row (S5, P6, J7, 400) into the shipments table, only the status of supplier S5 should be increased by 5 (see screen shot below).  However, an update such as: UPDATE shipments SET quantity = quantity + 50 WHERE pnum = “P3”, would increase by 5 the status of every supplier who ships part P3 in a quantity &gt;= 100 after the update has been issued.




NOTE: If you elect to do the bonus problem, submit only this version of your application.  Do not also submit the non-bonus problem version.  Let the TAs know if you’ve elected to do the bonus problem or not.

Immediately after issuing the update (insert above), the user reruns the select * from suppliers query:


