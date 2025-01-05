<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movie Sphere</title>
    <link href="https://fonts.googleapis.com/css2?family=Lobster&display=swap" rel="stylesheet">
    <style>
        /* General Styles */
        body {
            font-family: 'Lobster', cursive;
            margin: 0;
            padding: 0;
            height: 100vh;
            background: linear-gradient(45deg, #c46e71, #cdbbbb, #9a073a);
            background-size: 400% 400%;
            animation: gradientBG 8s ease infinite;
            display: flex;
            flex-direction: column;
            align-items: center;
            transition: background-color 0.3s, color 0.3s;
        }
        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        body.dark-mode {
            background: #121212;
            color: #e0e0e0;
            animation: none;
        }
        header, footer {
            width: 100%;
            color: white;
            padding: 1rem 2rem;
            text-align: center;
            font-size: 2rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: background-color 0.3s;
        }
        header { background-color: #ff6f61; }
        footer {
            margin-top: auto;
            font-size: 1rem;
        }
        body.dark-mode header, body.dark-mode footer {
            background-color: #1e1e1e;
        }
        .movie-container, .feature-card {
            margin: 2rem auto;
            text-align: center;
            background: white;
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: background-color 0.3s, color 0.3s;
        }
        .movie-container { width: 80%; max-width: 600px; }
        .features-section {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1rem;
            width: 90%;
            max-width: 1200px;
        }
        body.dark-mode .movie-container, body.dark-mode .feature-card {
            background: #1e1e1e;
            color: #e0e0e0;
        }
        .movie-container input, .movie-container button, .utility-button {
            padding: 0.7rem;
            font-size: 1rem;
            border-radius: 10px;
            outline: none;
            transition: background-color 0.3s, color 0.3s, border 0.3s;
        }
        .movie-container input {
            margin-right: 1rem;
            border: 2px solid #ff6f61;
        }
        body.dark-mode .movie-container input {
            background-color: #333;
            color: #e0e0e0;
            border: 2px solid #555;
        }
        .movie-container button, .utility-button {
            color: white;
            border: none;
            cursor: pointer;
        }
        .movie-container button { background-color: #ff6f61; }
        .utility-button {
            position: fixed;
            z-index: 1000;
            top: 20px;
            right: 20px;
            background-color: #ff6f61;
        }
        .utility-button:hover, body.dark-mode .movie-container button { background-color: #967cff; }
        #dark-mode-toggle { top: 80px; }
        .iframe-container {
            margin-top: 1.5rem;
            position: relative;
            width: 100%;
            padding-top: 56.25%; /* 16:9 Aspect Ratio */
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .iframe-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
    </style>
</head>
<body>
    <button id="stop-animation-btn" class="utility-button">Stop Animation</button>
    <button id="start-animation-btn" class="utility-button" style="display: none;">Start Animation</button>
    <button id="dark-mode-toggle" class="utility-button">Enable Dark Mode</button>

    <header>Movie Sphere</header>

    <div class="movie-container">
        <label for="movie_name">Enter Movie Code:</label>
        <input id="movie_name" type="text" placeholder="e.g., tt1234567">
        <button id="update_btn">Load Movie</button>
        <div class="iframe-container">
            <iframe id="movie_iframe" src="https://vidsrc.xyz/embed/movie?imdb=tt13186482" allowfullscreen></iframe>
        </div>
    </div>

    <section class="features-section">
        <div class="feature-card"><h2>Auto Update</h2><p>Movies are automatically updated with the latest content.</p></div>
        <div class="feature-card"><h2>Responsive</h2><p>Optimized for all devices, including mobile and desktop.</p></div>
        <div class="feature-card"><h2>High Quality</h2><p>Stream movies in HD and 4K quality seamlessly.</p></div>
        <div class="feature-card"><h2>Availability</h2><p>Access movies anytime, anywhere with a stable connection.</p></div>
    </section>

    <footer>&copy; 2025 Movie Sphere</footer>

    <script>
        const movieInput = document.getElementById('movie_name');
        const updateButton = document.getElementById('update_btn');
        const iframe = document.getElementById('movie_iframe');
        const stopButton = document.getElementById('stop-animation-btn');
        const startButton = document.getElementById('start-animation-btn');
        const darkModeToggle = document.getElementById('dark-mode-toggle');

        updateButton.addEventListener('click', () => {
            const movieCode = movieInput.value.trim();
            if (movieCode) {
                iframe.src = `https://vidsrc.xyz/embed/movie?imdb=${movieCode}`;
            } else {
                alert('Please enter a valid movie code.');
            }
        });

        darkModeToggle.addEventListener('click', () => {
            document.body.classList.toggle('dark-mode');
            darkModeToggle.textContent = 
                document.body.classList.contains('dark-mode') ? 'Disable Dark Mode' : 'Enable Dark Mode';
        });

        stopButton.addEventListener('click', () => {
            document.body.style.animation = 'none';
            stopButton.style.display = 'none';
            startButton.style.display = 'inline-block';
        });

        startButton.addEventListener('click', () => {
            document.body.style.animation = '';
            startButton.style.display = 'none';
            stopButton.style.display = 'inline-block';
        });
    </script>
</body>
</html># Movie-Sphere
