---
layout: page
title: About
permalink: /about/
---


<style>
    img {
        display: block;
        margin: 20px auto; /* Centers the image and adds space around it */
        max-width: 300px; /* Adjust this size as needed */
        height: auto; /* Keeps the image's aspect ratio */
        border: 7px solid #00f5ff; /* Adds a solid border with a specified color */
        border-radius: 10px; /* Optional: Adds rounded corners to the border */
    }

    .photo-container {
        position: relative;
        width: 300px; /* Adjust width as needed */
        height: 200px; /* Adjust height as needed */
        overflow: hidden; /* Hide overflowing content */
        margin: 20px auto;
    }

    .photo-box {
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        overflow: hidden;
    }

    .photo-box img {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover; /* Cover the box without distortion */
        transition: opacity 1s ease-in-out; /* Smooth transition for fading */
    }

    .photo-box img.hidden {
        opacity: 0;
    }

    .thin-box {
        position: absolute;
        width: 30px; /* Width of the thin box */
        height: 200px; /* Height of the thin box */
        background: rgba(0, 245, 255, 0.5); /* Semi-transparent color */
        border: 1px solid #00f5ff; /* Border color to match the image border */
        z-index: 1; /* Ensure boxes are above images */
    }

    .thin-box.left {
        left: -30px; /* Position the left boxes outside the container */
    }

    .thin-box.right {
        right: -30px; /* Position the right boxes outside the container */
    }

    /* Animation for thin boxes */
    @keyframes moveLeft {
        from { left: -30px; }
        to { left: 100%; }
    }

    @keyframes moveRight {
        from { right: -30px; }
        to { right: 100%; }
    }

    .move-left {
        animation: moveLeft 6s linear infinite;
    }

    .move-right {
        animation: moveRight 6s linear infinite;
    }

    /* Optional: Add some spacing to each section */
    section {
        margin-bottom: 40px;
    }

    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }

    .grid-item {
        text-align: center;
    }

    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }

    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }
</style>

# Joshua Thinh
I am very excited to take this class and delve deeper into computer science.

## Important things within my life: 
### Family, School, Video Games

### Family
- Family members:
    - Mother
    - Father
    - Brother
    - Little sister
    
<!-- This is where the cycling photo box will be displayed -->
<div class="photo-container">
    <div class="photo-box" id="photo_box">
        <!-- Images will be dynamically added here -->
    </div>
    <!-- Thin boxes on the left and right -->
    <div class="thin-box left move-left"></div>
    <div class="thin-box right move-right"></div>
</div>

### School
- Classes taking:
    - Stats
    - Photography
    - CSA
    - Civics
![Friends image]({{site.baseurl}}/images/friendphoto.png)

### Flags
<!-- This grid_container class is for the CSS styling, the id is for JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- Content will be added here by JavaScript -->
</div>

<script>
    // 1. Define the images to cycle through for the photo box
    var photoImages = [
        "{{site.baseurl}}/images/familyphoto.png",
        "{{site.baseurl}}/images/friendphoto.png"
    ];

    var photoBox = document.getElementById("photo_box");

    // 2. Create img elements for each photo and add to the photo box
    photoImages.forEach((src, index) => {
        var img = document.createElement("img");
        img.src = src;
        img.className = index === 0 ? "" : "hidden"; // Show the first image initially
        photoBox.appendChild(img);
    });

    // 3. Function to cycle through images in the photo box
    function cyclePhotos() {
        var current = 0;
        var images = photoBox.querySelectorAll("img");
        
        setInterval(() => {
            images[current].classList.add("hidden");
            current = (current + 1) % images.length;
            images[current].classList.remove("hidden");
        }, 3000); // Change image every 3 seconds
    }

    // Start cycling photos
    cyclePhotos();

    // 4. Define the flags data for the grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/01/Flag_of_California.svg", "description": "California - lived here forever", "greeting": "Love the food"},
        {"flag": "c/cf/Flag_of_Canada.svg", "description": "Canada - have a citizenship", "greeting": "Nicest people"}
    ]; 
    
    // 5. Grid dynamic generation for each data row
    var container = document.getElementById("grid_container");
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements

        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // Concatenate the source and flag
        img.alt = location.description + " Flag"; // Add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // Extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // Extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>

I enjoy playing sports and video games in my free time. I used to play basketball but now play volleyball on our school varsity team. The switch in sports was mainly due to the coaching and community differences. Volleyball is more laid-back and fits my vibe. My favorite subjects in school are math and technology because they just click in my brain. Other subjects like science and history aren’t my strongest, but I’ve had fun learning in them. However, English is my least favorite subject because it feels dull to me. My favorite food is ramen, which I first tried during my father's birthday celebration in elementary school. Coincidentally, the next day I was introduced to my least favorite food: sour cream, which I disliked because of its texture and taste.

I am good at working within a team and leading it to success. I am also very hard-working and determined, allowing me to complete any assignment given to me. However, I do struggle with decision-making because I tend to overthink, considering various outcomes before making a choice.

In the future, I hope to make my parents proud by becoming successful in the field of computer science. I plan to attend SDSU, following in my parents' footsteps. Computer science appeals to me not just because of its high earning potential but also because it is intellectually stimulating, especially with the variety of programming languages. Another goal is to maintain a healthy body and get stronger so I can continue to excel in volleyball.

Making my parents proud is a key motivator for me, highlighting how much my family means to me. I love my parents and siblings deeply, and they play a significant role in pushing me toward my goals. My faith is also important to me. Although I was introduced to Christianity by my parents, it wasn’t until a Christian retreat during my sophomore year that I started to take it more seriously.

I am looking forward to this computer science class to better understand the field's theoretical, practical, and innovative aspects.
