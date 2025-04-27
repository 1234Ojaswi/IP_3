<!DOCTYPE html>
<html>
<head>
  <title>Live Clock</title>
</head>
<body>
  <h1>⏰ Live Clock</h1>
  <div id="clock" style="font-size: 24px; color: blue;"></div>

  <script>
    function updateClock() {
      const now = new Date();
      const time = now.toLocaleTimeString();
      document.getElementById('clock').innerText = time;
    }

    // Call every 1 second
    setInterval(updateClock, 1000);
    updateClock(); // also show immediately on load
  </script>
</body>
</html>

<!DOCTYPE html>
<html>
<head>
  <title>Fetch User Data</title>
</head>
<body>
  <h1>🧑 Random User Info</h1>
  <button onclick="getUser()">Get Random User</button>
  <div id="userInfo" style="margin-top: 20px;"></div>

  <script>
    function getUser() {
      fetch('https://randomuser.me/api/')
        .then(response => response.json())
        .then(data => {
          const user = data.results[0];
          document.getElementById('userInfo').innerHTML = `
            <img src="${user.picture.large}" />
            <p><strong>Name:</strong> ${user.name.first} ${user.name.last}</p>
            <p><strong>Country:</strong> ${user.location.country}</p>
            <p><strong>Email:</strong> ${user.email}</p>
          `;
        })
        .catch(error => {
          document.getElementById('userInfo').innerText = 'Error loading user!';
        });
    }
  </script>
</body>
</html>
