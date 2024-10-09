<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Date Invitation</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            height: 100vh;
            background-color: #f0f8ff;
            font-family: Arial, sans-serif;
        }
        .invitation {
            padding: 20px;
            border-radius: 10px;
            background-color: #ffffff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            text-align: center;
            margin-bottom: 20px;
        }
        .response {
            margin-top: 20px;
        }
        button {
            margin: 5px;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background-color: #4CAF50; /* Green */
            color: white;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <div class="invitation" id="invitation">
        <h1>You're Invited!</h1>
        <p id="message"></p>
    </div>
    
    <div class="response">
        <h2>Will you go out with me?</h2>
        <button onclick="respond('yes')">Yes</button>
        <button onclick="respond('no')">No</button>
    </div>
    
    <div id="reply" class="response"></div>

    <script>
        // Function to create the date invitation message
        function createDateInvitation(name) {
            return `Hey ${name}! 😊 I was wondering if you'd like to go out with me sometime. Maybe grab a coffee or dinner? Let me know what you think! ❤️`;
        }

        // Get the name from the URL parameters
        const urlParams = new URLSearchParams(window.location.search);
        const name = urlParams.get('name') || 'there'; // Default to 'there' if no name is provided

        // Display the invitation message
        document.getElementById('message').innerText = createDateInvitation(name);

        // Function to handle the response
        function respond(answer) {
            let replyMessage;
            if (answer === 'yes') {
                replyMessage = "Yay! 🎉 I'm so excited! Let's plan the details!";
            } else {
                replyMessage = "No worries! 😊 Maybe another time.";
            }
            document.getElementById('reply').innerText = replyMessage;
        }
    </script>
</body>
</html>

