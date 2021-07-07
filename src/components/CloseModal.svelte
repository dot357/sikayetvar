<script>
  import { createEventDispatcher } from 'svelte';
  export let isOpen;
  const dispatch = createEventDispatcher();
  function closeModal() {
    isOpen = false;

   
  }

  
</script>


<span on:click={closeModal} class="close">x</span>


<style>
    span {
    cursor: pointer;
    float: right;
    font-size:1.6em;
    font-weight: 400;
    color: rgb(27, 27, 27);

    /* for disabling sellection on page indicators*/
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    transition: all 0.15s ease;
  }


  span:hover, span:focus{
    opacity: 0.6;
  }
</style>