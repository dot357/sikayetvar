<script>
    export let facebook;
    export let twitter;
    export let dribbble;
    export let github;

  
</script>

<footer>
<div class="footer">
    <div class="topLevel">
        <div class="leftSide">
            <h2>Thank you for supporting us!</h2>
            <h3>Let's get in touch on any of these platforms.</h3>
        </div>
        <div class="rightSide">
            <ul>
      
               <a class="tooltip" href="{twitter}" target="_blank"><li class="twitter "><i class="fab fa-twitter"></i> </li><span class="tooltiptext">Follow us</span></a>
               <a class="tooltip" href="{facebook}" target="_blank"><li class="facebook"><i class="fab fa-facebook-square"></i></li><span class="tooltiptext">Follow us</span></a>
               <a class="tooltip" href="{dribbble}" target="_blank"><li class="dribbble"><i class="fab fa-dribbble"></i></li><span class="tooltiptext">Follow us</span></a>
               <a class="tooltip" href="{github}" target="_blank"><li class="github"><i class="fab fa-github"></i></li><span class="tooltiptext">Follow us</span></a>
            </ul>
        </div>
    </div>
    <div class="bottomInfo">
        <p class="left"><span>© 2021</span>Şikayetvar</p>
        <p class="right"><a href="/">Posts</a></p>
    </div>
</div>

</footer>

<style>
    footer{
        box-shadow: 0px -6px 25px -13px rgba(0, 0, 0, 0.267);
        font-family: 'Open Sans', sans-serif;
        width:100%;
        background-color: white;
    }
 .footer{
        padding-top: 35px;
        margin: 0 auto;
        margin-top: 115px;
		width: min(77%, 90%);
		
		
 }

 .footer .topLevel{
    
     width: 100%;
     display: flex;
     flex-direction: row;
     justify-content: space-between;
     border-bottom: 1px solid rgba(0, 0, 0, 0.1);
     margin-bottom: 25px;
     padding-bottom: 81px;
 }
 .footer .topLevel .leftSide h2{
     color: #00CDAC;
     font-weight: 400;
     font-size: 24px;
 }

 .footer .topLevel .leftSide h3{
     color: #32325D;
     font-weight: 300;
     font-size: 22px;
 }

 .footer .topLevel .rightSide ul{
    list-style: none;
  
 }

 .footer .topLevel .rightSide ul li{
    display:inline;
    margin-left: 12px;
   
    color:white;
    box-shadow: 0px 7px 14px rgba(50, 50, 93, 0.1), 0px 3px 6px rgba(0, 0, 0, 0.08);
border-radius: 4px;
font-size: 14px;

transition: all 0.15s ease;
cursor:pointer;

 }

 .twitter{
    background-color: #1DA1F2;
    padding: 1em;
 }

 .facebook{
    background-color: #3B5999;
    padding: 1em 1.05em;
 }
 .dribbble{
    background-color: #EA4C89;
    padding: 1em;
 }

.github{
    background-color: #222222;
    padding: 1em;
}


 .footer .bottomInfo{
     width: 100%;
     display: flex;
     flex-direction: row;
     align-items: baseline;
    
 }


 .footer .bottomInfo .left {
  
    font-weight: 700;
    font-size:14px;
    color: #00CDAC;
    width:50%;
    
  

 }

 .footer .bottomInfo .left span{
     color:#525f7f;
     margin-right: 3px;
 }

 .footer .bottomInfo .right{
     text-align: right;
    color:#8898AA;
    text-decoration: none;
     width: 50%;
 }

 .footer .bottomInfo .right a{
   
    text-decoration: none;
   
 }


 @media screen and (max-width: 920px) {
    .footer .topLevel{
        flex-direction: column;
    }

    .footer .topLevel .rightSide ul{
        padding: 0;
       
    }
    .footer .topLevel .rightSide ul li{
        margin:0;
       
    }

    .footer .topLevel .leftSide h2{
        font-size:20px;
    }
    .footer .topLevel .leftSide h3{
        font-size: 18px;
    }

 }



 .tooltip {
  position: relative;
  display: inline-block;
  
}



.tooltip .tooltiptext {
  visibility: hidden;
  font-weight: 400;
  font-size: 14px;
  width: 120px;
  background-color: #212529;
  color: #fff;
  text-align: center;
  border-radius: 4px;
  padding: 5px 0;
  position: absolute;
  z-index: 1;
  bottom: 145%;
  left: 60%;
  margin-left: -60px;
  opacity: 0;
  transition: opacity 0.3s;
}

.tooltip .tooltiptext::after {
  content: "";
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #212529 transparent transparent transparent;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
  opacity: 1;
}
 
 
</style>