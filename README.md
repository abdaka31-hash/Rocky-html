# Rocky-html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rocky Site - ❤️</title>
    <link rel="stylesheet" href="style.css"> 
</head>
<body>

    <div id="heart-container" onclick="toggleIcon()">
        <span id="icon" class="heart-icon">❤️</span> 
        <span id="middle-finger-icon" class="middle-finger-icon">🖕🏻</span> 
    </div>

    <script src="script.js"></script> 

</body>
</html>
body {
    background-color: white; 
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; 
    margin: 0;
    overflow: hidden; 
}

#heart-container {
    position: relative;
    cursor: pointer; 
    transition: transform 0.3s ease; 
}

#icon, #middle-finger-icon {
    font-size: 150px; 
    line-height: 1;
    transition: transform 0.3s ease, font-size 0.3s ease;
}

.heart-icon {
    color: red; 
}

.middle-finger-icon {
    color: black; 
    display: none; 
}

.transformed {
    transform: rotate(5deg) scale(1.5);
    font-size: 200px !important; 
}

.small {
    transform: rotate(-5deg) scale(0.8);
    font-size: 100px !important;
}
const heartContainer = document.getElementById('heart-container');
const heartIcon = document.getElementById('icon');
const middleFingerIcon = document.getElementById('middle-finger-icon');
let isHeart = true;
let timeoutId;

function toggleIcon() {
    clearTimeout(timeoutId);

    if (isHeart) {
        heartIcon.style.display = 'none';
        middleFingerIcon.style.display = 'block';
        isHeart = false;
        
        middleFingerIcon.classList.add('transformed');

        timeoutId = setTimeout(() => {
            middleFingerIcon.classList.remove('transformed');
            middleFingerIcon.classList.add('small');

            setTimeout(() => {
                middleFingerIcon.classList.remove('small');
                middleFingerIcon.style.display = 'none';
                heartIcon.style.display = 'block';
                isHeart = true;
            }, 1000);

        }, 500);

    } else {
        middleFingerIcon.classList.remove('transformed');
        middleFingerIcon.classList.remove('small');
        middleFingerIcon.style.display = 'none';
        heartIcon.style.display = 'block';
        isHeart = true;
    }
}
