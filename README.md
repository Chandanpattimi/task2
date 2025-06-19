# task2
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Intermediate HTML, CSS, and JS Task</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background: #f0f4f7;
    }

    h1, h2 {
      text-align: center;
    }

    .container {
      display: grid;
      grid-template-columns: 1fr;
      gap: 30px;
      max-width: 800px;
      margin: auto;
    }

    form, .todo-section {
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    input, textarea {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    button {
      background: #28a745;
      color: white;
      padding: 10px;
      width: 100%;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background: #218838;
    }

    ul {
      list-style-type: none;
      padding: 0;
    }

    li {
      background: #e9ecef;
      margin: 5px 0;
      padding: 10px;
      border-radius: 5px;
      cursor: pointer;
    }

    @media (min-width: 768px) {
      .container {
        grid-template-columns: 1fr 1fr;
      }
    }
  </style>
</head>
<body>

  <h1>Contact Form and To-Do List</h1>
  <div class="container">
    <!-- Contact Form -->
    <form id="contactForm">
      <h2>Contact Us</h2>
      <input type="text" name="name" placeholder="Your Name" required />
      <input type="email" name="email" placeholder="Your Email" required />
      <textarea name="message" rows="4" placeholder="Your Message" required></textarea>
      <button type="submit">Submit</button>
    </form>

    <!-- To-Do List -->
    <div class="todo-section">
      <h2>To-Do List</h2>
      <input type="text" id="todoInput" placeholder="Enter task">
      <button onclick="addTodo()">Add Task</button>
      <ul id="todoList"></ul>
    </div>
  </div>

  <script>
    // Form validation
    document.getElementById("contactForm").addEventListener("submit", function(e) {
      const email = e.target.email.value;
      const name = e.target.name.value;

      if (!email.includes("@")) {
        alert("Please enter a valid email address.");
        e.preventDefault();
      } else if (name.trim() === "") {
        alert("Please enter your name.");
        e.preventDefault();
      }
    });

    // To-Do list functionality
    function addTodo() {
      const input = document.getElementById("todoInput");
      const task = input.value.trim();
      if (task === "") return;

      const li = document.createElement("li");
      li.textContent = task;
      li.onclick = () => li.remove();  // Remove task on click
      document.getElementById("todoList").appendChild(li);
      input.value = "";
    }
  </script>
</body>
</html>
