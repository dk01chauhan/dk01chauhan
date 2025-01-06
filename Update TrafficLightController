# Traffic-Controller-System
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Management - Traffic Controller</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha3/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            background-color: #f4f7fa;
            font-family: Arial, sans-serif;
        }

        .container {
            margin-top: 30px;
        }

        .table {
            background-color: #ffffff;
            border-radius: 10px;
            overflow: hidden;
        }

        .form-container {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        h1, h2 {
            color: #343a40;
        }

        .btn-actions {
            display: flex;
            gap: 10px;
        }

        .form-select {
            color: #495057;
        }

        .alert-message {
            margin-top: 10px;
            display: none;
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- Title -->
        <h1 class="text-center">User Management - Traffic Controller</h1>

        <!-- Alert Message -->
        <div id="alertMessage" class="alert alert-success alert-message">
            <strong>Success!</strong> User has been added successfully.
        </div>

        <!-- User List Table -->
        <h2 class="mt-4">User List</h2>
        <table class="table table-striped table-bordered">
            <thead class="table-dark">
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Role</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody id="userList">
                <!-- Dynamic User Entries will appear here -->
            </tbody>
        </table>

        <!-- Add User Form -->
        <div class="form-container mt-4">
            <h2>Add User</h2>
            <form id="userForm">
                <div class="mb-3">
                    <label for="userName" class="form-label">Name</label>
                    <input type="text" class="form-control" id="userName" placeholder="Enter full name" required>
                </div>
                <div class="mb-3">
                    <label for="userEmail" class="form-label">Email</label>
                    <input type="email" class="form-control" id="userEmail" placeholder="Enter email" required>
                </div>
                <div class="mb-3">
                    <label for="userRole" class="form-label">Role</label>
                    <select id="userRole" class="form-select" required>
                        <option value="">Choose role</option>
                        <option value="Admin">Admin</option>
                        <option value="Manager">Manager</option>
                        <option value="User">User</option>
                    </select>
                </div>
                <button type="submit" class="btn btn-success w-100">Add User</button>
            </form>
        </div>
    </div>

    <!-- Bootstrap JS, Popper.js and jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha3/dist/js/bootstrap.bundle.min.js"></script>

    <script>
        const userForm = document.getElementById('userForm');
        const userNameInput = document.getElementById('userName');
        const userEmailInput = document.getElementById('userEmail');
        const userRoleInput = document.getElementById('userRole');
        const userList = document.getElementById('userList');
        const alertMessage = document.getElementById('alertMessage');

        let users = [];

        userForm.addEventListener('submit', function(e) {
            e.preventDefault();

            // Get user input
            const name = userNameInput.value.trim();
            const email = userEmailInput.value.trim();
            const role = userRoleInput.value.trim();

            if (!name || !email || !role) {
                alert('All fields are required!');
                return;
            }

            // Email validation
            const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
            if (!emailPattern.test(email)) {
                alert('Please enter a valid email!');
                return;
            }

            // Add new user
            const newUser = { id: users.length + 1, name, email, role };
            users.push(newUser);

            // Update the user list UI
            updateUserList();

            // Show success message
            alertMessage.style.display = 'block';
            setTimeout(() => {
                alertMessage.style.display = 'none';
            }, 3000);

            // Reset form
            userForm.reset();
        });

        function updateUserList() {
            // Clear existing user list
            userList.innerHTML = '';

            // Populate the table with users
            users.forEach((user) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${user.id}</td>
                    <td>${user.name}</td>
                    <td>${user.email}</td>
                    <td>${user.role}</td>
                    <td class="btn-actions">
                        <button class="btn btn-warning btn-sm" onclick="editUser(${user.id})">Edit</button>
                        <button class="btn btn-danger btn-sm" onclick="deleteUser(${user.id})">Delete</button>
                    </td>
                `;
                userList.appendChild(row);
            });
        }

        function editUser(id) {
            const user = users.find(user => user.id === id);
            if (user) {
                userNameInput.value = user.name;
                userEmailInput.value = user.email;
                userRoleInput.value = user.role;

                // Remove user from array before updating
                users = users.filter(user => user.id !== id);
                updateUserList();
            }
        }

        function deleteUser(id) {
            users = users.filter(user => user.id !== id);
            updateUserList();
        }
    </script>
</body>
</html>
