# test.03
a simple Website designed by Gavaine
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Be My Valentine 💕</title>

<style>
body{
    background: linear-gradient(135deg, #ffe6f0, #ffd1e8);
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
}

.container{
    background: white;
    border-radius: 22px;
    padding: 25px;
    max-width: 600px;
    width: 90%;
    text-align: center;
    box-shadow: 0 12px 30px rgba(0,0,0,0.12);
}

h1{ color:#ff5fa2; }

#question{
    font-size: 1.4rem;
    margin: 16px 0;
}

img{
    width: 170px;
    height: 170px;
    object-fit: cover;
    border-radius: 18px;
    margin: 12px 0;
    transition: 0.4s ease;
}

.buttons{
    margin-top: 18px;
    display:flex;
    justify-content:center;
    gap:15px;
    flex-wrap:wrap;
}

button{
    border:none;
    border-radius:12px;
    padding:14px 26px;
    font-size:1.1rem;
    cursor:pointer;
    transition:transform 0.5s ease;
}

#yesBtn{
    background:#ff69b4;
    color:white;
}

#noBtn{
    background:#ffc1dc;
    color:#7a2449;
}

.note{
    margin-top:15px;
    font-style:italic;
    color:#b23a6f;
}

.poem{
    margin-top:20px;
    padding:18px;
    background:#ffe6f2;
    border-radius:14px;
    color:#8a1f52;
    display:none;
    line-height:1.6;
}
</style>
</head>

<body>
<div class="container">
    <h1>💖 Will You Be My Valentine? 💖</h1>

    <img id="moodImage"
         src="https://media.istockphoto.com/id/513237708/photo/man-with-bouquet-of-red-roses-on-a-gray-background.jpg?s=612x612&w=0&k=20&c=x0Vn55sreqzSQekdCvw4kWseuyXL-zJkb_4ao98FdBY=">

    <div id="question">Please say yes 💕</div>

    <div class="buttons">
        <button id="yesBtn">Yes 💕</button>
        <button id="noBtn">No 😢</button>
    </div>

    <div id="note" class="note"></div>
    <div id="poem" class="poem"></div>
</div>

<script>
let yesCount = 0;
let noCount = 0;
let hasSaidNo = false;

const yesNotes = [
    "You have such a beatuful VOICE 💖",
    "You make things feel A little better 🌸",
    "There’s something really special about you 💕",
    "You’re genuinely wonderful 🥰",
    "You’re easy to appreciate 🌷",
    "This means a lot 💘"
];

const happyImages = [
    "https://images.pexels.com/photos/461198/pexels-photo-461198.jpeg",
    "https://images.pexels.com/photos/1028725/pexels-photo-1028725.jpeg",
    "https://images.pexels.com/photos/931177/pexels-photo-931177.jpeg",
    "https://images.pexels.com/photos/1382731/pexels-photo-1382731.jpeg",
    "https://images.pexels.com/photos/1468379/pexels-photo-1468379.jpeg",
   "https://pintsizedbaker.com/wp-content/uploads/2016/05/Strawberries-and-Chocolate-Jello-Mold.jpg",
];

const sadImages = [
    "https://images.pexels.com/photos/459225/pexels-photo-459225.jpeg",
    "https://images.pexels.com/photos/1557652/pexels-photo-1557652.jpeg",
    "https://images.pexels.com/photos/307008/pexels-photo-307008.jpeg",
];

const noQuestions = [
    "Why are you so mean 😭",
    "That hurt a little 💔",
    "Are you really sure? 😢",
    "I’m still hoping 🥺",
    "Okay… I hear you 😞"
];

document.getElementById("yesBtn").addEventListener("click", yesClick);
document.getElementById("noBtn").addEventListener("click", noClick);

function yesClick(){
    if(hasSaidNo){
        finalYes();
        return;
    }

    if(yesCount < 6){
        document.getElementById("question").innerText = "Are you sure? 💗";
        document.getElementById("note").innerText = yesNotes[yesCount];
        document.getElementById("moodImage").src = happyImages[yesCount];

        const scale = 1 + yesCount * 8;
        document.getElementById("yesBtn").style.transform = `scale(${scale})`;

        yesCount++;
    } else {
        finalYes();
    }
}

function finalYes(){
    document.getElementById("yesBtn").style.transform = "scale(1)";
    document.getElementById("yesBtn").disabled = true;
    document.getElementById("noBtn").disabled = true;
    document.getElementById("noBtn").style.display = "none";

    document.getElementById("question").innerText =
        "💖 THANK YOU FOR CHOOSEING ME KIMESHA💖";

    document.getElementById("moodImage").src = happyImages[5];
    document.getElementById("note").innerText = "";

    document.getElementById("poem").innerHTML = `
        I do not like you in a loud, careless way,
Nor chase your name through reckless praise;
I like you in the hush of night,
Where hearts speak truth beyond our sight.

In borrowed glances, calm and deep,
In promises the soul must keep,
KIM In every breath I do not say,
Yet hope you somehow feel each day.

If time should ask what love can be,
I’d point to you, then quietly
Confess my heart has learned your name
And nothing in this world’s the same.
    `;
    document.getElementById("poem").style.display = "block";

    localStorage.setItem("valentineAnswer", "YES 💖");
}

function noClick(){
    hasSaidNo = true;
    noCount++;

    document.getElementById("question").innerText =
        noQuestions[Math.min(noCount - 1, noQuestions.length - 1)];

    document.getElementById("note").innerText = "That’s okay 💔";

    document.getElementById("moodImage").src =
        sadImages[Math.min(noCount - 1, sadImages.length - 1)];

    document.getElementById("noBtn").style.transform =
        `scale(${Math.max(0.3, 1 - noCount * 0.2)})`;

    document.getElementById("yesBtn").style.transform =
        `scale(${1 + noCount * 2})`;
}
</script>
</body>
</html>
