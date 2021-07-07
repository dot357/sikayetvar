

<script context="module">
	import Writer from './../../components/Writer.svelte';
	import Footer from './../../components/Footer.svelte';
	import Head from './../../components/Head.svelte';
  


   export async function preload({params, query}) {
       //console.log(params);
       const res = await this.fetch(`http://jsonplaceholder.typicode.com/posts/${params.slug}`);
       const data = await res.json()
      
       return {postInfo : data};
   }


   
</script>



<script>
     export let postInfo;
   // console.log(userInfo);
</script>

<svelte:head>
	<title>{postInfo.title}</title>
</svelte:head>

<Head />

<article class="postStyle">

   <div class="title"><h1>{postInfo.title}</h1></div>
   <div class="body"><p>{postInfo.body}</p></div>
   <div class="writer">
      <a rel="prefetch" href='/profile/{postInfo.userId}'><Writer userId={postInfo.userId}/></a></div>

   



</article>

<Footer  facebook='https://www.facebook.com/sikayetvar/' github='https://github.com/dot357' dribbble='#' twitter='#'/>


<style>
   .postStyle{
      margin: 0 auto;
    margin-top: 5em;
    padding-left: 2em;
    padding-right: 2.1em;
    padding-top: 1em;
    padding-bottom: 1em;
    min-height: 500px;
    font-family: "Open Sans", sans-serif;
    list-style: none;
    background-color: white;
    width: min(75%, 90%);
    box-shadow: 0px 15px 35px rgba(50, 50, 93, 0.1),
      0px 5px 15px rgba(0, 0, 0, 0.07);
    border-radius: 4px;
   }

   .title{
      width: 100%;
      padding-top: 25px;
      padding-bottom: 15px;
      text-align: left;
   }
   .body{
      width: 100%;
      text-align: left;
   
   }

   .writer a {
      float: left;
      text-decoration: none;
    margin: 8px 8px;
    margin-left: 0px;
    padding: 0.3em;
    cursor: pointer;
    background: linear-gradient(to bottom, #8ddad5 0%, #00cdac 100%);
    background-position: 0 100%;
    background-repeat: repeat-x;
    background-size: 1px 1px;
    /* for disabling sellection on page indicators*/
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    transition: all 0.15s ease-in;
  }

  .writer a:hover,
  .writer a:focus {
    color: white;
    font-weight: bold;
    letter-spacing: 1px;
    text-decoration: none;
    position: relative;
    font-weight: 400;
    background: linear-gradient(to bottom, #8ddad5 0%, #00cdac 100%);
    background-position: 0 100%;
    background-repeat: repeat-x;
    background-size: 35px 35px;
    box-shadow: 0px 0px 13px -8px rgba(0, 0, 0, 0.288);
  }
</style>