<!DOCTYPE html>
<html>
<head>
    <title>Save Student Details</title>
    <script>
        function saveDetails() {
            
            const name = document.getElementById("name").value;
            const age = document.getElementById("age").value;
            const studentClass = document.getElementById("class").value;
            const email = document.getElementById("email").value;
            const phone = document.getElementById("phone").value;

            
            if (!name || !age || !studentClass || !email || !phone) {
                alert("Please fill all the fields.");
                return;
            }

            
            const student = {
                name,
                age,
                studentClass,
                email,
                phone
            };
            localStorage.setItem("studentDetails", JSON.stringify(student));

            
            alert("Student details saved successfully!");
        }

        function loadDetails() {
            
            const savedDetails = localStorage.getItem("studentDetails");
            if (savedDetails) {
                const student = JSON.parse(savedDetails);
                alert(`Saved Student Details:\nName: ${student.name}\nAge: ${student.age}\nClass: ${student.studentClass}\nEmail: ${student.email}\nPhone: ${student.phone}`);
            } else {
                alert("No student details found.");
            }
        }
    </script>
</head>
<body>
    <h1>Student Details Form</h1>
    <form onsubmit="event.preventDefault(); saveDetails();">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="age">Age:</label>
        <input type="number" id="age" name="age" min="0" required><br><br>

        <label for="class">Class:</label>
        <input type="text" id="class" name="class" required><br><br>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>

        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" name="phone" pattern="[0-9]{10}" title="Enter a 10-digit phone number" required><br><br>

        <button type="submit">Save Details</button>
        <button type="button" onclick="loadDetails()">Load Saved Details</button>
    </form>
</body>
</html>
