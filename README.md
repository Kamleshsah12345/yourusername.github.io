# yourusername.github.io
A simple project site with a Calculator and To-Do List built using HTML, CSS, and JavaScript.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Project Site</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #f4f4f9;
      color: #333;
    }
    header {
      background: #4CAF50;
      color: white;
      padding: 20px;
      text-align: center;
    }
    nav {
      background: #333;
      display: flex;
      justify-content: center;
    }
    nav a {
      color: white;
      padding: 14px 20px;
      text-decoration: none;
      text-align: center;
    }
    nav a:hover {
      background: #575757;
    }
    section {
      padding: 20px;
      max-width: 900px;
      margin: auto;
    }
    .project {
      background: white;
      padding: 15px;
      margin: 15px 0;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    footer {
      background: #333;
      color: white;
      text-align: center;
      padding: 10px;
      margin-top: 20px;
    }

    /* Calculator styling */
    .calculator {
      background: #222;
      padding: 20px;
      border-radius: 10px;
      display: inline-block;
    }
    .calculator input {
      width: 100%;
      height: 50px;
      font-size: 18px;
      text-align: right;
      margin-bottom: 10px;
      padding: 10px;
      border: none;
      border-radius: 5px;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 60px);
      gap: 10px;
      justify-content: center;
    }
    .buttons button {
      height: 50px;
      font-size: 18px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background: #4CAF50;
      color: white;
    }
    .buttons button:hover {
      background: #45a049;
    }
    .buttons button.operator {
      background: #f39c12;
    }
    .buttons button.operator:hover {
      background: #e67e22;
    }

    /* To-Do List styling */
    .todo {
      margin-top: 20px;
    }
    .todo input {
      padding: 10px;
      width: 70%;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .todo button {
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      margin-left: 5px;
      background: #4CAF50;
      color: white;
      cursor: pointer;
    }
    .todo button:hover {
      background: #45a049;
    }
    ul {
      list-style-type: none;
      padding: 0;
      margin-top: 10px;
    }
    ul li {
      background: #eee;
      padding: 10px;
      margin: 5px 0;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    ul li.completed {
      text-decoration: line-through;
      color: gray;
    }
    ul li button {
      background: red;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      padding: 5px 10px;
    }
    ul li button:hover {
      background: darkred;
    }
  </style>
</head>
<body>
  <header>
    <h1>Welcome to My Project Site</h1>
    <p>A showcase of my student projects 🚀</p>
  </header>

  <nav>
    <a href="#about">About Me</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </nav>

  <section id="about">
    <h2>About Me</h2>
    <p>Hello! I am a student passionate about coding and learning new things. This site is where I share my small projects and experiments.</p>
  </section>

  <section id="projects">
    <h2>My Projects</h2>

    <!-- Calculator Project -->
    <div class="project">
      <h3>🧮 Calculator</h3>
      <p>A simple calculator built with HTML, CSS, and JavaScript.</p>
      <div class="calculator">
        <input type="text" id="display" disabled>
        <div class="buttons">
          <button onclick="press('7')">7</button>
          <button onclick="press('8')">8</button>
          <button onclick="press('9')">9</button>
          <button class="operator" onclick="press('/')">÷</button>

          <button onclick="press('4')">4</button>
          <button onclick="press('5')">5</button>
          <button onclick="press('6')">6</button>
          <button class="operator" onclick="press('*')">×</button>

          <button onclick="press('1')">1</button>
          <button onclick="press('2')">2</button>
          <button onclick="press('3')">3</button>
          <button class="operator" onclick="press('-')">−</button>

          <button onclick="press('0')">0</button>
          <button onclick="press('.')">.</button>
          <button onclick="calculate()">=</button>
          <button class="operator" onclick="press('+')">+</button>

          <button style="grid-column: span 4; background: #e74c3c;" onclick="clearDisplay()">C</button>
        </div>
      </div>
    </div>

    <!-- To-Do List Project -->
    <div class="project">
      <h3>📝 To-Do List</h3>
      <p>A simple To-Do List app to add and manage tasks.</p>
      <div class="todo">
        <input type="text" id="taskInput" placeholder="Enter a task...">
        <button onclick="addTask()">Add</button>
        <ul id="taskList"></ul>
      </div>
    </div>

  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p>Email: <a href="mailto:youremail@example.com">youremail@example.com</a></p>
    <p>GitHub: <a href="https://github.com/yourusername" target="_blank">yourusername</a></p>
  </section>

  <footer>
    <p>© 2025 My Project Site | Made with ❤️ by Me</p>
  </footer>

  <script>
    // Calculator JS
    let display = document.getElementById("display");
    function press(value) {
      display.value += value;
    }
    function calculate() {
      try {
        display.value = eval(display.value);
      } catch {
        display.value = "Error";
      }
    }
    function clearDisplay() {
      display.value = "";
    }

    // To-Do List JS
    let taskList = document.getElementById("taskList");
    function addTask() {
      let input = document.getElementById("taskInput");
      if (input.value.trim() === "") return;
      
      let li = document.createElement("li");
      li.textContent = input.value;

      // Toggle complete on click
      li.addEventListener("click", () => {
        li.classList.toggle("completed");
      });

      // Delete button
      let deleteBtn = document.createElement("button");
      deleteBtn.textContent = "X";
      deleteBtn.onclick = () => li.remove();
      li.appendChild(deleteBtn);

      taskList.appendChild(li);
      input.value = "";
    }
  </script>
</body>
</html>![1000021278](https://github.com/user-attachments/assets/6c7c9bb5-dbff-40b2-a105-b5056e7ae4ef)
