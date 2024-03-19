# Freelances

#index.html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Company CDN</title>

    <!-- CSS -->
    <link rel="stylesheet" href="css/style.css" />

    <!-- Boxicons CSS -->
    <link
      href="https://unpkg.com/boxicons@2.1.2/css/boxicons.min.css"
      rel="stylesheet"
    />
  </head>
  <body>
    <nav>
      <div class="logo">
        <i class="bx bx-menu menu-icon"></i>
        <span class="logo-name">Company CDN</span>
      </div>

      <div class="sidebar">
        <div class="logo">
          <i class="bx bx-menu menu-icon"></i>
          <span class="logo-name">Company CDN</span>
        </div>

        <div class="sidebar-content">
          <ul class="lists">
            <li class="list">
              <a href="index.html" class="nav-link">
                <i class="bx bx-home-alt icon"></i>
                <span class="link">Dashboard</span>
              </a>
            </li>

             <li class="list">
              <a href="viewuser.php" class="nav-link">
                <i class="bx bx-folder-open icon"></i>
                <span class="link">Freelancers</span>
              </a>
            </li>

            <li class="list">
              <a href="registeruser.php" class="nav-link">
                <i class="bx bx-bell icon"></i>
                <span class="link">Register User</span>
              </a>
            </li>
            
          </ul>

          <div class="bottom-cotent">
            <!-- <li class="list">
              <a href="#" class="nav-link">
                <i class="bx bx-cog icon"></i>
                <span class="link">Settings</span>
              </a>
            </li> -->
            <li class="list">
              <a href="#" class="nav-link">
                <i class="bx bx-log-out icon"></i>
                <span class="link">Logout</span>
              </a>
            </li>
          </div>
        </div>
      </div>
    </nav>

    <section class="overlay"></section>

    <script>
      const navBar = document.querySelector("nav"),
        menuBtns = document.querySelectorAll(".menu-icon"),
        overlay = document.querySelector(".overlay");

      menuBtns.forEach((menuBtn) => {
        menuBtn.addEventListener("click", () => {
          navBar.classList.toggle("open");
        });
      });

      overlay.addEventListener("click", () => {
        navBar.classList.remove("open");
      });
    </script>
  </body>
</html>

#viewuser.php
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Company CDN</title>

    <!-- CSS -->
    <link rel="stylesheet" href="css/style.css" />

    <!-- Boxicons CSS -->
    <link
      href="https://unpkg.com/boxicons@2.1.2/css/boxicons.min.css"
      rel="stylesheet"
    />

    <style>
      table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 20px;
    }

    th, td {
      padding: 8px;
      text-align: left;
      border-bottom: 1px solid #ddd;
    }

    th {
      background-color: #f2f2f2;
    }

    /* Adjust content positioning */
    .content {
      margin-top: 70px; /* Adjust this value according to your navigation menu height */
    }

    /* Button style */
    .btn {
      display: inline-block;
      padding: 8px 16px;
      background-color: #007bff;
      color: #fff;
      text-decoration: none;
      border-radius: 4px;
    }

    .btn:hover {
      background-color: #0056b3;
    }

     .shifted {
    margin-left: 250px; 
  }
    </style>
  </head>
  <body>
    <nav>
      <div class="logo">
        <i class="bx bx-menu menu-icon"></i>
        <span class="logo-name">Company CDN</span>
      </div>

      <div class="sidebar">
        <div class="logo">
          <i class="bx bx-menu menu-icon"></i>
          <span class="logo-name">Company CDN</span>
        </div>

        <div class="sidebar-content">
          <ul class="lists">
             <li class="list">
              <a href="index.html" class="nav-link">
                <i class="bx bx-home-alt icon"></i>
                <span class="link">Dashboard</span>
              </a>
            </li>

             <li class="list">
              <a href="viewuser.php" class="nav-link">
                <i class="bx bx-folder-open icon"></i>
                <span class="link">Freelancers</span>
              </a>
            </li>

            <li class="list">
              <a href="registeruser.php" class="nav-link">
                <i class="bx bx-bell icon"></i>
                <span class="link">Register User</span>
              </a>
            </li>
          </ul>

          <div class="bottom-cotent">
            <!-- <li class="list">
              <a href="#" class="nav-link">
                <i class="bx bx-cog icon"></i>
                <span class="link">Settings</span>
              </a>
            </li> -->
            <li class="list">
              <a href="#" class="nav-link">
                <i class="bx bx-log-out icon"></i>
                <span class="link">Logout</span>
              </a>
            </li>
          </div>
        </div>
      </div>

    </nav>

    <br>

       <div class="content" id="content">
        <h2>Registered Users</h2>
        <br><br>
        <table>
            <thead>
                <tr>
                    <th>Username</th>
                    <th>Email</th>
                    <th>Phone Number</th>
                    <th>Skillsets</th>
                    <th>Hobby</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <?php
                include 'connection.php';

                $sql = "SELECT * FROM users";
                $result = $conn->query($sql);

                if ($result->num_rows > 0) {
                    while($row = $result->fetch_assoc()) {
                        echo "<tr>";
                        echo "<td>" . $row["username"] . "</td>";
                        echo "<td>" . $row["email"] . "</td>";
                        echo "<td>" . $row["phone_number"] . "</td>";
                        echo "<td>" . $row["skillsets"] . "</td>";
                        echo "<td>" . $row["hobby"] . "</td>";
                        echo "<td>";
                       echo "<a href='javascript:void(0);' onclick='showUpdateConfirmation(" . $row["id"] . ")' class='btn' style='margin-right: 10px;'><i class='bx bx-pencil'></i></a>";
                        echo "<a href='delete_user.php?id=" . $row["id"] . "' class='btn' style='background-color: #dc3545; margin-right: 10px;'><i class='bx bx-trash'></i></a>";


                        echo "</td>";
                        echo "</tr>";
                    }
                } else {
                    echo "<tr><td colspan='6'>No users found</td></tr>";
                }

                $conn->close();
                ?>
            </tbody>
        </table>
        <!-- <a href="add_user.php" class="btn">Register User</a> -->
    </div>


    <section class="overlay"></section>

  
        <script>

          function showUpdateConfirmation(userId) {
        var confirmation = confirm("Are you sure you want to update this user?");
        if (confirmation) {
            // Redirect to update_user.php with user ID
            window.location.href = "update_user.php?id=" + userId;
        }
    }
      const navBar = document.querySelector("nav"),
        menuBtns = document.querySelectorAll(".menu-icon"),
        overlay = document.querySelector(".overlay"),
        content = document.querySelector(".content"); 

      menuBtns.forEach((menuBtn) => {
        menuBtn.addEventListener("click", () => {
          navBar.classList.toggle("open");
          content.classList.toggle("shifted"); 
        });
      });

      overlay.addEventListener("click", () => {
        navBar.classList.remove("open");
        content.classList.remove("shifted"); 
      });
    </script>

  </body>
</html>

#registeruser.php
<?php
require 'connection.php';


$successMessage = ''; 

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $usernames = $_POST['usernames'];
    $email = $_POST['email'];
    $phone = $_POST['phone']; 
    $skill = $_POST['skill'];
    $hobby = $_POST['hobby'];
  
    $query = "INSERT INTO users (username, email, phone_number, skillsets, hobby) VALUES ('$usernames', '$email', '$phone', '$skill', '$hobby')";
    
    $stmt = mysqli_query($conn, $query);

    if ($stmt) {
        $successMessage = 'New user successfully added!';
    } else {
        $successMessage = 'Failed to add new user. Please try again.';
    }
}
?>

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Company CDN</title>

    <link rel="stylesheet" href="css/style.css" />

    <link
      href="https://unpkg.com/boxicons@2.1.2/css/boxicons.min.css"
      rel="stylesheet"
    />

    <style>

       .add-user-container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 8px;
            background-color: #f9f9f9;
        }

        label {
            font-weight: bold;
        }

         input,textarea {
            width: 100%;
            padding: 8px;
            margin-top: 6px;
            margin-bottom: 16px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }

        button[type="submit"] {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button[type="submit"]:hover {
            background-color: #0056b3;
        }

     .shifted {
    margin-left: 250px; 
  }
    </style>
  </head>
  <body>
    <nav>
      <div class="logo">
        <i class="bx bx-menu menu-icon"></i>
        <span class="logo-name">Company CDN</span>
      </div>

      <div class="sidebar">
        <div class="logo">
          <i class="bx bx-menu menu-icon"></i>
          <span class="logo-name">Company CDN</span>
        </div>

        <div class="sidebar-content">
          <ul class="lists">
            <li class="list">
              <a href="index.html" class="nav-link">
                <i class="bx bx-home-alt icon"></i>
                <span class="link">Dashboard</span>
              </a>
            </li>

             <li class="list">
              <a href="viewuser.php" class="nav-link">
                <i class="bx bx-folder-open icon"></i>
                <span class="link">Freelancers</span>
              </a>
            </li>

            <li class="list">
              <a href="registeruser.php" class="nav-link">
                <i class="bx bx-bell icon"></i>
                <span class="link">Register User</span>
              </a>
            </li>
            
          </ul>

          <div class="bottom-cotent">
            <!-- <li class="list">
              <a href="#" class="nav-link">
                <i class="bx bx-cog icon"></i>
                <span class="link">Settings</span>
              </a>
            </li> -->
            <li class="list">
              <a href="#" class="nav-link">
                <i class="bx bx-log-out icon"></i>
                <span class="link">Logout</span>
              </a>
            </li>
          </div>
        </div>
      </div>

    </nav>

    <br><br>

    <div class="add-user-container" id="add-user-container">
        <h2 style="text-align: center;">Register New Freelancers</h2><br>

        <form action="" method="post">
            <label for="usernames">Username:</label><br>
            <input type="usernames" id="usernames" name="usernames" required><br>

            <label for="email">Email:</label><br>
            <input type="email" id="email" name="email" required><br>

            <label for="phone">Phone Number:</label><br>
            <input id="phone" name="phone" required><br>

            <label for="skill">Skillsets:</label><br>
            <input id="skill" name="skill" required><br>

            <label for="hobby">Hobby:</label><br>
            <input id="hobby" name="hobby" required><br>

            <br>

            <button type="submit">Submit</button>
        </form>
        
    </div>

       
                
        <!-- <a href="add_user.php" class="btn">Register User</a> -->
    </div>


    <section class="overlay"></section>

  
        <script>

            window.onload = function() {
            var successMessage = "<?php echo $successMessage; ?>";
            if (successMessage !== '') {
                alert(successMessage);
            }
        };

          const navBar = document.querySelector("nav"),
          menuBtns = document.querySelectorAll(".menu-icon"),
          overlay = document.querySelector(".overlay"),
          content = document.querySelector(".content"); 

          menuBtns.forEach((menuBtn) => {
          menuBtn.addEventListener("click", () => {
            navBar.classList.toggle("open");
            content.classList.toggle("shifted"); 
          });
        });

        overlay.addEventListener("click", () => {
        navBar.classList.remove("open");
        content.classList.remove("shifted"); 
      });
    </script>

  </body>
</html>

#updateuser.php
<?php
include 'connection.php';

$errorMessage = ''; 
$successMessage = '';

if(isset($_GET['id']) && !empty($_GET['id'])) {
    $id = $_GET['id'];
    
    $sql = "SELECT * FROM users WHERE id = $id";
    $result = $conn->query($sql);
    
    if ($result->num_rows > 0) {
        $user = $result->fetch_assoc();
    } else {
        echo "User not found";
        exit();
    }
} else {
    echo "Invalid user ID";
    exit();
}

// Check if form is submitted
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Retrieve form data
    $usernames = $_POST['usernames'];
    $email = $_POST['email'];
    $phone = $_POST['phone'];
    $skillsets = $_POST['skill'];
    $hobby = $_POST['hobby'];

    // Update user information
    $sql = "UPDATE users SET username='$usernames', email='$email', phone_number='$phone', skillsets='$skillsets', hobby='$hobby' WHERE id=$id";

    if ($conn->query($sql) === TRUE) {
         $successMessage = 'User successfully deleted!';
    } else {
        $errorMessage = 'Failed to delete user. Please try again.';
    }
}

$conn->close();


?>

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Company CDN</title>

    <link rel="stylesheet" href="css/style.css" />

    <link
      href="https://unpkg.com/boxicons@2.1.2/css/boxicons.min.css"
      rel="stylesheet"
    />

    <style>

       .add-user-container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 8px;
            background-color: #f9f9f9;
        }

        label {
            font-weight: bold;
        }

         input,textarea {
            width: 100%;
            padding: 8px;
            margin-top: 6px;
            margin-bottom: 16px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }

        button[type="submit"] {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button[type="submit"]:hover {
            background-color: #0056b3;
        }

     .shifted {
    margin-left: 250px; 
  }
    </style>
  </head>
<body>
     <div class="add-user-container" id="add-user-container">
        <h2 style="text-align: center;">Register New Freelancers</h2><br>

        <form action="" method="post">
            <label for="usernames">Username:</label><br>
            <input type="text" id="usernames" name="usernames" value="<?php echo $user['username']; ?>" required><br>


            <label for="email">Email:</label><br>
            <input type="email" id="email" name="email" value="<?php echo $user['email']; ?>" required><br>

            <label for="phone">Phone Number:</label><br>
            <input id="phone" name="phone" value="<?php echo $user['phone_number']; ?>" required><br>

            <label for="skill">Skillsets:</label><br>
            <input id="skill" name="skill" value="<?php echo $user['skillsets']; ?>" required><br>

            <label for="hobby">Hobby:</label><br>
            <input id="hobby" name="hobby" value="<?php echo $user['hobby']; ?>" required><br>

            <br>

            <button type="submit">Submit</button>
        </form>

        <script>
             window.onload = function() {

            var successMessage = "<?php echo $successMessage; ?>";
            if (successMessage !== '') {
                alert(successMessage);
                window.location.href = 'viewuser.php';
            }
        };
        </script>
        
</body>
</html>

#deleteuser.php
<?php
include 'connection.php';

$errorMessage = ''; 
$successMessage = ''; 

if(isset($_GET['id']) && !empty($_GET['id'])) {
    $id = $_GET['id'];
    
    $sql = "DELETE FROM users WHERE id = $id";
    if ($conn->query($sql) === TRUE) {
        $successMessage = 'User successfully deleted!';
    } else {
        $errorMessage = 'Failed to delete user. Please try again.';
    }
} else {
    $errorMessage = 'Invalid user ID';
}

$conn->close();

echo "<script>
        alert('$successMessage');
        window.location.href = 'viewuser.php';
      </script>";
?>
#connection.php
<?php
$servername = "localhost";
$username = "root"; 
$password = ""; 
$dbname = "freelancer"; 

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>

#style.css
/* Google Fonts - Poppins */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}
body {
  min-height: 100%;
  background: #e3f2fd;
}
nav {
  position: fixed;
  top: 0;
  left: 0;
  height: 70px;
  width: 100%;
  display: flex;
  align-items: center;
  background: #fff;
  box-shadow: 0 0 1px rgba(0, 0, 0, 0.1);
}
nav .logo {
  display: flex;
  align-items: center;
  margin: 0 24px;
}
.logo .menu-icon {
  color: #333;
  font-size: 24px;
  margin-right: 14px;
  cursor: pointer;
}
.logo .logo-name {
  color: #333;
  font-size: 22px;
  font-weight: 500;
}
nav .sidebar {
  position: fixed;
  top: 0;
  left: -100%;
  height: 100%;
  width: 260px;
  padding: 20px 0;
  background-color: #fff;
  box-shadow: 0 5px 1px rgba(0, 0, 0, 0.1);
  transition: all 0.4s ease;
}
nav.open .sidebar {
  left: 0;
}
.sidebar .sidebar-content {
  display: flex;
  height: 100%;
  flex-direction: column;
  justify-content: space-between;
  padding: 30px 16px;
}
.sidebar-content .list {
  list-style: none;
}
.list .nav-link {
  display: flex;
  align-items: center;
  margin: 8px 0;
  padding: 14px 12px;
  border-radius: 8px;
  text-decoration: none;
}
.lists .nav-link:hover {
  background-color: #4070f4;
}
.nav-link .icon {
  margin-right: 14px;
  font-size: 20px;
  color: #707070;
}
.nav-link .link {
  font-size: 16px;
  color: #707070;
  font-weight: 400;
}
.lists .nav-link:hover .icon,
.lists .nav-link:hover .link {
  color: #fff;
}
.overlay {
  position: fixed;
  top: 0;
  left: -100%;
  height: 1000vh;
  width: 200%;
  opacity: 0;
  pointer-events: none;
  transition: all 0.4s ease;
  background: rgba(0, 0, 0, 0.3);
}
nav.open ~ .overlay {
  opacity: 1;
  left: 260px;
  pointer-events: auto;
}

table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 20px;
    }

    th, td {
      padding: 8px;
      text-align: left;
      border-bottom: 1px solid #ddd;
    }

    th {
      background-color: #f2f2f2;
    }

    /* Button style */
    .btn {
      display: inline-block;
      padding: 8px 16px;
      background-color: #007bff;
      color: #fff;
      text-decoration: none;
      border-radius: 4px;
    }

    .btn:hover {
      background-color: #0056b3;
    }
