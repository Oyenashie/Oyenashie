<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SoloEduMastery Welcome Page</title>

  <!-- Firebase SDK and Initialization -->
  <script type="module">
    // Import the Firebase SDK
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.13.2/firebase-app.js";
    import { getAuth, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/10.13.2/firebase-auth.js";
    import { getAnalytics } from "https://www.gstatic.com/firebasejs/10.13.2/firebase-analytics.js";

    // Firebase configuration for SoloEduMastery
    const firebaseConfig = {
      apiKey: "AIzaSyD9ckqcL5MDAQKfFb6ALzQKRc-bbdJ4GEA",
      authDomain: "soloedumastery.firebaseapp.com",
      projectId: "soloedumastery",
      storageBucket: "soloedumastery.appspot.com",
      messagingSenderId: "863521795050",
      appId: "1:863521795050:web:8b2f5d028ec550d5b1e093",
      measurementId: "G-6MH8H11M1Y"
    };

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);
    const analytics = getAnalytics(app);
    const auth = getAuth(app);

    // Check if user is authenticated
    window.addEventListener('load', () => {
      onAuthStateChanged(auth, (user) => {
        if (user) {
          // User is logged in, display their name or email
          document.getElementById("user-name").textContent = `${user.displayName || user.email}, welcome to SoloEduMastery!`;
        } else {
          // Redirect to sign-in page if not logged in
          window.location.href = "https://sites.google.com/d/1UfYpOhbxDqU5ilhPS2YPYwMfZs-yzFxI/p/1Ssn79xJ8jkRuMEU13BB_2qDKvneEWmah/edit";
        }
      });
    });

    // Sign-out function
    function signOutUser() {
      signOut(auth).then(() => {
        // Sign-out successful, redirect to the sign-in page
        window.location.href = "https://sites.google.com/d/1UfYpOhbxDqU5ilhPS2YPYwMfZs-yzFxI/p/1Ssn79xJ8jkRuMEU13BB_2qDKvneEWmah/edit";
      }).catch((error) => {
        console.error("Error signing out:", error);
      });
    }
  </script>

  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f0f8ff;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #004080;
      color: white;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 28px;
    }

    .content {
      padding: 20px;
      text-align: center;
    }

    .welcome-message {
      margin-top: 20px;
      font-size: 24px;
      font-weight: bold;
      color: #333;
    }

    .edu-options {
      margin-top: 40px;
      display: flex;
      justify-content: space-around;
    }

    .edu-options div {
      background-color: #004080;
      color: white;
      padding: 15px;
      width: 30%;
      border-radius: 10px;
      cursor: pointer;
    }

    .edu-options div:hover {
      background-color: #0066cc;
    }

    button {
      margin-top: 40px;
      padding: 10px 20px;
      background-color: #ff0000;
      color: white;
      border: none;
      cursor: pointer;
      font-size: 16px;
      border-radius: 5px;
    }

    button:hover {
      background-color: #cc0000;
    }
  </style>

</head>
<body>

  <header>
    <h1>Welcome to SoloEduMastery!</h1>
  </header>

  <div class="content">
    <!-- Welcome message for logged-in user -->
    <div class="welcome-message">
      <h2 id="user-name">Loading user info...</h2>
    </div>

    <!-- Navigation options for the platform -->
    <div class="edu-options">
      <div onclick="window.location.href='/courses.html'">Explore Courses</div>
      <div onclick="window.location.href='/resources.html'">Access Resources</div>
      <div onclick="window.location.href='/personalized-coaching.html'">Get Personalized Coaching</div>
    </div>

    <!-- Sign Out Button -->
    <button onclick="signOutUser()">Sign Out</button>
  </div>

</body>
</html>
