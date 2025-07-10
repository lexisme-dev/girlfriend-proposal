# girlfriend-proposal
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Girlfriend?</title>
    <style>
        :root {
            --primary-pink: #ff9bb3;
            --dark-pink: #ff7597;
            --light-pink: #ffc0cb;
            --white: #ffffff;
            --shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #fff5f7;
            color: #333;
            overflow-x: hidden;
            transition: all 0.3s ease;
        }

        .heart {
            position: absolute;
            pointer-events: none;
            animation: float 4s ease-in-out infinite;
            opacity: 0.8;
            z-index: 1000;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 0.8; }
            50% { transform: translateY(-20px) rotate(20deg); opacity: 1; }
            100% { transform: translateY(0) rotate(0deg); opacity: 0.8; }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .page {
            width: 100%;
            display: none;
            animation: fadeIn 0.5s ease forwards;
        }

        .active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 2rem;
            color: #d23c67;
            text-align: center;
            font-weight: 700;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px;
            box-shadow: var(--shadow);
        }

        .btn-primary {
            background-color: var(--primary-pink);
            color: white;
            position: relative;
            overflow: hidden;
        }

        .btn-primary:hover {
            background-color: var(--dark-pink);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 121, 151, 0.3);
        }

        .btn-outline {
            background-color: transparent;
            border: 2px solid var(--primary-pink);
            color: var(--dark-pink);
            transition: all 0.3s ease;
            position: relative;
        }

        .btn-outline:hover {
            background-color: var(--primary-pink);
            color: white;
        }

        .form-container {
            background-color: white;
            border-radius: 20px;
            padding: 2rem;
            box-shadow: var(--shadow);
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #d23c67;
        }

        input, select {
            width: 100%;
            padding: 12px;
            border: 2px solid #ffe0e6;
            border-radius: 10px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--primary-pink);
            box-shadow: 0 0 0 3px rgba(255, 155, 179, 0.3);
        }

        .radio-group {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 1rem;
        }

        .radio-option {
            flex: 1 1 calc(33.333% - 15px);
            min-width: 150px;
            position: relative;
        }

        .radio-option input {
            position: absolute;
            opacity: 0;
            width: 0;
            height: 0;
        }

        .radio-option label {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 15px;
            background-color: #fff9fa;
            border: 2px solid #ffe0e6;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }

        .radio-option input:checked + label {
            border-color: var(--primary-pink);
            background-color: #fff0f3;
            box-shadow: 0 0 10px rgba(255, 155, 179, 0.2);
        }

        .radio-option img {
            width: 80px;
            height: 80px;
            object-fit: cover;
            border-radius: 10px;
            margin-bottom: 10px;
            transition: all 0.3s ease;
        }

        .radio-option input:checked + label img {
            transform: scale(1.05);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .date-card {
            background-color: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
        }

        .date-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }

        .date-card img {
            width: 100%;
            height: 180px;
            object-fit: cover;
            border-radius: 10px;
            margin-bottom: 15px;
        }

        .date-card h3 {
            color: #d23c67;
            margin-bottom: 10px;
        }

        .date-card p {
            margin-bottom: 5px;
            color: #666;
        }

        .date-card .date {
            font-weight: 600;
            color: var(--dark-pink);
        }

        .result-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            width: 100%;
            margin-top: 2rem;
        }

        .navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 2rem;
            width: 100%;
        }

        .no-button {
            position: absolute;
            transition: all 0.1s ease;
        }

        .romantic-text {
            font-size: 1.2rem;
            line-height: 1.6;
            color: #666;
            text-align: center;
            margin-bottom: 2rem;
            max-width: 700px;
        }

        .heart-icon {
            color: var(--primary-pink);
            font-size: 1.5rem;
            vertical-align: middle;
            margin: 0 5px;
        }

        .btn-container {
            position: relative;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Page 1: Initial Question -->
        <div class="page active" id="page1">
            <h1>Will You Be My Girlfriend?</h1>
            <div class="romantic-text">
                Every moment with you feels like a beautiful dream <span class="heart-icon">❤️</span> 
                Your smile brightens my darkest days <span class="heart-icon">❤️</span> 
                Would you do me the incredible honor of being my girlfriend?
            </div>
            <div class="btn-container">
                <button class="btn btn-primary" id="yesBtn">Yes I Do!</button>
                <button class="btn btn-outline no-button" id="noBtn">No, leave me alone</button>
            </div>
        </div>

        <!-- Page 2: Date Scheduling -->
        <div class="page" id="page2">
            <h1>Let's Plan Our First Date!</h1>
            <div class="form-container">
                <div class="form-group">
                    <label for="date">Choose a Date</label>
                    <input type="date" id="date" name="date">
                </div>
                <div class="form-group">
                    <label for="time">Select Time</label>
                    <input type="time" id="time" name="time">
                </div>
                <div class="form-group">
                    <label>What Would You Like to Do?</label>
                    <div class="radio-group">
                        <div class="radio-option">
                            <input type="radio" id="pizza" name="activity" value="pizza">
                            <label for="pizza">
                                <img src="https://placehold.co/400x300?text=Pizza+Date&font=playfair-display" alt="Delicious wood-fired pizza with various toppings on a wooden board">
                                Pizza Night
                            </label>
                        </div>
                        <div class="radio-option">
                            <input type="radio" id="sushi" name="activity" value="sushi">
                            <label for="sushi">
                                <img src="https://placehold.co/400x300?text=Sushi+Date&font=playfair-display" alt="Beautifully arranged sushi platter with fresh fish and colorful garnishes">
                                Sushi Dinner
                            </label>
                        </div>
                        <div class="radio-option">
                            <input type="radio" id="movie" name="activity" value="movie">
                            <label for="movie">
                                <img src="https://placehold.co/400x300?text=Movie+Night&font=playfair-display" alt="Movie theater with red velvet seats and a large screen">
                                Movie Night
                            </label>
                        </div>
                    </div>
                </div>
            </div>
            <div class="navigation">
                <button class="btn btn-primary" id="continueBtn">Continue</button>
            </div>
        </div>

        <!-- Page 3: Date Confirmation -->
        <div class="page" id="page3">
            <h1>Our Date Plans</h1>
            <div class="romantic-text">
                I can't wait for our special day together! Here's what we've planned:
            </div>
            <div class="result-container" id="dateCards">
                <!-- Date cards will be inserted here by JavaScript -->
            </div>
            <div class="navigation">
                <button class="btn btn-primary" id="restartBtn">Start Over</button>
            </div>
        </div>
    </div>

    <script>
        // Heart trail animation
        document.addEventListener('DOMContentLoaded', function() {
            const body = document.querySelector('body');
            const colors = ['#ff9bb3', '#ff7597', '#ffc0cb', '#ffdfe5'];
            let heartsCount = 0;

            body.addEventListener('mousemove', function(e) {
                if (heartsCount < 15) { // Limit number of hearts on screen
                    const heart = document.createElement('div');
                    heart.className = 'heart';
                    
                    const size = Math.random() * 20 + 10;
                    heart.style.width = `${size}px`;
                    heart.style.height = `${size}px`;
                    heart.style.left = `${e.pageX - size/2}px`;
                    heart.style.top = `${e.pageY - size/2}px`;
                    heart.style.color = colors[Math.floor(Math.random() * colors.length)];
                    
                    heart.innerHTML = '❤️';
                    body.appendChild(heart);
                    heartsCount++;
                    
                    setTimeout(() => {
                        heart.remove();
                        heartsCount--;
                    }, 4000);
                }
            });

            // No button behavior
            const noBtn = document.getElementById('noBtn');
            const btnContainer = document.querySelector('.btn-container');
            
            noBtn.addEventListener('mouseover', function() {
                const containerRect = btnContainer.getBoundingClientRect();
                const btnRect = noBtn.getBoundingClientRect();
                const maxX = containerRect.width - btnRect.width;
                const maxY = containerRect.height - btnRect.height;
                
                const randomX = Math.floor(Math.random() * maxX);
                const randomY = Math.floor(Math.random() * maxY);
                
                noBtn.style.left = `${randomX}px`;
                noBtn.style.top = `${randomY}px`;
            });

            // Page navigation
            const pages = document.querySelectorAll('.page');
            const yesBtn = document.getElementById('yesBtn');
            const continueBtn = document.getElementById('continueBtn');
            const restartBtn = document.getElementById('restartBtn');
            
            function changePage(pageNumber) {
                pages.forEach(page => page.classList.remove('active'));
                document.getElementById(`page${pageNumber}`).classList.add('active');
                
                if (pageNumber === 1) {
                    createConfetti();
                }
                
                window.scrollTo(0, 0);
            }
            
            yesBtn.addEventListener('click', function() {
                changePage(2);
                createConfetti();
            });
            
            continueBtn.addEventListener('click', function() {
                const date = document.getElementById('date').value;
                const time = document.getElementById('time').value;
                const activity = document.querySelector('input[name="activity"]:checked').value;
                
                if (!date || !time || !activity) {
                    alert('Please fill all the fields!');
                    return;
                }
                
                // Format date to be more readable
                const dateObj = new Date(date);
                const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
                const formattedDate = dateObj.toLocaleDateString('en-US', options);
                
                // Create date card HTML
                let activityText, activityImg;
                switch(activity) {
                    case 'pizza':
                        activityText = 'Pizza Night';
                        activityImg = 'https://placehold.co/600x400?text=Pizza+Date&font=playfair-display';
                        break;
                    case 'sushi':
                        activityText = 'Sushi Dinner';
                        activityImg = 'https://placehold.co/600x400?text=Sushi+Date&font=playfair-display';
                        break;
                    case 'movie':
                        activityText = 'Movie Night';
                        activityImg = 'https://placehold.co/600x400?text=Movie+Night&font=playfair-display';
                        break;
                }
                
                const dateCardHTML = `
                    <div class="date-card">
                        <img src="${activityImg}" alt="${activityText} - Romantic date night">
                        <h3>${activityText}</h3>
                        <p class="date">${formattedDate}</p>
                        <p>Time: ${time}</p>
                        <p>Can't wait to spend this special time with you!</p>
                    </div>
                `;
                
                document.getElementById('dateCards').innerHTML = dateCardHTML;
                changePage(3);
            });
            
            restartBtn.addEventListener('click', function() {
                changePage(1);
            });
            
            function createConfetti() {
                for (let i = 0; i < 50; i++) {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti';
                    
                    const size = Math.random() * 10 + 5;
                    confetti.style.width = `${size}px`;
                    confetti.style.height = `${size}px`;
                    confetti.style.left = `${Math.random() * window.innerWidth}px`;
                    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    
                    confetti.style.animationDuration = `${Math.random() * 2 + 2}s`;
                    
                    document.body.appendChild(confetti);
                    
                    setTimeout(() => {
                        confetti.remove();
                    }, 3000);
                }
            }
        });
    </script>
</body>
</html>
