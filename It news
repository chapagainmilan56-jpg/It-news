<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NEWS IT | Your Daily Source</title>
    <!-- Animate.css for quick, smooth animations -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"/>
    <style>
        :root {
            --primary-blue: #007bff;
            --dark-blue: #0056b3;
            --bg-color: #f8f9fa;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            margin: 0;
            background-color: var(--bg-color);
            color: #333;
            overflow-x: hidden;
        }

        /* Animated Header & Logo */
        header {
            background: #ffffff;
            padding: 15px 0;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            animation: fadeInDown 0.8s;
        }

        .logo-container {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            fill: var(--primary-blue);
            animation: pulse 2s infinite;
        }

        .logo-text {
            font-size: 2rem;
            font-weight: 800;
            letter-spacing: -1px;
            color: #222;
        }

        .logo-text span {
            color: var(--primary-blue);
        }

        /* Navigation Buttons */
        .nav-buttons {
            display: flex;
            justify-content: center;
            margin: 30px 0;
            gap: 15px;
        }

        .btn {
            background-color: var(--primary-blue);
            color: white;
            border: none;
            padding: 14px 28px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            border-radius: 50px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 123, 255, 0.3);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn:hover {
            background-color: var(--dark-blue);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 123, 255, 0.4);
        }

        .btn:active {
            transform: translateY(0);
        }

        /* Main Container */
        .container {
            width: 90%;
            max-width: 700px;
            margin: 0 auto 50px auto;
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
        }

        .hidden { display: none; }

        /* Animation for sections */
        .section-animate {
            animation: fadeInUp 0.6s ease-out;
        }

        /* Form Styling */
        h2 { margin-top: 0; color: #222; }
        input, textarea {
            width: 100%;
            margin: 10px 0 20px 0;
            padding: 12px;
            border: 2px solid #eee;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }
        input:focus, textarea:focus {
            outline: none;
            border-color: var(--primary-blue);
        }

        /* News Cards */
        .news-card {
            background: #fff;
            border-radius: 12px;
            margin-bottom: 25px;
            padding-bottom: 20px;
            border-bottom: 1px solid #eee;
            animation: fadeIn 0.5s ease-in;
        }

        .news-card img {
            width: 100%;
            max-height: 400px;
            object-fit: cover;
            border-radius: 10px;
            margin: 15px 0;
        }

        .news-card h3 { font-size: 1.5rem; margin-bottom: 5px; }
        .news-card small { color: #888; display: block; margin-bottom: 10px; }
        .news-card p { line-height: 1.6; color: #444; }

    </style>
</head>
<body>

    <header>
        <div class="logo-container">
            <!-- SVG Logo -->
            <svg class="logo-icon" viewBox="0 0 24 24">
                <path d="M20 5H4c-1.1 0-2 .9-2 2v10c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm-1 12H5V7h14v10zM11 8H7v2h4V8zm0 3H7v2h4v-2zm0 3H7v2h4v-2zm6-6h-4v8h4V8z"/>
            </svg>
            <div class="logo-text">NEWS <span>IT</span></div>
        </div>
    </header>

    <div class="nav-buttons animate__animated animate__fadeIn">
        <button class="btn" onclick="showSection('see-news')">
            <span>📰</span> See News
        </button>
        <button class="btn" onclick="showSection('upload-news')">
            <span>📤</span> Upload News
        </button>
    </div>

    <!-- Upload News Section -->
    <div id="upload-news" class="container hidden section-animate">
        <h2>Create a Story</h2>
        <input type="text" id="news-title" placeholder="Catchy Headline...">
        <textarea id="news-text" rows="5" placeholder="What's happening?"></textarea>
        
        <p style="margin-bottom: 5px; font-weight: bold;">Add an Image</p>
        <input type="file" id="news-image" accept="image/*">
        
        <button class="btn" onclick="saveNews()" style="width: 100%; justify-content: center; margin-top: 10px;">
            Post News
        </button>
    </div>

    <!-- See News Section -->
    <div id="see-news" class="container section-animate">
        <h2>Latest Updates</h2>
        <div id="news-list">
            <!-- News items will appear here -->
        </div>
    </div>

    <script>
        function showSection(sectionId) {
            const upload = document.getElementById('upload-news');
            const see = document.getElementById('see-news');
            
            // Hide both
            upload.classList.add('hidden');
            see.classList.add('hidden');
            
            // Show and re-trigger animation
            const target = document.getElementById(sectionId);
            target.classList.remove('hidden');
            target.style.animation = 'none';
            target.offsetHeight; /* trigger reflow */
            target.style.animation = null;

            if (sectionId === 'see-news') {
                displayNews();
            }
        }

        function saveNews() {
            const title = document.getElementById('news-title').value;
            const text = document.getElementById('news-text').value;
            const imageInput = document.getElementById('news-image');
            
            if (!title || !text) {
                alert("Please add a title and some text!");
                return;
            }

            const reader = new FileReader();
            
            const postData = (img) => {
                const newsItem = {
                    title: title,
                    text: text,
                    image: img,
                    date: new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' })
                };

                let newsLibrary = JSON.parse(localStorage.getItem('newsData')) || [];
                newsLibrary.unshift(newsItem);
                localStorage.setItem('newsData', JSON.stringify(newsLibrary));

                // Clear and switch
                document.getElementById('news-title').value = '';
                document.getElementById('news-text').value = '';
                document.getElementById('news-image').value = '';
                showSection('see-news');
            };

            if (imageInput.files[0]) {
                reader.onload = (e) => postData(e.target.result);
                reader.readAsDataURL(imageInput.files[0]);
            } else {
                postData(null);
            }
        }

        function displayNews() {
            const newsList = document.getElementById('news-list');
            const newsLibrary = JSON.parse(localStorage.getItem('newsData')) || [];

            if (newsLibrary.length === 0) {
                newsList.innerHTML = '<p style="text-align:center; color:#999; margin-top:20px;">No news stories yet. Be the first to post!</p>';
                return;
            }

            newsList.innerHTML = '';
            newsLibrary.forEach((item, index) => {
                const card = document.createElement('div');
                card.className = 'news-card';
                // Delay each card slightly for a sequence effect
                card.style.animationDelay = (index * 0.1) + 's';
                
                let imgHtml = item.image ? `<img src="${item.image}" alt="News">` : '';
                
                card.innerHTML = `
                    <h3>${item.title}</h3>
                    <small>📅 ${item.date}</small>
                    <p>${item.text}</p>
                    ${imgHtml}
                `;
                newsList.appendChild(card);
            });
        }

        // Load news on first visit
        displayNews();
    </script>
</body>
</html>
