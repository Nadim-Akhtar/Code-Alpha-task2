# Code-Alpha-task2
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f2f2f2;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: white;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        #taskList {
            margin-bottom: 20px;
        }

        #addTaskForm {
            border-top: 1px solid #ccc;
            padding-top: 20px;
        }

        label {
            display: block;
            margin-bottom: 5px;
        }

        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            box-sizing: border-box;
        }

        button {
            background-color: rgb(238, 175, 15);
            color: white;
            padding: 15px;
            border: none;
            cursor: pointer;
            border-radius: 10px;
        }

        button:hover {
            background-color: #2885dc;
        }
    </style>
    <title>Task Scheduler</title>
</head>
<body>
    <div class="container">
        <h1>TASK SCHEDULER</h1>
        <div id="taskList">
            <!-- Display tasks here -->
        </div>
        <div id="addTaskForm">
            <h2>Add Task</h2>
            <form id="taskForm">
                <label for="taskName">Task Name:</label>
                <input type="text" id="taskName" required>

                <label for="taskDate">Task Date:</label>
                <input type="datetime-local" id="taskDate" required>

                <button type="button" onclick="addTask()">Add Task</button>
            </form>
        </div>
    </div>

    <script>
        const tasks = [];

        function addTask() {
            const taskName = document.getElementById('taskName').value;
            const taskDate = document.getElementById('taskDate').value;

            if (taskName && taskDate) {
                const task = {
                    name: taskName,
                    date: taskDate
                };

                tasks.push(task);
                displayTasks();
                scheduleNotification(task);
                sendEmailNotification(task);
                clearForm();
            }
        }

        function displayTasks() {
            const taskList = document.getElementById('taskList');
            taskList.innerHTML = '';

            tasks.forEach(task => {
                const taskItem = document.createElement('div');
                taskItem.classList.add('task-item');
                taskItem.innerHTML = `
                    <p><strong>${task.name}</strong> - ${task.date}</p>
                `;
                taskList.appendChild(taskItem);
            });
        }

        function scheduleNotification(task) {
            // Add logic for scheduling push notifications (requires backend implementation)
            console.log(`Scheduled push notification for task: ${task.name}`);
        }

        function sendEmailNotification(task) {
            // Add logic for sending email notifications (requires backend implementation)
            console.log(`Sent email notification for task: ${task.name}`);
        }

        function clearForm() {
            document.getElementById('taskForm').reset();
        }

        // Initial display of tasks
        displayTasks();
    </script>
</body>
</html>
