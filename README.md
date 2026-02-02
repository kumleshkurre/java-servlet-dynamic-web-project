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
```
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

```
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
```
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
## 🎯 Learning Outcomes
- Creating Dynamic Web Projects
- Using web.xml with Servlets
- HTML to Servlet communication
- Handling GET requests
- Deploying Servlet applications on Tomcat

## 👨‍💻 Author

Kumlesh Kurre
Java | Servlet | Web Development
