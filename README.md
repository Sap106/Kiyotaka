<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KIY - AI Bot Kiyotaka</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #1a1a1a;
            color: #eee;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            height: 100vh;
            justify-content: center;
            align-items: center;
        }
        #chat-container {
            background-color: #2a2a2a;
            width: 90%;
            max-width: 600px;
            height: 80vh;
            display: flex;
            flex-direction: column;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(50, 50, 50, 0.7);
            overflow: hidden;
        }
        #chat-window {
            flex-grow: 1;
            overflow-y: auto;
            padding: 15px;
            scrollbar-width: thin;
            scrollbar-color: #888 #2a2a2a;
        }
        #chat-window::-webkit-scrollbar {
            width: 8px;
        }
        #chat-window::-webkit-scrollbar-thumb {
            background-color: #888;
            border-radius: 4px;
        }
        .message {
            margin-bottom: 15px;
            max-width: 75%;
            padding: 10px 15px;
            border-radius: 20px;
            line-height: 1.4;
            font-size: 1rem;
        }
        .user-msg {
            background-color: #005f73;
            align-self: flex-end;
            border-bottom-right-radius: 0;
        }
        .kiy-msg {
            background-color: #0a9396;
            align-self: flex-start;
            border-bottom-left-radius: 0;
        }
        #input-container {
            padding: 10px 15px;
            background-color: #111;
            display: flex;
            gap: 10px;
        }
        #user-input {
            flex-grow: 1;
            border-radius: 20px;
            border: none;
            padding: 10px 15px;
            font-size: 1rem;
            outline: none;
            background-color: #222;
            color: #eee;
        }
        #send-btn {
            background-color: #005f73;
            border: none;
            color: #eee;
            padding: 10px 20px;
            border-radius: 20px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        #send-btn:hover {
            background-color: #0a9396;
        }
        h1 {
            margin-top: 20px;
            font-weight: normal;
            color: #0a9396;
        }
        footer {
            margin: 15px;
            color: #666;
            font-size: 0.8rem;
        }
    </style>
</head>
<body>

    <h1>KIY - AI Bot Kiyotaka</h1>

    <div id="chat-container">
        <div id="chat-window">
            <!-- Messages appear here -->
        </div>
        <div id="input-container">
            <input id="user-input" type="text" placeholder="Ask Kiyotaka..." autocomplete="off" />
            <button id="send-btn">Send</button>
        </div>
    </div>

    <footer>
        Powered by KIY — Inspired by Ayanokoji Kiyotaka from Classroom of the Elite
    </footer>

    <script>
        const chatWindow = document.getElementById('chat-window');
        const userInput = document.getElementById('user-input');
        const sendBtn = document.getElementById('send-btn');

        function appendMessage(text, sender) {
            const msgDiv = document.createElement('div');
            msgDiv.textContent = text;
            msgDiv.classList.add('message');
            msgDiv.classList.add(sender === 'user' ? 'user-msg' : 'kiy-msg');
            chatWindow.appendChild(msgDiv);
            chatWindow.scrollTop = chatWindow.scrollHeight;
        }

        function kiyResponse(userText) {
            userText = userText.toLowerCase();
            if (userText.includes('master') && userText.includes('manipulation')) {
                return "Mastery of manipulation requires observation, patience, and subtlety.";
            } else if (userText.includes('motivate')) {
                return "Motivation is a superficial concept. I simply move forward, one step at a time.";
            } else if (userText.includes('conflict')) {
                return "Understanding motivations is crucial. Resolve conflict with minimal intervention.";
            } else if (userText.includes('location')) {
                return "I cannot track locations without data access. Logical analysis requires information.";
            } else {
                return "State your question or problem explicitly. I will analyze it with precision.";
            }
        }

        function sendMessage() {
            const message = userInput.value.trim();
            if (!message) return;

            appendMessage(message, 'user');

            // KIY response (replace with real AI backend for production)
            const response = kiyResponse(message);
            setTimeout(() => appendMessage(response, 'kiy'), 500);

            userInput.value = '';
            userInput.focus();
        }

        sendBtn.addEventListener('click', sendMessage);

        userInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                e.preventDefault();
                sendMessage();
            }
        });
    </script>
</body>
</html>

