<!DOCTYPE html>
<html lang="en">
<head>
<!-- Information about the page, not shown on it -->
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>My Basic Portfolio</title>

 <style>
    /* 1. GENERAL STYLES */
    body {
        font-family: Arial, sans-serif;
        background-color: #f4f4f9;
        color: #333333;
        margin: 0;
        padding: 0;
    }
    /* 2. HEADER STYLES */
    header {
        background-color: #ac5a6c;
        color: white;
        text-align: center;
        padding: 40px 20px;
    }
    header h1 {
        margin: 0;
        font-size: 36px;
    }

    header p {
        margin-top: 10px;
        font-size: 18px;
        color: #e9c8cf;
    }
    /* 3. MAIN CONTENT STYLES */
    main {
        padding: 40px 20px;
        max-width: 1000px;
        margin: 0 auto;
    }
    /* 4. FLEXBOX CONTAINER FOR CARDS */
    #skills-container {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
        justify-content: center;
    }
    /* 5. INDIVIDUAL CARD STYLES */
    .skill-card {
        position: relative;
        background-color: white;
        border-radius: 8px;
        padding: 20px;
        width: 250px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        text-align: center;
        border-top: 5px solid #db3466;
    }
    .toggle-icon {
        position: absolute;
        top: 14px;
        right: 16px;
        font-size: 1.25rem;
        font-weight: bold;
        color: #9e6a75;
        line-height: 1;
    }
    .skill-card h3 {
        margin-top: 0;
        color: #683843;
    }

    .skill-card p {
        font-size: 14px;
        color: #666666;
        line-height: 1.5;
    }
    .skill-card.selected {
        border: 2px solid #eb2556;
        background-color: #ffe6ec;
        transform: scale(1.03);
    }
 </style>
</head>
<body>
<header>
    <h1>Ellen Cain</h1>
    <p>A beginner web developer learning to code</p>
</header>
<main>
    <h2 style="text-align: center; margin-bottom: 30px;">My Skills</h2>
     <div id="skills-container">
     </div>
</main>

<script>
    const mySkills = [
        {
            name: "HTML",
            description: "The building blocks of the web. I use this to structure my websites."
        },
        {
            name: "CSS",
            description: "The styling language. I use this to add colors, layouts, and make things look pretty."
        },
        {
            name: "JavaScript",
            description: "The brain of the website. I am learning this to make my websites interactive."
        },
        {
            name: "Problem Solving",
            description: "Breaking down complex problems into smaller, manageable steps."
        }
    ];

    const container = document.getElementById("skills-container");

    mySkills.forEach(function(skill) {
        // a) create an empty <div>
        const cardElement = document.createElement("div");

        // b) give it the class our CSS styles
        cardElement.className = "skill-card";

        // c) put HTML inside the card
        cardElement.innerHTML = `
            <span class="toggle-icon">+</span>
            <h3>${skill.name}</h3>
        `;

        // d) the description, hidden at first
        const details = document.createElement('p');
        details.textContent = skill.description;
        details.style.display = 'none';
        cardElement.appendChild(details);

        // f) react to a click
        cardElement.addEventListener('click', function() {
            const icon = cardElement.querySelector('.toggle-icon');
            const isHidden = details.style.display === 'none';
            details.style.display = isHidden ? 'block' : 'none';
            cardElement.classList.toggle('selected');
            if (isHidden) {
               details.style.display = 'block';
               icon.textContent = '-';
            } else {
              details.style.display = 'none';
              icon.textContent = '+';
            }
        });

        //e) put the card on the page
        container.appendChild(cardElement);
    });
</script>

<footer>
    <p>&copy; 2026 My Website - Built with HTML,  CSS and JavaScript by Ellen Cain. All rights reserved.</p>
</footer>
</body>
</html>
