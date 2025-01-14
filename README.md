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
        input[type="text"], input[type="email"] {
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            margin: 5px;
        }
    </style>
</head>
<body>
    <div class="invitation" id="invitation">
        <h1>You're Invited!</h1>
        <p id="message"></p>
    </div>

    <div class="response">
        <h2>What's your name?</h2>
        <input type="text" id="nameInput" placeholder="Enter your name" />
        <button onclick="setName()">Submit</button>
    </div>

    <form id="responseForm" action="https://formspree.io/f/xvgoplev" method="POST" style="display:none;">
        <input type="hidden" name="name" id="formName" />
        <input type="hidden" name="response" id="formResponse" />
    </form>

    <div class="response">
        <h2>Will you go out with me?</h2>
        <button onclick="respond('yes')">Yes</button>
        <button onclick="respond('no')">No</button>
    </div>

    <div id="reply" class="response"></div>

    <script>
        let userName = 'there'; // Default name

        // Function to set the user's name
        function setName() {
            const nameInput = document.getElementById('nameInput').value;
            userName = nameInput || 'there'; // Use default if input is empty
            document.getElementById('message').innerText = createDateInvitation(userName);
        }

        // Function to create the date invitation message
        function createDateInvitation(name) {
            return `Hey ${name}! 😊 I was wondering if you'd like to go out with me sometime. Maybe grab a coffee or dinner? Let me know what you think! ❤️`;
        }

        // Function to handle the response
        function respond(answer) {
            let replyMessage;
            if (answer === 'yes') {
                replyMessage = `Yay! 🎉 I'm so excited, ${userName}! Let's plan the details!`;
            } else {
                replyMessage = `No worries, ${userName}! 😊 Maybe another time.`;
            }
            document.getElementById('reply').innerText = replyMessage;

            // Send response to Formspree
            document.getElementById('formName').value = userName;
            document.getElementById('formResponse').value = answer;
            document.getElementById('responseForm').submit();
        }
    </script>
</body>
</html>




