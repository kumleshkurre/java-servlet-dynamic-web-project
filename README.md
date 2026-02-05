# 🌐 Java Servlet Dynamic Web Project

This project demonstrates how to create a **Java Servlet-based Dynamic Web Application** using **Eclipse IDE**, **HTML**, **Servlets**, and **Apache Tomcat**.  
User input is collected through an HTML form and processed using a Java Servlet.

---

## 🚀 Features
- Dynamic Web Project using Eclipse
- Servlet creation with web.xml configuration
- HTML form to Servlet communication
- GET request handling
- Apache Tomcat deployment

---

## 🛠️ Technologies Used
- Java (Servlet)
- HTML5
- Eclipse IDE
- Apache Tomcat 10
- Jakarta Servlet API

---

## 📂 Project Structure
```js
ProjectName
└── src
└── src/main/java
│ └── CSkumlesh
│ └── Kurre.java
└── src/main/webapp
├── index.html
└── WEB-INF
└── web.xml
```

---

## 🧩 Project Setup Steps

### 1️⃣ Create Dynamic Web Project
- Open **Eclipse**
- File → New → Dynamic Web Project
- ✔ Select **Generate web.xml**
- Choose **Apache Tomcat**
- Click **Finish**

---

### 2️⃣ Create Servlet
1. Go to **Java Resources**
2. Right-click on `src/main/java`
3. New → Servlet
4. Enter:
   - Package Name: `CSkumlesh`
   - Class Name: `Kurre`
5. Click **Next → Next**
6. ✔ Select `doGet()`
7. Finish

---
### 3️⃣ Create HTML Page
📍 Location: `src/main/webapp/index.html`

```css
html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Servlet Page</title>
</head>
<body>
<center>
<h1>This is My Servlet Page</h1>

<form action="Kurre" method="GET">
  Name: <input type="text" name="nm">
  <input type="submit" value="SEND">
</form>

</center>
</body>
</html>
```
### 4️⃣ Servlet Code (Kurre.java)
📍 Location: src/main/java/CSkumlesh/Kurre.java
```js
package CSkumlesh;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

/**
 * Servlet implementation class Kurre
 */
@WebServlet("/Kurre")
public class Kurre extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public Kurre() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		    Connection con;
		    Statement stmt;     // select query use
		    ResultSet rs;       // data store
		    try {
	            // Database Connection
		    	String url= "jdbc:postgresql://localhost:5432/your_database_name";
		    	String user= "your_username";
		    	String pwd= "YOUR_PASSWORD";
		    	Class.forName("org.postgresql.Driver");
	            con = DriverManager.getConnection(url,user,pwd);
	            System.out.println("Connection Successful");

	            // Create Statement
	            stmt = con.createStatement();

	            // Execute Query
	            rs = stmt.executeQuery("select * from contact");

	            while (rs.next()) {
	            	System.out.println(rs.getString("name")+" "+rs.getString("mob"));
	            	 out.println("<h1>" + rs.getString("name")+" "+rs.getString("mob") + "</h1>");
	            }

	        } catch (Exception e) {
	            System.out.println("Error : " + e);
	        }
	    }

}

```
## Second Program Insert Qury Add
### 1️⃣ Create HTML Page
📍 Location: `src/main/webapp/index.html`
```css
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<center>
<form action="Servlent" method="Get">
<h1>THIS IS MY JAVA WEB PAGE</h1>
<form action="Servlent" method="Get">
<label>Name</label> <input type="text"name="name"><br><br> 
<label>Email</label> <input type="text"name="email"><br><br> 
<label>Mobail</label> <input type="text"name="mobail"><br><br> 
<label>Age</label> <input type="text"name="age"><br><br> 
<label>City</label> <input type="text"name="city"><br><br> 
<input type="submit" value="Submit">        <!--  // jo value server pe submit hota hai kisi na kisi key ka agenst hota hai -->
</form>
</center>                                    <!--jo bhi requst ham insert karenga wo jsp page me redarect hoga-->
</body>
</html>
```
### 2️⃣ Servlet Code (Servlent.java)
📍 Location: src/main/java/Servlentdataconnection/Servlent.java
```jss
package Servlentdataconnection;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;


@WebServlet("/Servlent")
public class Servlent extends HttpServlet {
	private static final long serialVersionUID = 1L;
    
    public Servlent() {
        super();
        // TODO Auto-generated constructor stub
        
    }
      protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		 //TODO Auto-generated method stub
    	  
        response.getWriter().append("Served at: ").append(request.getContextPath());
        response.setContentType("text/html"); 
		String name=request.getParameter("name");
		String email=request.getParameter("email");     //data lake racho
		String mobail=request.getParameter("mobail");
		int age=Integer.parseInt(request.getParameter("age"));
		String city=request.getParameter("city");
		
		    //database connection
		         Connection con;
	             PreparedStatement psmt;  //insert update delete
		 try {
	    	  String url= "jdbc:postgresql://localhost:5432/your_database_name";
		    	String user= "your_username";
		    	String pwd= "YOUR_PASSWORD";
	    	   Class.forName("org.postgresql.Driver");
	    	   con=DriverManager.getConnection(url,user,pwd);
	    	 
	    	   
	    	  System.out.println("Connection Successfull");   //connection check
	    	  
	    	  //Insert Qury
	    	  psmt=con.prepareStatement("insert into contact(name,email,mob,age,city)values(?,?,?,?,?)");
	    	  psmt.setString(1,name);
	    	  psmt.setString(2,email);
	    	  psmt.setString(3,mobail);      //data ko dsatbase me insert karo 
	    	  psmt.setInt(4,age);
	    	  psmt.setString(5,city);
	    	  
	    	  int r=psmt.executeUpdate();  // executeUpdate 0 and 1 value return kerta hai
	    	  
	    	  if(r>0) {           //r 0 se beda hai
	    		     System.out.println("Insert Success");
	    	  }else {
	    		     System.out.println("Insert Failed");
	    	  }
	       }catch(Exception e) {
	    	   System.out.println(e);
	       }
		
	}
}
```

## 🎯 Learning Outcomes
- Creating Dynamic Web Projects
- Using web.xml with Servlets
- HTML to Servlet communication
- Handling GET requests
- Deploying Servlet applications on Tomcat

## 👨‍💻 Author

Kumlesh Kurre
Java | Servlet | Web Development
