# Random-jokes-User
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Jokes & Users</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        .container {
            max-width: 500px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
        }
        button {
            padding: 10px 15px;
            margin: 10px;
            border: none;
            background-color: #007bff;
            color: white;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background-color: #0056b3;
        }
        #joke, #user {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Random Joke</h2>
        <button onclick="fetchJoke()">Get Joke</button>
        <p id="joke">Click the button to get a joke!</p>
    </div>
    
    <div class="container">
        <h2>Random User</h2>
        <button onclick="fetchUser()">Get User</button>
        <div id="user">Click the button to get user details!</div>
    </div>
    
    <script>
        function fetchJoke() {
            var xhr = new XMLHttpRequest();
            xhr.open("GET", "https://v2.jokeapi.dev/joke/Any", true);
            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    var response = JSON.parse(xhr.responseText);
                    document.getElementById("joke").innerHTML = response.type === "single" ? response.joke : response.setup + "<br>" + response.delivery;
                }
            };
            xhr.send();
        }

        function fetchUser() {
            var xhr = new XMLHttpRequest();
            xhr.open("GET", "https://randomuser.me/api/", true);
            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    var response = JSON.parse(xhr.responseText).results[0];
                    document.getElementById("user").innerHTML = `
                        <img src="${response.picture.large}" alt="User Picture" style="border-radius: 50%;"><br>
                        <strong>${response.name.title} ${response.name.first} ${response.name.last}</strong><br>
                        ${response.email}<br>
                        ${response.location.city}, ${response.location.country}
                    `;
                }
            };
            xhr.send();
        }
    </script>
</body>
</html>
![Randm Jokes Interface](https://github.com/user-attachments/assets/332aa72b-6438-4726-94b5-df6f40e619f6)
![Genrated Jokes   Users](https://github.com/user-attachments/assets/cd87b72d-9a18-4b79-8c00-52b33dc589bb)


