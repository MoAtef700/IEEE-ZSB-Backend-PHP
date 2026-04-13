Task 5 - PHP Security 
________________________________________
1. SQL Injection (SQLi)
Definition
A vulnerability that allows attackers to manipulate SQL queries by injecting malicious input.
Attack Scenario
$email = $_POST['email'];
$query = "SELECT * FROM users WHERE email = '$email'";
Malicious Input:
' OR 1=1 --
Result: Authentication bypass
Prevention
•	Use Prepared Statements
•	Avoid direct query concatenation
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = ?");
$stmt->execute([$email]);
________________________________________
2. Cross-Site Scripting (XSS)
Definition
Injection of malicious JavaScript into web pages viewed by other users.
Attack Scenario
echo $_GET['name'];
Malicious Input:
<script>alert('Hacked')</script>
Prevention
echo htmlspecialchars($_GET['name'], ENT_QUOTES, 'UTF-8');
________________________________________
3. Reflected XSS
Definition
A type of XSS where the payload is reflected immediately in the response.
Attack Scenario
User clicks a crafted malicious URL.
Prevention
•	Escape output
•	Validate inputs
________________________________________
4. Stored XSS
Definition
Malicious script stored in database and executed for all users.
Attack Scenario
Comment system stores script and displays it later.
Prevention
•	Sanitize inputs
•	Escape outputs
________________________________________
5. Cross-Site Request Forgery (CSRF)
Definition
Forcing a logged-in user to perform unintended actions.
Attack Scenario
User visits malicious site that triggers a request automatically.
Prevention
Step 1: Generate Token
$_SESSION['token'] = bin2hex(random_bytes(32));
Step 2: Add to Form
<input type="hidden" name="token" value="<?php echo $_SESSION['token']; ?>">
Step 3: Validate
if ($_POST['token'] !== $_SESSION['token']) {
    die("Invalid CSRF token");
}
________________________________________
6. File Upload Vulnerabilities
Definition
Uploading harmful files to the server.
Attack Scenario
Attacker uploads a malicious PHP file.
Prevention
•	Restrict file types
•	Rename files
•	Store securely
$allowed = ['jpg', 'png'];
$ext = pathinfo($_FILES['file']['name'], PATHINFO_EXTENSION);

if (!in_array($ext, $allowed)) {
    die("Invalid file type");
}
________________________________________
7. Authentication Weaknesses
Definition
Weak authentication mechanisms allow unauthorized access.
Common Problems
•	Plain text passwords
•	Weak validation
Prevention
Hash Passwords
$password = password_hash($_POST['password'], PASSWORD_DEFAULT);
Verify Passwords
password_verify($input_password, $hashed_password);
________________________________________
8. Session Hijacking
Definition
Stealing user session to gain access.
Attack Scenario
Attacker steals cookies.
Prevention
Secure Session
session_regenerate_id(true);
Protect Cookies
ini_set('session.cookie_httponly', 1);
Use HTTPS
________________________________________
Comparison Table
Attack Type	Risk Level	Prevention
SQL Injection	High	Prepared Statements
XSS	High	Escape Output
CSRF	High	CSRF Token
File Upload	Medium	Validate Files
Authentication	High	Password Hashing
Session Hijacking	High	Secure Sessions + HTTPS
________________________________________
Key Security Principles
•	Never trust user input
•	Always validate and sanitize data
•	Escape output before rendering
•	Use secure authentication methods
•	Protect sessions properly
________________________________________

