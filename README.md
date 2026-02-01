<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine Surprise</title>
<style>
  body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    font-family: 'Comic Sans MS', cursive, sans-serif;
    background: linear-gradient(to bottom right, #ff9a9e, #fad0c4);
    text-align: center;
    color: #fff;
  }

  h1 {
    font-size: 3rem;
    margin-bottom: 2rem;
    text-shadow: 2px 2px 8px #ff69b4;
  }

  .buttons {
    display: flex;
    gap: 2rem;
    margin-top: 2rem;
    position: relative;
  }

  button {
    font-size: 1.5rem;
    padding: 1rem 2rem;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    transition: all 0.3s;
  }

  .yes-btn {
    background-color: #ff69b4;
    color: #fff;
  }

  .no-btn {
    background-color: #fff;
    color: #ff69b4;
    position: absolute;
  }

  img {
    margin-top: 2rem;
    max-width: 80%;
    border-radius: 12px;
    box-shadow: 0 0 20px #ff69b4;
  }
</style>
</head>
<body>
  <h1>Leonie, will you be my Valentine? 💖</h1>
  <div class="buttons">
    <button class="yes-btn">Yes</button>
    <button class="no-btn">No</button>
  </div>
  <img id="surprise" src="" style="display:none;" alt="Surprise Picture">
<script>
  const yesBtn = document.querySelector('.yes-btn');
  const noBtn = document.querySelector('.no-btn');
  const surpriseImg = document.getElementById('surprise');

  // When Yes is clicked, show your picture
  yesBtn.addEventListener('click', () => {
    surpriseImg.src = 'https://your-image-url-here.com/picture.jpg'; // <-- replace with your picture URL
    surpriseImg.style.display = 'block';
  });

  // Make No button run away
  noBtn.addEventListener('mouseover', () => {
    const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
    const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
    noBtn.style.left = `${x}px`;
    noBtn.style.top = `${y}px`;
  });
</script>
</body>
</html>
