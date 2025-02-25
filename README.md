# Image-Slider

HTML

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Slider</title>
    <link rel="stylesheet" href="slide.css">
</head>
<body>
    <div class="slider">
        <div class="slides">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQcdZa0XcB6lvfV4VuEynpSBK4GIR2HFYavRg&s" class="slide" alt="Image 1">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSmIAXjK_PnYZ08axKUdOON3sUd3yg2qHzk4g&s" class="slide" alt="Image 2">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTukZ_mEx7gBu4iw0aDfq9JNk8M3Y6NmFLR0Q&s" class="slide" alt="Image 3">
        </div>
        <button class="prev" onclick="prevSlide()">&#10094;</button>
        <button class="next" onclick="nextSlide()">&#10095;</button>
    </div>

    <script src="slide.js"></script>
</body>
</html>


CSS


body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f4f4f4;
    background-image: url("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS-PyDOUmVj2IjjPGrCy63l3f3e_-jMlaXuCQ&s");
    background-repeat: no-repeat;
    background-size: cover;
}

.slider {
    position: relative;
    width: 100%;
    max-width: 1000px;
    overflow: hidden;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.slides {
    display: flex;
    width: 300%;
    transition: transform 0.9s;
}

.slide {
    width: 100%;
    border-radius: 10px;
}

button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.5);
    color: white;
    border: none;
    padding: 10px;
    cursor: pointer;
    font-size: 18px;
    border-radius: 50%;
}

.prev {
    left: 10px;
}

.next {
    right: 10px;
}

button:hover {
    background: rgba(0, 0, 0, 0.8);
}




JAVASCRIPT


let currentIndex = 0;

function showSlide(index) {
    const slides = document.querySelector('.slides');
    const totalSlides = document.querySelectorAll('.slide').length;
    
    if (index >= totalSlides) {
        currentIndex = 0; // Loop back to first slide
    } else if (index < 0) {
        currentIndex = totalSlides - 1;
    } else {
        currentIndex = index;
    }

    slides.style.transform = `translateX(-${currentIndex * 100}%)`;
}

function nextSlide() {
    currentIndex++;
    showSlide(currentIndex);
}

function prevSlide() {
    currentIndex--;
    showSlide(currentIndex);
}

// Auto-slide every 3 seconds
setInterval(nextSlide, 3000);




CSSS
