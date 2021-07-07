<script>
    //animation of bubbles
    import { onMount } from 'svelte';

  onMount(() => {
      //create
     document.querySelector('.bubble1').animate([
                // keyframes
                { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/50)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
              
                 },
                 { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/50)}px`,
                   transform: `scale(0.${100 - Math.floor(Math.random() * 100)})`
                   
                 },
                 { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/50)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
                 },
                { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/50)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
              
                 },
               
            ], {
                // timing options
                duration: 30000,
                iterations: Infinity
            });

            document.querySelector('.bubble2').animate([
                // keyframes
                { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/55)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
              
                 },
                 { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/55)}px`,
                   transform: `scale(0.${100 - Math.floor(Math.random() * 100)})`
                   
                 },
                 { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/55)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
                 },
                { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/55)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
              
                 },
               
            ], {
                // timing options
                duration: 25000,
                iterations: Infinity
            });

            document.querySelector('.bubble3').animate([
                // keyframes
                { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/60)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
              
                 },
                 { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/60)}px`,
                   transform: `scale(0.${100 - Math.floor(Math.random() * 100)})`
                   
                 },
                 { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/60)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
                 },
                { left: `${Math.floor(Math.random() * window.innerWidth)}px`,
                   top: `${Math.floor(Math.random() * window.innerHeight/60)}px`,
                   transform: `scale(1.${Math.floor(Math.random() * 100)})`
              
                 },
               
            ], {
                // timing options
                duration: 35000,
                iterations: Infinity
            });
            

        
  });



</script>

<div class="mainBg">
  <div class="bubble1" ></div>
  <div class="bubble2" ></div>
  <div class="bubble3" ></div>
  
</div>

<style>
  .mainBg {
    position: fixed;
    height: 70%;
    width: 100%;
    background: linear-gradient(340.03deg, #8ddad5 8.42%, #00cdac 91.45%);
    clip-path: polygon(0 0, 100% 0, 100% 90%, 0% 100%);
    top: 0;
    left: 0;
    z-index: -9;
  }

  .bubble1 {
    width: 250px;
    height: 250px;
    border-radius: 9999px;
    background: #ffffff;
    mix-blend-mode: normal;
    opacity: 0.15;
    position: relative;
  }
  .bubble2 {
    width: 150px;
    height: 150px;
    border-radius: 9999px;
    background: #ffffff;
    mix-blend-mode: normal;
    opacity: 0.15;
    position: relative;
  }
  .bubble3 {
    width: 350px;
    height: 350px;
    border-radius: 9999px;
    background: #ffffff;
    mix-blend-mode: normal;
    opacity: 0.15;
    position: relative;
  }
</style>
