<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Light/Dark Mode Toggle</title>
    <style>
        body {
            font-family: sans-serif;
            transition: background-color 0.3s ease, color 0.3s ease; /* Smooth transitions */
        }

        body.light-mode {
            background-color: #f8f8f8;
            color: #333;
        }

        body.dark-mode {
            background-color: #333;
            color: #f8f8f8;
        }

        .toggle-container {
            display: flex;
            justify-content: center; /* Center the toggle */
            margin-top: 20px;
        }

        .toggle-switch {
            position: relative;
            width: 60px;
            height: 34px;
        }

        .toggle-switch input { 
            opacity: 0;
            width: 0;
            height: 0;
        }

        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            -webkit-transition: .4s;
            transition: .4s;
            border-radius: 34px;
        }

        .slider:before {
            position: absolute;
            content: "";
            height: 26px;
            width: 26px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            -webkit-transition: .4s;
            transition: .4s;
            border-radius: 50%;
        }

        input:checked + .slider {
            background-color: #2196F3; /* Example active color */
        }

        input:focus + .slider {
            box-shadow: 0 0 1px #2196F3; /* Example focus style */
        }

        input:checked + .slider:before {
            -webkit-transform: translateX(26px);
            -ms-transform: translateX(26px);
            transform: translateX(26px);
        }

        /* Example content styling - you can customize this */
        .content {
            padding: 20px;
            text-align: center; /* Center the content */
        }
    </style>
</head>
<body>

    <div class="toggle-container">
        <label class="toggle-switch">
            <input type="checkbox" id="themeToggle">
            <span class="slider"></span>
        </label>
    </div>

    <div class="content">
        <h1>Light/Dark Mode Example</h1>
        <p>This is some example content.  It will change with the theme.</p>
    </div>


    <script>
        const body = document.body;
        const themeToggle = document.getElementById('themeToggle');
        const savedTheme = localStorage.getItem('theme');

        if (savedTheme) {
            body.classList.add(savedTheme);
            themeToggle.checked = savedTheme === 'dark-mode';
        } else {
          // Set initial theme if none is saved (e.g., light mode)
          body.classList.add('light-mode'); // Or 'dark-mode'
        }


        themeToggle.addEventListener('change', () => {
            body.classList.toggle('dark-mode');  // Toggle the class

            if (body.classList.contains('dark-mode')) {
                localStorage.setItem('theme', 'dark-mode');
            } else {
                localStorage.setItem('theme', 'light-mode');
            }
        });
    </script>

</body>
</html>