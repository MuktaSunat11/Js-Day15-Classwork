# Car Generator
This is a simple web app that allows users to generate images of cars. The app uses to fetch images of cars.

# Html File
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Generator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="main-container">
        <h3> Car Generator</h3>
        <button class="carBtn">Get Car</button>
         
        <div class="car-content">
            <img class="car-img" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQkg24wLDuUsSfL8d4M8lrkjyg0j_awRZTYeA&usqp=CAU" alt="">
            <h3 class="car-name">Car Name</h3>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

# Css File
```
body{
    margin: 0;
    background: linear-gradient(to right, rgb(109, 198, 228), rgb(249, 255, 85));
    display: flex;
    height: 100vh;
    justify-content: center;
    align-items: center;
    font-family: 'Courier New', Courier, monospace;
}

.main-container{
    background: aliceblue;
    border-radius: 10px;
    box-shadow: 0 10px 20px rgba(0,0,0,0.3);
    text-align: center;
    padding: 10px;
    width: 450px;
    margin: 5px;
}

.carBtn{
    background-color:rgb(119, 9, 44);
    color: aliceblue;
    padding: 10px 30px;
    font-size: 16px;
    margin-bottom: 30px;
    border-radius: 6px;
    cursor: pointer;

}

.carBtn:disabled{
    background-color: gray;
    cursor: not-allowed;
}

.car-img{
    height: 300px;
    width: 300px;
    border-radius: 50%;
    border: 3px solid rgb(5, 248, 114);
}

.car-name{
    margin: 20px;
    background-color: rgb(119, 9, 44);
    color: aliceblue;
    padding: 10px;
    border-radius: 6px;
    font-size: 17px;
    font-weight: 600;
}

.car-content{
    display: none;
}
```

# Javascript File
```
const carBtn=document.querySelector(".carBtn");
const Container=document.querySelector(".anime-car");
const img=document.querySelector(".animeImg");
const name=document.querySelector(".animeName");


carBtn.addEventListener("click",async function(){
    try{
        carBtn.disabled="true";
        carBtn.innerText="Loading...";
        img.src="generator.svg";
        const response=await fetch("https://api.unsplash.com/photos/random?client_id=gM-W5b6zHt-3-J9Ubxi9IvBJl_ksBWrwxK0y5G-KELM&query=car");
        const data=await response.json();
        carBtn.disabled="false";
        carBtn.innerText="Get Car";
        Container.style.display="block";
        img.src=data.links.download;
        name.innerText=data.alt_description;


    }
    catch (error){
        console.log(error);
        carBtn.disabled = false;
        carBtn.innerText = "Get car";
        name.innerText = "An error happened, please try again";
    }
});
```
