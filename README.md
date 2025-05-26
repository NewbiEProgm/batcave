<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BatHub - Gotham's Code Repository</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
            color: #e0e6ed;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: radial-gradient(circle at center, rgba(255, 215, 0, 0.1) 0%, transparent 70%);
        }

        .login-box {
            background: rgba(0, 0, 0, 0.9);
            border: 2px solid #ffd700;
            border-radius: 15px;
            padding: 40px;
            box-shadow: 0 0 30px rgba(255, 215, 0, 0.3);
            text-align: center;
            min-width: 400px;
            backdrop-filter: blur(10px);
        }

        .bat-logo {
            font-size: 4rem;
            color: #ffd700;
            margin-bottom: 20px;
            text-shadow: 0 0 20px rgba(255, 215, 0, 0.5);
        }

        .login-title {
            color: #ffd700;
            font-size: 2rem;
            margin-bottom: 30px;
            font-weight: bold;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.3);
        }

        .input-group {
            margin-bottom: 20px;
            position: relative;
        }

        .input-field {
            width: 100%;
            padding: 15px;
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid #333;
            border-radius: 8px;
            color: #e0e6ed;
            font-size: 16px;
            transition: all 0.3s ease;
        }

        .input-field:focus {
            outline: none;
            border-color: #ffd700;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.3);
        }

        .login-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(45deg, #ffd700, #ffed4e);
            color: #000;
            border: none;
            border-radius: 8px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
        }

        .login-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(255, 215, 0, 0.4);
        }

        .main-container {
            display: none;
            min-height: 100vh;
        }

        .header {
            background: rgba(0, 0, 0, 0.9);
            border-bottom: 2px solid #ffd700;
            padding: 15px 30px;
            display: flex;
            justify-content: between;
            align-items: center;
            backdrop-filter: blur(10px);
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #ffd700;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
            margin-left: auto;
            margin-right: 30px;
        }

        .nav-links a {
            color: #e0e6ed;
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 5px;
            transition: all 0.3s ease;
        }

        .nav-links a:hover {
            background: rgba(255, 215, 0, 0.2);
            color: #ffd700;
        }

        .logout-btn {
            background: #dc3545;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .logout-btn:hover {
            background: #c82333;
        }

        .content {
            display: flex;
            height: calc(100vh - 80px);
        }

        .sidebar {
            width: 300px;
            background: rgba(0, 0, 0, 0.8);
            border-right: 2px solid #ffd700;
            padding: 20px;
        }

        .repo-list {
            list-style: none;
        }

        .repo-item {
            background: rgba(255, 215, 0, 0.1);
            margin-bottom: 10px;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #ffd700;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .repo-item:hover {
            background: rgba(255, 215, 0, 0.2);
            transform: translateX(5px);
        }

        .main-content {
            flex: 1;
            padding: 30px;
            display: flex;
            flex-direction: column;
        }

        .welcome-section {
            background: rgba(0, 0, 0, 0.6);
            padding: 30px;
            border-radius: 15px;
            border: 2px solid #ffd700;
            margin-bottom: 30px;
            text-align: center;
        }

        .chatbot-container {
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #ffd700;
            border-radius: 15px;
            padding: 20px;
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .chatbot-header {
            color: #ffd700;
            font-size: 1.5rem;
            margin-bottom: 20px;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .chat-area {
            flex: 1;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            overflow-y: auto;
            max-height: 400px;
        }

        .message {
            margin-bottom: 15px;
            padding: 10px;
            border-radius: 8px;
            max-width: 80%;
        }

        .user-message {
            background: rgba(255, 215, 0, 0.2);
            margin-left: auto;
            text-align: right;
        }

        .bot-message {
            background: rgba(0, 100, 200, 0.2);
            border-left: 4px solid #ffd700;
        }

        .chat-input-container {
            display: flex;
            gap: 10px;
        }

        .chat-input {
            flex: 1;
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid #333;
            border-radius: 8px;
            padding: 12px;
            color: #e0e6ed;
            font-size: 16px;
        }

        .chat-input:focus {
            outline: none;
            border-color: #ffd700;
        }

        .send-btn {
            background: #ffd700;
            color: #000;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .send-btn:hover {
            background: #ffed4e;
            transform: translateY(-1px);
        }

        .error-message {
            color: #ff6b6b;
            text-align: center;
            margin-top: 10px;
            font-size: 14px;
        }

        .quick-commands {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            flex-wrap: wrap;
        }

        .quick-cmd {
            background: rgba(255, 215, 0, 0.2);
            border: 1px solid #ffd700;
            color: #ffd700;
            padding: 5px 10px;
            border-radius: 15px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.3s ease;
        }

        .quick-cmd:hover {
            background: rgba(255, 215, 0, 0.3);
            transform: scale(1.05);
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .typing {
            animation: pulse 1.5s infinite;
        }
    </style>
</head>
<body>
    <!-- Login Screen -->
    <div id="loginContainer" class="login-container">
        <div class="login-box">
            <div class="bat-logo">🦇</div>
            <h1 class="login-title">BatHub Access</h1>
            <form id="loginForm">
                <div class="input-group">
                    <input type="text" id="username" class="input-field" placeholder="Username" required>
                </div>
                <div class="input-group">
                    <input type="password" id="password" class="input-field" placeholder="Password" required>
                </div>
                <button type="submit" class="login-btn">Access Granted</button>
                <div id="loginError" class="error-message"></div>
            </form>
            <p style="margin-top: 20px; font-size: 12px; color: #666;">
                Demo credentials: batman / gotham123
            </p>
        </div>
    </div>

    <!-- Main Application -->
    <div id="mainContainer" class="main-container">
        <header class="header">
            <div class="logo">
                <span>🦇</span>
                <span>BatHub</span>
            </div>
            <ul class="nav-links">
                <li><a href="#" onclick="showRepositories()">Repositories</a></li>
                <li><a href="#" onclick="showProjects()">Projects</a></li>
                <li><a href="#" onclick="showIssues()">Issues</a></li>
                <li><a href="#" onclick="showPullRequests()">Pull Requests</a></li>
            </ul>
            <button class="logout-btn" onclick="logout()">Logout</button>
        </header>

        <div class="content">
            <aside class="sidebar">
                <h3 style="color: #ffd700; margin-bottom: 20px;">🗂️ Repositories</h3>
                <ul class="repo-list">
                    <li class="repo-item">
                        <strong>bat-signal-detector</strong>
                        <br><small>Advanced signal processing system</small>
                    </li>
                    <li class="repo-item">
                        <strong>batcave-security</strong>
                        <br><small>Multi-layer security protocols</small>
                    </li>
                    <li class="repo-item">
                        <strong>gotham-crime-analytics</strong>
                        <br><small>Crime pattern analysis tools</small>
                    </li>
                    <li class="repo-item">
                        <strong>batmobile-diagnostics</strong>
                        <br><small>Vehicle monitoring system</small>
                    </li>
                </ul>
            </aside>

            <main class="main-content">
                <section class="welcome-section">
                    <h1>Welcome to the Batcave, Dark Knight! 🦇</h1>
                    <p>Your secure development environment is ready. All systems are operational and Gotham is under watch.</p>
                </section>

                <section class="chatbot-container">
                    <div class="chatbot-header">
                        <span>🤖</span>
                        <span>ALFRED - AI Assistant</span>
                        <span>🦇</span>
                    </div>

                    <div class="quick-commands">
                        <span class="quick-cmd" onclick="sendQuickCommand('temperature')">🌡️ Temperature</span>
                        <span class="quick-cmd" onclick="sendQuickCommand('traffic')">🚦 Traffic</span>
                        <span class="quick-cmd" onclick="sendQuickCommand('time')">⏰ Time</span>
                        <span class="quick-cmd" onclick="sendQuickCommand('crime rate')">🚨 Crime Rate</span>
                        <span class="quick-cmd" onclick="sendQuickCommand('weather')">🌤️ Weather</span>
                        <span class="quick-cmd" onclick="sendQuickCommand('news')">📰 News</span>
                    </div>

                    <div id="chatArea" class="chat-area">
                        <div class="message bot-message">
                            <strong>ALFRED:</strong> Good evening, Master Wayne. I'm here to assist you with information about Gotham City. You can ask me about temperature, traffic, time, crime rates, weather, and more. How may I serve you tonight?
                        </div>
                    </div>

                    <div class="chat-input-container">
                        <input type="text" id="chatInput" class="chat-input" placeholder="Ask ALFRED anything..." onkeypress="handleEnter(event)">
                        <button class="send-btn" onclick="sendMessage()">Send</button>
                    </div>
                </section>
            </main>
        </div>
    </div>

    <script>
        // Credentials (in a real app, this would be handled securely on the server)
        const validCredentials = {
            username: 'batman',
            password: 'gotham123'
        };

        // AI Responses Database
        const aiResponses = {
            'temperature': [
                "Current temperature in Gotham City is 18°C (64°F). Perfect weather for patrol tonight, Master Wayne.",
                "The temperature is 22°C (72°F). Quite pleasant for a night in Gotham.",
                "It's currently 15°C (59°F). You might want to bring the thermal cape tonight."
            ],
            'traffic': [
                "Traffic is light on the main arteries. The Batmobile can move freely through downtown Gotham.",
                "Heavy congestion reported on Gotham Bridge. I suggest taking the underground tunnel route.",
                "Traffic conditions are optimal. All major routes are clear for rapid deployment."
            ],
            'time': [
                `Current time in Gotham City: ${new Date().toLocaleTimeString()}. The night is still young, Master Wayne.`,
                `It is currently ${new Date().toLocaleTimeString()}. Perfect timing for your evening patrol.`,
                `The time is ${new Date().toLocaleTimeString()}. Gotham's criminals won't expect you this early.`
            ],
            'crime rate': [
                "Crime rates are down 23% this month thanks to your vigilant efforts, Master Wayne.",
                "Petty crime has increased in the East End. Might require additional attention tonight.",
                "Overall crime statistics show improvement, but organized crime activity has been detected in the warehouse district."
            ],
            'weather': [
                "Clear skies with minimal cloud cover. Excellent visibility for surveillance work.",
                "Light rain expected around midnight. The streets will be slick - drive carefully.",
                "Foggy conditions developing. Perfect cover for stealth operations, but limited visibility."
            ],
            'news': [
                "Wayne Enterprises stock is up 5%. The board is pleased with the quarterly results.",
                "Commissioner Gordon held a press conference today praising the recent drop in crime rates.",
                "The Gotham Gazette reports increased citizen confidence in city safety measures."
            ],
            'help': [
                "I can provide information about temperature, traffic, time, crime rates, weather, and news. What would you like to know?",
                "Available commands: temperature, traffic, time, crime rate, weather, news. How may I assist you tonight?",
                "I'm here to help with city information and data analysis. What information do you require, Master Wayne?"
            ]
        };

        // Default responses for unknown queries
        const defaultResponses = [
            "I'm not quite sure about that, Master Wayne. Could you try asking about temperature, traffic, time, crime rates, weather, or news?",
            "My databases don't have that information readily available. Perhaps you could rephrase your query?",
            "I'm still learning, Master Wayne. Try asking me about Gotham's current conditions or statistics.",
            "That's beyond my current capabilities. I can help with city data, weather, and traffic information."
        ];

        // Login functionality
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const errorElement = document.getElementById('loginError');
            
            if (username === validCredentials.username && password === validCredentials.password) {
                document.getElementById('loginContainer').style.display = 'none';
                document.getElementById('mainContainer').style.display = 'block';
                errorElement.textContent = '';
            } else {
                errorElement.textContent = 'Access Denied. Invalid credentials.';
            }
        });

        // Logout functionality
        function logout() {
            document.getElementById('mainContainer').style.display = 'none';
            document.getElementById('loginContainer').style.display = 'flex';
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
            document.getElementById('loginError').textContent = '';
        }

        // Chat functionality
        function sendMessage() {
            const input = document.getElementById('chatInput');
            const message = input.value.trim();
            
            if (message) {
                addMessage(message, 'user');
                input.value = '';
                
                // Simulate typing delay
                setTimeout(() => {
                    const response = generateResponse(message);
                    addMessage(response, 'bot');
                }, 1000);
            }
        }

        function sendQuickCommand(command) {
            addMessage(command, 'user');
            setTimeout(() => {
                const response = generateResponse(command);
                addMessage(response, 'bot');
            }, 1000);
        }

        function addMessage(message, sender) {
            const chatArea = document.getElementById('chatArea');
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('message');
            
            if (sender === 'user') {
                messageDiv.classList.add('user-message');
                messageDiv.innerHTML = `<strong>You:</strong> ${message}`;
            } else {
                messageDiv.classList.add('bot-message');
                messageDiv.innerHTML = `<strong>ALFRED:</strong> ${message}`;
            }
            
            chatArea.appendChild(messageDiv);
            chatArea.scrollTop = chatArea.scrollHeight;
        }

        function generateResponse(query) {
            const normalizedQuery = query.toLowerCase();
            
            // Check for keyword matches
            for (const [keyword, responses] of Object.entries(aiResponses)) {
                if (normalizedQuery.includes(keyword)) {
                    return responses[Math.floor(Math.random() * responses.length)];
                }
            }
            
            // Return default response if no match found
            return defaultResponses[Math.floor(Math.random() * defaultResponses.length)];
        }

        function handleEnter(event) {
            if (event.key === 'Enter') {
                sendMessage();
            }
        }

        // Navigation functions (placeholder)
        function showRepositories() {
            alert('Repositories section - Feature coming soon!');
        }

        function showProjects() {
            alert('Projects section - Feature coming soon!');
        }

        function showIssues() {
            alert('Issues section - Feature coming soon!');
        }

        function showPullRequests() {
            alert('Pull Requests section - Feature coming soon!');
        }

        // Initialize chat with welcome message
        document.addEventListener('DOMContentLoaded', function() {
            // Chat is initialized with the welcome message in HTML
        });
    </script>
</body>
</html>
