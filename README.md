<html lang="en">
<head>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"></link>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div class="container-1">
 <h1>Challenge 1:Your age in days</h1>
 <div class="flex-box-container-1">
     <div>
 <button class="btn btn-primary" onclick="ageindays()">Click Me!</button>  
</div><div> 
    <button class="btn btn-danger" onclick="reset()">Reset</button>
</div>
</div>
<div class="flex-box-container-1">
    <div class="flex-box-container-1" id="flex-box"></div>
</div>
</div>
<div class="container-1">
    <h1>Challenge 2:Aman Genrator</h1>
    <div class="flex-box-container-1">
        <div>
            <button class="btn btn-success" onclick="amangen()">
                Genrate Aman
            </button>
        </div>
    </div>
    <div class="flex-box-container-1" id="flex-aman">
        
    </div>
</div>
<div class="container-1">
    <h1>Challenge 3:Rock,Paper,Scissors</h1>
    <div class="flex-box-container-2" id="flex-box-rps">
        <img src="Capture.1PNG.png" alt="" height="150" width="150" id="rock" onclick="rpsgame(this)">
        <img src="Capture2.png" alt="" height="150" width="150" id="paper" onclick="rpsgame(this)">
        <img src="Capture3.png" alt="" height="150" width="150" id="scissors" onclick="rpsgame(this)">
    </div>
    <div class="flex-box-container-1" id="flex-box-rps">
        <button class="btn btn-info" onclick="rpsgamegenrate()">Play Again</button>
    </div>
</div>
<style>
  .container-1{
    border: 1px solid black;
    width: 55%;
    margin: 0 auto ;
    text-align: center;
}
.flex-box-container-1,.flex-box-container-2{
    display: flex;
    flex-wrap: wrap;
    border: 1px solid black;
    padding: 10px;
    justify-content: space-around;
}
.flex-box-container-1 div{
    padding: 10px;
    border: 1px solid black;
}
.flex-box-container-1 img{
    box-shadow: 0px 10px 50px rgba(0,0,0,0.7);
    margin:10px;
}
.flex-box-container-2 img:hover{
    box-shadow: 0px 10px 50px rgba(20,20,243,1);
}
</style>
<script>
function ageindays(){
    var birthyear=prompt("Which year were you born in?");
    var ageindayss=(new Date().getFullYear()-birthyear)*365;
    var h1=document.createElement("h1");
    h1.setAttribute("id","aman");
    text=document.createTextNode("You are "+ageindayss+" days old.");
    h1.appendChild(text);
    document.getElementById("flex-box").appendChild(h1);
}

function reset(){
    document.getElementById("aman").remove();
}
function amangen(){
    var img=document.createElement('img');
    img.src="aman1.png";
    document.getElementById("flex-aman").appendChild(img);
}
function rpsgamegenrate(){
    document.getElementById('aman').remove();
    document.getElementById('amanaman').remove();
    document.getElementById('amanamanaman').remove();
    var img=document.createElement('div');
    img.innerHTML="<img src='Capture.1PNG.png' id='rock' alt='' margin=10px height=150 width=150 onclick='rpsgame(this)'><img src='Capture2.png' margin=10px id='scissors' alt='' height=150 width=150 onclick='rpsgame(this)'><img src='Capture3.png' margin=10px id='paper' alt='' height=150 width=150 onclick='rpsgame(this)'>"
    document.getElementById('flex-box-rps').appendChild(img)
    
}
function rpsgame(YourChoice){
    var human,computer;
    human=YourChoice.id;
    computer=choose(randomator())
    console.log("Computer Choice:",computer);
    var result=checkWinner(human,computer);
    console.log(result)
    var message=finalmessage(result);
    console.log(message);
    rpsFrontEnd(human,computer,message);
   
     
}
function randomator(){
    return Math.floor(Math.random()*3);
    
}
function choose(number){
    return['rock','paper','scissors'][number]
}
function checkWinner(YourChoice,computer){
    var rpsdatabase={
        'rock':{'scissors':1,'rock':0.5,'paper':0},
        'scissors':{'scissors':0.5,'rock':0,'paper':1},
        'paper':{'scissors':0,'rock':1,'paper':0.5}
    }
    var yourscore=rpsdatabase[YourChoice][computer];
    var computerscore=rpsdatabase[computer][YourChoice]
    return([yourscore,computerscore])
}
function finalmessage([yourscore,computerscore]){
    if(yourscore===0){
        return{'message':'You Lost' ,'color':"red"}
    }
    else if(yourscore===1){
        return{'message':'You Won','color':"green"}
    }
    else{
        return{'message':'You Tied','color':"blue"}
    }
}
function rpsFrontEnd(humanchoice,botchoice,finalmessage){
    var imagedatabase={
        'rock':document.getElementById('rock').src,
        'paper':document.getElementById('paper').src,
        'scissors':document.getElementById('scissors').src,
    }
    document.getElementById('rock').remove();
    document.getElementById('paper').remove();
    document.getElementById('scissors').remove();
    var humandiv=document.createElement('div');
    var computerdiv=document.createElement('div');
    var messagediv=document.createElement('div');
    humandiv.innerHTML="<img src='"+imagedatabase[humanchoice]+"' id='aman'height=150 width=150 style='box-shadow: 0px 10px 50px rgba(20,20,243,1);'>"
    computerdiv.innerHTML="<img src='"+imagedatabase[botchoice]+"' id='amanaman' height=150 width=150 style='box-shadow:0px 10px 50px rgba(243,20,20,1);'>"
    messagediv.innerHTML="<h1 style='color:"+finalmessage['color']+"' id='amanamanaman'font-size:60px padding:60px>"+finalmessage['message']+"</h1>"
    document.getElementById("flex-box-rps").appendChild(humandiv);
    document.getElementById("flex-box-rps").append(messagediv);
    document.getElementById("flex-box-rps").appendChild(computerdiv);
}</script>
</body>
</html>

